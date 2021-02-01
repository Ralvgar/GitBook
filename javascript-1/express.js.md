# Express.js

 Express.js is a web application framework that is built on top of [Node.js](https://www.edureka.co/blog/nodejs-tutorial/). It provides a minimal interface with all the tools required to build a web application. Express.js adds flexibility to an application with a huge range of modules available on npm that you can directly plug into Express as per requirement. It helps in easy management of the flow of data between server and routes in the server-side applications.

Example from my project [codos-app-backend](https://github.com/mallorcabootcamp/codos-app-backend):

```javascript
// index.ts

import express from 'express';

const app = express();

app.use(cors());
app.use(express.json());
app.use(router);


app.listen(process.env.PORT, () => {
     mqttOnConnect();
     log('Conectado al puerto ' + process.env.PORT);
});

// middelware

import { Request, Response, NextFunction } from 'express';


export const validationParamsData = (req: Request, res: Response, next: NextFunction) => {

     if(!req.query.fromDate || !req.query.toDate || !req.query.user || !req.query.aggregateTimeScale || !req.query.dataToGet) {
          return res.status(403).json({
               msg: "Los parámetros 'fromDate', 'toDate', 'user', 'aggregateTimeScale' y 'dataToGet' son requeridos"
          });
     }
     next();

}

// Responses

import { InfluxDBService } from '../influxDBService/influxDBService';
import { NextFunction, Request, Response } from 'express';
import debug from 'debug';


const log = debug("app:controller:users");
const mockData = process.env['MOCK_DATA'];

export const users = (req: Request, res: Response, next: NextFunction) => {

     log("getting users data");

     if (mockData === 'true') {
          const mockUser = require('../mockData/mockUser.json')
          res.json(mockUser);
     } else {

          const instance = new InfluxDBService();

          instance.getUsers().then(((data): void => {
               try {
                    log(`receiving users data`);

                    res.json(new Array().concat(...data))

                    log("exit controller");
               } catch (error) {
                    log('ERROR: ', error);
                    res.status(500).json({
                         ok: false,
                         msg: 'Error de servidor'
                    });
               }
               next();
          }))
     }
}




```

{% embed url="https://expressjs.com/" %}



