---
description: NodeJS app deployment
---

# NodeJS app deployment

You can use a Linux/Ubuntu [server ](https://www.digitalocean.com/)to deploy your app, if you're using typescript or something that a browser can't understand you should use `npm run build` it  creates a `build` directory with a production build of your app.

You can clone a copy of your build into your server and keep it working with [PM2](https://pm2.keymetrics.io/), [forever ](https://www.npmjs.com/package/forever)or some other process manager, they will help you manage and keep your application online 24/7.

Should add ssh keys, [install Node](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04).js on your server, `npm i` for install your package.json.

