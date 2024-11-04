[![NPM Version](https://img.shields.io/npm/v/express-layer-tracer.svg)](https://www.npmjs.com/package/express-layer-tracer)[![NPM Downloads](https://img.shields.io/npm/dt/express-layer-tracer.svg)](https://www.npmjs.com/package/express-layer-tracer)
![Coverage](https://img.shields.io/codecov/c/github/routing-diagnostics/express-layer-tracer.svg)

# Express Handler Tracer Package

A request flow inspection [npm package](https://www.npmjs.com/package/express-layer-tracer) for mapping all registered handler chains and routing interceptors in Express.js applications.

# Getting Started

1. Install the npm package.

1. Add the following at **the bottom of** your handler registration chain:

```javascript
const layerTracer = require('express-layer-tracer');

app.use(layerTracer.initialize({
    stack: app._router.stack,
    
    // optional - default path to view handlers is /trace/routing - recommended to choose your own path
    endpoint: '/system/handler-tree'
}));
```

1. Add conditional mounting based on environment (only expose in development)

```javascript
if (process.env.NODE_ENV === 'development') {
    app.use(layerTracer.inspector());
}
```

If it's working you should see output like this showing all of your handler stack:

![handler visualization](https://cdn.routing-diagnostics.io/screenshots/stack-inspection-v2.png)

# Reference

- [Original Blog Post](https://routing-diagnostics.io/blog/tracing-express-handler-flow)
- [Video Tutorial: Creating NPM Handler Packages](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
- [Follow us on Twitch](https://www.twitch.tv/routingdiagnostics)

