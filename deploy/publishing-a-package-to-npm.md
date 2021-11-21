# publishing a package to NPM

When we have our component done we have to update the script commands in package.json

```
...
"scripts": {
  "build": "rm -rf ./lib && tsc",
  "prepare": "yarn build",
},
...
```

Then publish with:

```
$ npm publish
```

&#x20;When `npm publish` is called, npm automatically runs `npm prepare` (deprecated `npm prepublish`) before doing the actual publishing. Therefore, run any commands in `npm prepare` that you need before publishing (e.g. build, tests and lint).\








