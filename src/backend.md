# Backend

## BACKLOG

- blockchain
- openai
- aws:
  - Cognito, IAM, Lambda, API Gateway, CodePipeline, ELB, CloudWatch, XRay, SQS, SecretManager, configservice, Route 53, SNS, S3, realtime db?
  - EC2, SES, SQS, ELB primarily
  - aws DevOps
  - sam framework
  - aws: sdk framework
  - aws: serverless framework
  - aws: cerification
  - aws: direct s3 upload, upload to s3 using node streams implementation (TradeZing project)
  - aws: storage, auth, ci/cd
- firebase
- investigate TradeZing project (BE)
- CSV file export/import from TradeZing, CSV and Excel file export/import from Enovos
- eslint and format option for import order from TradeZing
- JSON Schema
- Closures / Curring / HOF
- Observables / RxJS
- Generators
- "For a web process, graceful shutdown is achieved by ceasing to listen on the service port (thereby refusing any new requests), allowing any current requests to finish, and then exiting. Implicit in this model is that HTTP requests are short (no more than a few seconds), or in the case of long polling, the client should seamlessly attempt to reconnect when the connection is lost."
- "or a worker process, graceful shutdown is achieved by returning the current job to the work queue. For example, on RabbitMQ the worker can send a NACK;"
- "Instead, each running process writes its event stream, unbuffered, to stdout.
  The event stream for an app can be routed to a file, or watched via realtime tail in a terminal."
- https://www.dotenv.org/security/
- https://dev.to/gregorygaines/stop-using-env-files-now-kp0
- https://www.npmjs.com/package/nodemon#Gracefully-reloading-down-your-script
- https://www.npmjs.com/package/nodemon#Pipe-output-to-somewhere-else
- https://github.com/remy/nodemon/blob/HEAD/doc/events.md#Using_nodemon_as_child_process
- https://learnnode.com/
- https://www.javatpoint.com/
- https://yeoman.io/generators/
- https://gulpjs.com/docs/en/getting-started/creating-tasks/
- https://www.electronjs.org/

queues:

- https://blog.logrocket.com/scale-node-js-app-using-distributed-queues/
- https://www.sitepoint.com/implement-task-queue-node-js/
- https://betterprogramming.pub/using-bull-to-manage-job-queues-in-a-node-js-micro-service-stack-7a6257e64509
- https://www.thisdot.co/blog/bullmq-with-expressjs/
- https://celery-node.js.org/#/
  https://techsparx.com/nodejs/async/queue-processing.html
- https://devcenter.heroku.com/articles/node-redis-workers
- https://www.digitalocean.com/community/tutorials/how-to-handle-asynchronous-tasks-with-node-js-and-bullmq
- https://www.linkedin.com/pulse/introduction-nodejs-queues-jobs-practical-guide-examples-iqbal/
- https://byby.dev/node-job-queue-libraries
- https://levelup.gitconnected.com/how-to-implement-queues-in-node-js-8b3a06ce0dd0
- https://www.freecodecamp.org/news/how-to-use-queues-in-web-applications/
- https://www.makeuseof.com/task-queuing-nodejs-bullmq/#:~:text=BullMQ%20(Bull.,for%20task%20queuing%20in%20Node.
- https://adevait.com/nodejs/introduction-to-queues-nodejs#
- https://www.youtube.com/watch?app=desktop&v=-RnGbbIwTa8
- https://www.youtube.com/watch?app=desktop&v=E-01bE2LjxM
- https://www.youtube.com/watch?app=desktop&v=wAEMXVcRbgU
- https://blog.devgenius.io/boosting-server-performance-with-job-queue-in-node-js-3d480079cf31
- https://sliceofdev.com/posts/implementing-a-job-queue-in-nodejs
- https://stackoverflow.com/questions/16904093/worker-queue-for-nodejs
- https://github.com/bee-queue/bee-queue
- https://www.npmjs.com/search?q=job%20queue
- https://temporal.io/blog/using-temporal-as-a-node-task-queue
- https://www.yld.io/blog/a-distributed-work-queue/
- https://www.google.com/search?q=node+worker+queue&sca_esv=558660801&rlz=1CDGOYI_enDE753DE753&hl=en-US&sxsrf=AB5stBgOkiuR-yusfd2V4CHnQUeUBI60tA%3A1692593685096&ei=Fe7iZLG9BYCH9u8PrdCywAE&oq=node+worker&gs_lp=EhNtb2JpbGUtZ3dzLXdpei1zZXJwIgtub2RlIHdvcmtlcioCCAUyBxAjGIoFGCcyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESOdkUPoMWJEUcAF4AZABAJgBtgGgAdoIqgEDMC44uAEByAEA-AEBwgIKEAAYRxjWBBiwA8ICChAAGIoFGLADGEPiAwQYACBBiAYBkAYL&sclient=mobile-gws-wiz-serp#imgdii=CDAoh7wvZmz79M&imgrc=AIQ1850kdQvcWM
- https://www.youtube.com/watch?app=desktop&v=-RnGbbIwTa8
- https://www.google.com/search?q=node+worker+threads&rlz=1CDGOYI_enDE753DE753&oq=node+worker+task&gs_lcrp=EgZjaHJvbWUqBwgBEAAYogQyBggAEEUYOTIHCAEQABiiBDIHCAIQABiiBDIHCAMQABiiBNIBCjEzMDQyNGowajSoAgCwAgA&hl=en-US&sourceid=chrome-mobile&ie=UTF-8
- https://www.google.com/search?q=node+worker+queue&sca_esv=558660801&rlz=1CDGOYI_enDE753DE753&hl=en-US&sxsrf=AB5stBgOkiuR-yusfd2V4CHnQUeUBI60tA%3A1692593685096&ei=Fe7iZLG9BYCH9u8PrdCywAE&oq=node+worker&gs_lp=EhNtb2JpbGUtZ3dzLXdpei1zZXJwIgtub2RlIHdvcmtlcioCCAUyBxAjGIoFGCcyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESOdkUPoMWJEUcAF4AZABAJgBtgGgAdoIqgEDMC44uAEByAEA-AEBwgIKEAAYRxjWBBiwA8ICChAAGIoFGLADGEPiAwQYACBBiAYBkAYL&sclient=mobile-gws-wiz-serp

- plugin system
- gulp

js
ts
nodejs
git
vscode

## TODO

- debug
- mongodb, mongoose
- postgresql, sequelize
- db transactions
- cache, redis, memcached, node cache-manager, cache implementation (KandaSoft project)
- typeorm
- microservices, rabbitmq (cloudamqp), kafka, bullmq, event sourcing, event stores, CQRS
- DDD
- algorithms
- design patterns, solid, clean code / clean architecture,
  YAGNI (You aren't gonna need it), KISS (Keep it simple, stupid), DRY (Don't repeat yourself)
- aop
- data normalization, related tables normalization (1NF, 2NF, 3NF and BCNF)
- xstate
- node streams
- cron jobs
- auth
  - authorization / authentication
  - jwt, role based authorization, bearer token, refresh token, api token, 2fa, passportjs,
  - email / password auth, google auth, facebook auth, apple auth, microsoft auth
  - sign in, sign up, forgot / change password, block / unblock account, confirm email, confirm phone
- notifications, sendgrid, onesignal, twillo
- payments, paypal, stripe, google payment, apple payment
- ads, google ads, facebook ads
- booking, lightspeed
- video streaming, agora
- logging, winston, https://github.com/pimterry/loglevel
- web sockets, socket.io
- headless cms: https://strapi.io/
- webhooks

## IN PROGRESS

- nodejs
- expressjs
- nestjs

## DONE

- http response status codes
- nodemon
- openapi, swagger
- crud
- fast csv
- cookie parser
- rimraf
- yargs
- sharp
- multer
- nconf, env, dotenv, dotenv-expand, env-cmd, cross-env
- bcrypt
- ejs
- cors
- morgan
- chalk
- ora

## CLOSED

## LINKS

- https://www.rabbitmq.com/getstarted.html, https://customer.cloudamqp.com/login
- https://2021.stateofjs.com/
- https://stackshare.io/posts/top-developer-tools-2021
