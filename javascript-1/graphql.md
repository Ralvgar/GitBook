# GraphQL

GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

### **Data Fetching** <a href="e230" id="e230"></a>

Data fetching is certainly one of the most compelling advancements introduced by GraphQL. In a standard REST API to yield or recover data, we might require to make requests to numerous endpoints. The GraphQL in comparison offers single endpoint via which we access data available on the server.

```graphql
query {
  books {
    id
    title
    author
    isbn
    price
  } 
}
```

### Over or Under Data Fetching <a href="4e3e" id="4e3e"></a>

It is considerably much straightforward to fetch more data than you need in REST than in GraphQL as each endpoint in REST specification includes a settled data formation. Similarly, with REST it’s comparatively easier to under fetch the dataset, enabling clients to make additional requests to get relevant data.

The case is quite different when it comes to GraphQL. Since it’s a query language and supports declarative data fetching, the users can only get what they actually need from the server.

**Select only book title and price:**\


```graphql
query {
 books {
   title
   price
 } 
}
```

### Error Management <a href="0de6" id="0de6"></a>

Error management in REST specification is quite simple. All we need to do is to inspect the HTTP headers to know a position of a response. Contingent upon the status code, we can quickly state the error as well as the suitable way to resolve it. On the other hand, we always receive a 200 OK status in case of GraphQL.

```graphql
Request: query { books { error_field } }
Response:
Request Method:POST
Status Code: 200 OK
{“errors”:[{“message”:”Cannot query field \”error_field\” on type \”Book\”.”,”category”:”graphql”,”locations”:[{“line”:3,”column”:3}]}]}

```

### Caching <a href="9388" id="9388"></a>

Since REST is enforced employing HTTP which already put caching into effect, you can use it to avert getting resources. GraphQL, on the other hand, has no caching system, thus leaving the users with the burden of handling caching on their own.

There are some examples from our [beach sport rent](https://github.com/mallorcabootcamp/beach-sports-rent) project that also use [apollo](https://www.apollographql.com):

```javascript
// backend 
// typeDefs
 type KayakReservation {
    kayakType: String!
    duration: String!
  }

  type Reservation {
    _id: String!
    timestamp: String!
    userId: String!
    spotId: String!
    kayakReservations: [KayakReservation!]
    priceEur: Float!
  }
// resolvers
Query: {
    spots: async (
      parent: null | undefined,
      { query, limit }: { query: SpotsQuery; limit: number }
    ) => {
      return DbService.getSpots(query, limit);
    },
    reservations: () => {
      return DbService.getReservations();
    },
}
//

// frontend
// resolvers
export const GET_RESERVATIONS = gql`
  query getReservations {
    reservations {
        _id
        timestamp
        userId
        spotId
        kayakType
        duration
        priceEur
    }
  }
`;
// calls in code with apollo hooks
import { useQuery } from "@apollo/client";
import { GET_RESERVATIONS } from "../../gql/ReservationQueries";
const { loading, error, data } = useQuery(GET_RESERVATIONS);

const listData = data.reservations.filter(
        ({ timestamp }) => timestamp >= startOfDay && timestamp <= endOfDay
      );


```

