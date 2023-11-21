# Backend

## Log

- winston
- loglevel <https://github.com/pimterry/loglevel>
- sentry
- logrocket
- Grafana, Sentry, Instana
- morgan

## Security

- authorization (base)
- authentication (base)
- jwt
- role based authorization
- bearer token
- refresh token
- api token,
- 2fa
- passportjs
- email / password auth, google auth, facebook auth, apple auth, microsoft auth
- sign in, sign up, forgot / change password, block / unblock account, confirm email, confirm phone
- Cookie and Session (II): How session works in express-session <https://medium.com/@alysachan830/cookie-and-session-ii-how-session-works-in-express-session-7e08d102deb8>
- Best Practices for Secure Session Management in Node <https://jscrambler.com/blog/best-practices-for-secure-session-management-in-node>
- Why is it good practice to store session IDs in a database? <https://www.quora.com/Why-is-it-good-practice-to-store-session-IDs-in-a-database>
- JWT vs cookies for token-based authentication <https://stackoverflow.com/questions/37582444/jwt-vs-cookies-for-token-based-authentication>
- PassportJS, Sessions, API key, Auth0
- https://www.npmjs.com/package/jwks-rsa
- SSO
- Do I have to store tokens in cookies or localstorage or session? <https://stackoverflow.com/questions/54258233/do-i-have-to-store-tokens-in-cookies-or-localstorage-or-session>
- Keylock

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

## Udemy

Robert Bunch
Maximilian Schwarzmüller
Jonas Schmedtmann
Andrew Mead
Stephen Grider
Brad Traversy
Andrei Neagoie
Antonio Papa
Ryan Dhungel

## Resources

- Learn Node <https://learnnode.com/>
- Java Point <https://www.javatpoint.com/>
- Microsoft Learn <https://learn.microsoft.com/en-us/>
- Learn .NET <https://dotnet.microsoft.com/en-us/learn>
- AWS training and certification <https://www.aws.training/>
- AWS Hands-on Tutorials <https://aws.amazon.com/getting-started/hands-on/>
- StateOfJS2022 <https://2022.stateofjs.com/en-US/>
- Stackshare <https://stackshare.io/>
- Geeksforgeeks <https://www.geeksforgeeks.org/>
- freeCodeCamp <https://www.freecodecamp.org/>
- Khalilstemmler <https://khalilstemmler.com/>
- Fireship <https://fireship.io/>
- Refactoring <https://refactoring.guru/>
- Node.js Best Practices <https://github.com/goldbergyoni/nodebestpractices>
- JavaScriptInfo <https://javascript.info/>
- egghead <https://egghead.io/>
- wesbos <https://wesbos.com/>
- newline <https://www.newline.co/>
- codewithmosh <https://codewithmosh.com/>
- wanago <https://wanago.io/>
- rossbulat <https://rossbulat.medium.com/>
- webbyawards <https://www.webbyawards.com/>
- udemy labs <https://www.udemy.com/labs/listing/?vertical=all>
- hackerrank <https://www.hackerrank.com/>
- LogRocket blog <https://blog.logrocket.com/>
- Upwork blog <https://www.upwork.com/resources>
- IN learning <https://www.linkedin.com/learning/>
- in28minutes <https://www.in28minutes.com/>
- w3schools <https://www.w3schools.com/>
- zhenghao <https://www.zhenghao.io/>
- DEV <https://dev.to>
- DevIQ <https://deviq.com/>

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
- What the heck is the event loop anyway? <https://www.youtube.com/watch?v=8aGhZQkoFbQ>

```text
Db connection pool
https://stackoverflow.com/questions/8753442/thinking-behind-decision-of-database-connection-pool-size

If a typical request spends 50% of its time doing calculations and 50% on database connectivity you might only need 50 connections in your pool. Of course your application should release the db connection as early as possible.

In general holding a connection is not expensive for a database (while creating a new one is quite expensive). It should be no problem to keep the size high enough.

You can set

maximum pool size to 100
preferred pool size to 50
and the idle timeout to 5 minutes for pooled connections.
I am not familiar with microsoft sql server but I think its max pool limit is 100

Tomcat will be fine with this number of pool size.
```

```text
Db connection pool
https://stackoverflow.com/questions/19321157/determining-what-to-raising-max-pool-size-to-for-my-connection-pool

Why is this number defaulted at 100, seems low?
100 connections roughly means that you can handle two hundred 500ms database processings per second on every second without running low on connections. That's quite high. If you hit this limit, it's time to have a look at optimization.

Is there a good way to determine what this Max Should be raised to?
On a rough basis, it should be the number of connections you will need per second times the average execution time necessary before releasing each connection. For example, if you need to open one hundred new connections per second, each of them requiring 10 seconds before release (which would be really huge), you would need something like 1000 connections in your pool to handle it on the long run.
```

```text
Optimal number of connections in connection pool?
https://stackoverflow.com/questions/1208077/optimal-number-of-connections-in-connection-pool

Did you really mean 200 concurrent users or just 200 logged in users? In most cases, a browser user is not going to be able to do more than 1 page request per second. So, 200 users translates into 200 transactions per second. That is a pretty high number for most applications.

Regardless, as an example, let's go with 200 transactions per second. Say each front end (browser) tx takes 0.5 seconds to complete and of the 0.5 seconds, 0.25 are spent in the database. So, you would need 0.5 * 200, or 100 connections in the WebLogic thead pool and 0.25 * 200 = 50 connections in the DB connection pool.

To be safe, I would set the max thread pool sizes to at least 25% larger than you expect to allow for spikes in load. The minimums can be a small fraction of the max, but the tradeoff is that it could take longer for some users because a new connection would have to be created. In this case, 50 - 100 connections is not that many for a DB so that's probably a good starting number.
```

```text
worker threads or child processes in nodejs

While Node.js is primarily single-threaded, it can still leverage multiple threads through various mechanisms like child processes, worker threads, or external libraries. These mechanisms enable Node.js to offload heavy computations to separate threads or processes while the main event loop remains unblocked and responsive to handle I/O and other tasks.

To summarize, Node.js itself operates on a single thread for most of its tasks but uses an event-driven, non-blocking I/O model to efficiently manage concurrency. If you need to work with multiple threads explicitly, you can explore the use of worker threads or child processes to achieve parallelism in your Node.js applications.
```

- Database Connections: Less is More <https://kwahome.medium.com/database-connections-less-is-more-86c406b6fad>

- What is connection pooling, and why should you care <https://www.cockroachlabs.com/blog/what-is-connection-pooling/>

- About Pool Sizing <https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing>

- Determining database connection pool sizes <https://www.ibm.com/support/pages/determining-database-connection-pool-sizes-openpages-deployments-using-websphere-liberty-profile>

- Improve database performance with connection pooling <https://stackoverflow.blog/2020/10/14/improve-database-performance-with-connection-pooling/>

- realtime api, realtime db

- edge functions

- XState

- Node JS Cluster with PM2

- Lerna

- DDD, Inversion of Control / Dependencies Injection, Separation of Concerns, KISS, YAGNI, DRY, AOP

- related tables normalization (1NF, 2NF, 3NF and BCNF) <https://www.studytonight.com/dbms/database-normalization.php>

- data normalization
  <https://redux.js.org/tutorials/essentials/part-6-performance-normalization#normalizing-data>
  <https://redux.js.org/usage/structuring-reducers/normalizing-state-shape>
  <https://redux.js.org/usage/structuring-reducers/updating-normalized-data>

- https://www.npmjs.com/package/nodemailer

- SendGrid, OneSignal

- PayPal, Stripe

- Reverse Proxy, Load Balancer

- Custom plugins: install / uninstall, enable / disable, list all, configure

- eslint: --report-unused-disable-directives

- An introduction to Aspect-Oriented Programming <https://medium.com/@blueish/an-introduction-to-aspect-oriented-programming-5a2988f51ee2>

- Sorting Algorithms (Selection Sort, Bubble Sort, Merge Sort, and Quicksort) <https://levelup.gitconnected.com/sorting-algorithms-selection-sort-bubble-sort-merge-sort-and-quicksort-75479f8f80b1>

- https://www.npmjs.com/package/cron
- https://www.npmjs.com/package/node-cron

- https://www.npmjs.com/package/express-rate-limit

- sonarcube

- https://www.npmjs.com/package/newrelic

- https://www.npmjs.com/package/passport
- https://www.npmjs.com/package/passport-jwt
- https://www.npmjs.com/package/openid-client

- https://www.npmjs.com/package/pdfkit
- https://www.npmjs.com/package/pdfkit-table

- https://www.npmjs.com/package/compression

- https://www.npmjs.com/package/image-to-base64

- https://www.npmjs.com/package/pino
- https://www.npmjs.com/package/pino-pretty

- Doing a cleanup action just before Node.js exits <https://stackoverflow.com/questions/14031763/doing-a-cleanup-action-just-before-node-js-exits>

- https://www.npmjs.com/package/debug

- https://www.npmjs.com/package/express-http-proxy

- How to create a realtime app using Socket.io, React, Node & MongoDB <https://www.freecodecamp.org/news/how-to-create-a-realtime-app-using-socket-io-react-node-mongodb-a10c4a1ab676/>

- Building an online store with React, AWS, and Stripe <https://blog.bitsrc.io/how-to-build-an-online-store-with-react-aws-and-stripe-95413e6ce727>

- Sharing Types Between Backend and Frontend with the BFF Pattern <https://blog.bitsrc.io/sharing-types-between-backend-and-frontend-with-the-bff-pattern-553872842463>

- Which HTTP Status Code to Use for Every CRUD App <https://www.moesif.com/blog/technical/api-design/Which-HTTP-Status-Code-To-Use-For-Every-CRUD-App/>

- Cookies vs. Tokens: The Definitive Guide <https://dzone.com/articles/cookies-vs-tokens-the-definitive-guide>

- Agile Board usage – why tickets shouldn’t move left <https://agilefixer.com/2017/02/20/agile-board-usage-why-tickets-shouldnt-move-left/>

- How to apply SOLID principles with Typescript in an easy way <https://makinhs.medium.com/how-to-apply-solid-principles-with-typescript-in-an-easy-way-b91b53bc9853>

- 4 Simple and Effective Ways To Avoid Too Many Ifs With TypeScript <https://betterprogramming.pub/4-simple-and-effective-ways-to-avoid-too-many-ifs-with-typescript-89937c0f9a99>

- Automatic API Documentation in Node.js Using Swagger <https://medium.com/swlh/automatic-api-documentation-in-node-js-using-swagger-dd1ab3c78284>

- HOW TO SET UP A CRON JOB THAT RUNS A NODE.JS APP <https://flaviocopes.com/cron-job-nodejs-app/>

- How to create load balancing servers using Node.js ? <https://www.geeksforgeeks.org/how-to-create-load-balancing-servers-using-node-js/>

- A Complete Guide to Node.js Process Management with PM2 <https://blog.appsignal.com/2022/03/09/a-complete-guide-to-nodejs-process-management-with-pm2.html>

- https://www.npmjs.com/package/promisify

- stream-file-uploads-to-storage-server-in-node-js

- https://gist.github.com/ankitaabad/3872ba18a6048478267d620f67cfe9f1#file-fake_data-js

- How to OVER Engineer a Website <https://www.youtube.com/watch?v=Sxxw3qtb3_g>

- How to build real-time applications using WebSockets with AWS API Gateway and Lambda <https://www.freecodecamp.org/news/real-time-applications-using-websockets-with-aws-api-gateway-and-lambda-a5bb493e9452/>

- Module Pattern in JavaScript <https://javascript.plainenglish.io/data-hiding-with-javascript-module-pattern-62b71520bddd>

- <https://scaffoldhub.io/>

- Build a Doctor Appointment Bot With Azure Bot Service, Language Understanding, and Twilio SMS <https://betterprogramming.pub/build-a-doctor-appointment-bot-with-azure-bot-service-language-understanding-and-twilio-sms-5cc1311667bd>

- Cache implementation in Node.js <https://javaniceday.com/cache-implementation-in-node-js/>

- 5 NestJS Techniques to Build Efficient and Maintainable Apps <https://betterprogramming.pub/5-nestjs-techniques-to-build-efficient-and-maintainable-apps-be6bc77e789e>

- The Truth About Abs: How To Make $1,000,000 Per Month with Digital Products (Plus: Noah Kagan results) <https://tim.blog/2011/11/02/the-truth-about-abs-mike-geary/>

- Modernize how you build and manage applications <https://aws.amazon.com/partners/featured/modern-application-development/>

- terraform

- Swagger Codegen

- Agile/Scrum для начинающих. Что такое гибкая методология? <https://www.pmoffice.by/blog/agile/agile-approach.html>

- Dev Kanban Board: 1. Backlog, 2. To Do, 3. Development (Doing / Done), 4. Testing (Doing / Done), 5. Deployment, 6. Done.

```text
MongoDb ObjectId

1. import { Schema } from "mongoose"
const ObjectId = Schema.Types.ObjectId; // used in schemas

2. import { ObjectId } from "mongoose"
certificate._id as ObjectId // used for type casting

3. import { Types } from "mongoose"
const id = Types.ObjectId(certificate._id as string) // used to create a new ObjectId
```

```text
Error [ERR_MODULE_NOT_FOUND]: Cannot find module
Use --es-module-specifier-resolution=node flag, i.e.:
node --es-module-specifier-resolution=node src/app/api/file/test.js
```

- Documentation framework <https://docusaurus.io/>

- bots, trading bot <https://hummingbot.com/>

- <https://knexjs.org/>

- <https://github.com/anttiviljami/serverless-openapi-joi-boilerplate/blob/460ac2af3121172c0c803f74a2705183a5fb0439/scripts/build-swaggerui.js>

- <https://github.com/mesaugat/express-api-es6-starter/blob/b27510a960b7a4c1bb96974ea22ac62e9eb167ce/src/index.js>

- AWS Build a better business with data <https://pages.awscloud.com/global-ln-gc-600-dnb-10-data-stories-learn.html?gc-language=en-gb&trk=9100c9bb-5860-4e7f-be0c-255395525ebc&sc_channel=em>

- recursive functions

- blob, base64, checksum

- JSON is incredibly slow: Here’s What’s Faster! <https://medium.com/data-science-community-srm/json-is-incredibly-slow-heres-what-s-faster-ca35d5aaf9e8>

- CQRS - Command Query Responsibility Segregation <https://deviq.com/design-patterns/cqrs-pattern>

- Domain Events Pattern <https://deviq.com/design-patterns/domain-events-pattern>

- REPR <https://deviq.com/design-patterns/repr-design-pattern>
