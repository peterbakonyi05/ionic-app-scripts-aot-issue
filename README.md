# ionic-app-scripts Angular AOT issue

In case you create a subfolder in `app` and put the `main.ts` file there, AOT will fail. Normal build (without AOT) works fine.

See this [tiny commit](https://github.com/peterbakonyi05/ionic-app-scripts-aot-issue/commit/349d56c5f7a964144cd76c5ea428c3c2a9a14875) to understand how to replicate the issue.

This is a problem when you want to create a mobile web site and a native application from the same code base and have a separate entry file for the 2 platforms.

## Error

```
Uncaught TypeError: Cannot read property 'create' of undefined
    at main.js:8
    at t.invoke (polyfills.js:3)
    at Object.onInvoke (main.js:5)
    at t.invoke (polyfills.js:3)
    at e.run (polyfills.js:3)
    at t.run (main.js:5)
    at e._bootstrapModuleFactoryWithZone (main.js:8)
    at e.bootstrapModuleFactory (main.js:8)
    at Object.<anonymous> (main.js:25)
    at e (main.js:1)
    at main.js:1
    at main.js:1
```

## How to replicate the issue
```
npm run build --prod
```

Open `www/index.html`

## Notes
* `npm run build` without AOT works fine
* Tested with Angular 4 and the same issue happens
