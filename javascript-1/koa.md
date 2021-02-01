# Koa

Koa.js is a widely used Node.js web application framework. Koa.js is developed and maintained by the creators of another widely used Node.js framework — Express.js. As a lightweight Node.js framework, Koa.js provides a minimal interface for developing web applications and APIs. The features and tools provided by the framework further help programmers to accelerate development of web applications and APIs.

```text
const Koa = require('koa');
const app = new Koa();

// logger

app.use(async (ctx, next) => {
  await next();
  const rt = ctx.response.get('X-Response-Time');
  console.log(`${ctx.method} ${ctx.url} - ${rt}`);
});

// x-response-time

app.use(async (ctx, next) => {
  const start = Date.now();
  await next();
  const ms = Date.now() - start;
  ctx.set('X-Response-Time', `${ms}ms`);
});

// response

app.use(async ctx => {
  ctx.body = 'Hello World';
});

app.listen(3000);
```

{% embed url="https://koajs.com/\#" %}

