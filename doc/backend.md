# Backend

## Log

- winston
- loglevel: <https://github.com/pimterry/loglevel>
- sentry
- logrocket
- graphana
- morgan

## Security

- jwt
- role based authorization
- bearer token
- refresh token
- api token,
- 2fa
- passportjs
- email / password auth, google auth, facebook auth, apple auth, microsoft auth
- sign in, sign up, forgot / change password, block / unblock account, confirm email, confirm phone

## Plugin architecture

Creating a plugin architecture in Node.js involves designing a system that allows you to dynamically load and use external code modules or "plugins" in your application. This can make your application more extensible and flexible. Here are the general steps to create a plugin architecture in Node.js:

1. Define the Plugin Interface\
   Determine what functionality you want to make pluggable in your application.
   Define a clear interface or API that plugins must adhere to. This might include specifying functions, methods, or events that plugins should implement or interact with.

2. Plugin Discovery\
   Create a mechanism for discovering and loading plugins dynamically. Common approaches include using a directory where plugins can be placed or utilizing npm packages.

3. Plugin Loading\
   Use Node.js's require or import statements to load plugin modules dynamically at runtime. You can use tools like require.resolve to find the paths to plugin files.

4. Plugin Initialization\
   Initialize the loaded plugins by calling their initialization functions or constructors. This is where you can pass any configuration or dependencies that plugins may need.

5. Plugin Registration\
   Register the loaded plugins with your application. This may involve adding them to a registry or storing references to them in a data structure.

6. Plugin Usage\
   Integrate the loaded plugins into your application's logic. Call their methods, subscribe to their events, or utilize their functionality as needed.

7. Error Handling\
   Implement error handling to gracefully handle cases where plugins fail to load or behave unexpectedly.

8. Lifecycle Management\
   Define a plugin lifecycle, including initialization, configuration changes, updates, and disposal when the application exits or when a plugin is no longer needed.

9. Security Considerations\
   Be cautious when loading external code. Ensure that plugins are loaded from trusted sources and consider using security mechanisms like sandboxing or restricting plugin access to sensitive resources.

Here's a simplified example of a Node.js application with a plugin architecture:

```js
// main.js - Your application's entry point

const fs = require('fs');
const path = require('path');

// Define a directory where plugins can be placed
const pluginsDirectory = path.join(__dirname, 'plugins');

// Discover and load plugins
const plugins = fs.readdirSync(pluginsDirectory).map((pluginFileName) => {
  const pluginPath = path.join(pluginsDirectory, pluginFileName);
  return require(pluginPath);
});

// Initialize and register plugins
plugins.forEach((plugin) => {
  plugin.init();
  // Register the plugin with your application, e.g., by adding it to an array or map.
});

// Use the loaded plugins in your application
plugins.forEach((plugin) => {
  plugin.doSomething();
});
```

In this example, plugins are loaded dynamically from a `plugins` directory. Each plugin module exports an `init` method and provides functionality through other methods.

Keep in mind that building a robust plugin system can become more complex depending on your application's requirements and security considerations. Additionally, various libraries and frameworks can simplify the implementation of a plugin architecture in Node.js, so consider exploring existing solutions that match your needs.

## Resources

- Learn Node: <https://learnnode.com/>

- Java Point <https://www.javatpoint.com/>

- Microsoft Learn <https://learn.microsoft.com/en-us/>

- Learn .NET <https://dotnet.microsoft.com/en-us/learn>

- AWS training and certification <https://www.aws.training/>

- StateOfJS2022 <https://2022.stateofjs.com/en-US/>

- Stackshare <https://stackshare.io/>

- Geeksforgeeks <https://www.geeksforgeeks.org/>

## Inbox

- node cache-manager
- node streams
- cron jobs
- webhooks
- fast csv
- cookie parser
- sharp
- multer
- cross-env
- bcrypt
- cors
- NodeJS Shopping Cart - NodeJS, Express, Express-Session, Express handlebars (hbs) <https://github.com/gtsopour/nodejs-shopping-cart/tree/master>
- review all archived and active work projects
- CSV file export/import from TradeZing project, CSV and Excel file export/import from Enovos project
- upload a file using streams
- using a config server and "AWS Systems Manager Parameter Store" for env variables <https://dev.to/gregorygaines/stop-using-env-files-now-kp0>
- pipe output to a file <https://www.npmjs.com/package/nodemon#Pipe-output-to-somewhere-else>
- api throttling <https://www.tibco.com/reference-center/what-is-api-throttling>
- node threads <https://github.com/xk/node-threads-a-gogo#tagg-threads-%C3%A0-gogo-for-nodejs>
- Implement Redis with Node.js — Boosting Performance and Scalability of Application <https://rahulh123.medium.com/implement-redis-with-node-js-boosting-performance-and-scalability-of-application-8b0206579727>
- NodeJS TypeScript Docker Deployment Process With AWS EBS <https://codingwithmanny.medium.com/nodejs-typescript-docker-deployment-process-with-aws-ebs-14796cd78392>
