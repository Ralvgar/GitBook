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





