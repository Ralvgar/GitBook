# Authentication and Authorization

In our [Kayaks-for-rent](https://github.com/Ralvgar/kayaks-for-rent) project we saw about authentication and authorization for our login system we use the Abstract Protocol.

### Abstract Protocol Flow <a id="abstract-protocol-flow"></a>

![Abstract Protocol Flow](https://assets.digitalocean.com/articles/oauth/abstract_flow.png)

More detailed explanation of the steps in the diagram:

1. The _application_ requests authorization to access service resources from the _user_
2. If the _user_ authorized the request, the _application_ receives an authorization grant
3. The _application_ requests an access token from the _authorization server_ \(API\) by presenting authentication of its own identity, and the authorization grant
4. If the application identity is authenticated and the authorization grant is valid, the _authorization server_ \(API\) creates an access token to the application with a secret key to identificate the token. Authorization is complete.
5. The _application_ requests the resource from the _resource server_ \(API\) and presents the access token for authentication
6. If the access token is valid, the _resource server_ \(API\) serves the resource to the _application_

The actual flow of this process will differ depending on the authorization grant type in use, but this is the general idea.

some real examples from my code using Apollo, jwt and bcrypt:

```javascript
// Backend

//index.ts the context: We validate the token and grants access to the user

//...
await DbService.connect().then(
    () => {
      const server = new ApolloServer({
        typeDefs,
        resolvers,
        context: async ({ req }) => {
          const authHeader = req.headers.authorization || "";
          const token = authHeader.split(" ")[1];
          const validateToken = await tokenValidation(token);
          if (validateToken) {
            const user = await DbService.getUserFromToken(token);
            return { user };
          } else {
            return {};
          }
        },
      });
//...

//Login where ncrypt the password and create the token with the secret

// ...
export const loginMutation = async (
  parent: null | undefined,
  { email, password }: LoginParams
) => {
  const user = await DbService.getUser(email);

  if (!user) {
    return {
      ok: false,
      error: "El usuario no existe",
    };
  }
  const isEqual = await bcrypt.compareSync(password, user.password);
  if (!isEqual) {
    return {
      ok: false,
      error: "Contraseña incorrecta",
    };
  }
  const token = sign({ email: user.email }, process.env.SECRET as string, {
    expiresIn: "1h",
  });
  DbService.updateTokenOnUser(user.email, token);
  return { ok: true, email: user.email, token, tokenExpirationHours: 1 };
};
//...

// createReservation where we check if the user is logged in

//...
export const createReservationMutation = async (
  parent: null | undefined,
  { timestamp, spotId, kayakReservations, paymentId }: ReservationParams,
  context: UserContext
) => {
  if (!context.user) {
    return {
      error: "Es necesario estar identificado como usuario.",
    };
  }
//... 


```





