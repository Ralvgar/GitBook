---
description: 'https://www.mongodb.com/'
---

# MongoDB

```javascript
import { MongoClient, Db, ObjectId } from "mongodb";
import { User } from "@mallorcabootcamp/bsr-types";
import { SpotsQuery } from "../types/types";
import { PaymentService } from "./PaymentService";
import { getUniqueReservationId } from "../utils/getUniqueReservationId";

let db: Db | undefined;
const centsToEurosConversion = 100;

export class DbService {
  static connect() {
    const url = process.env.URL;
    const dbName = process.env.DB_NAME;
    return new Promise<void>((res, rej) => {
      const client = new MongoClient(url as string);
      client.connect((err) => {
        if (err) {
          rej(err);
        } else {
          db = client.db(dbName);
          res();
        }
      });
    });
  }

  static getSpots(query: SpotsQuery, limit?: number) {
    return DbService.getDb()
      .collection("spots")
      .find(query)
      .limit(!limit ? 0 : limit)
      .toArray();
  }

  static getSpotById(id: string) {
    return DbService.getDb()
      .collection("spots")
      .findOne({ _id: new ObjectId(id) });
  }

  static getReservations() {
    return DbService.getDb().collection("reservations").find().toArray();
  }

  static getUserFromToken(token: string) {
    return DbService.getDb().collection("users").findOne({ token });
  }

  static getUser(email: string): Promise<User | null> {
    return DbService.getDb().collection("users").findOne({ email });
  }
}
```

