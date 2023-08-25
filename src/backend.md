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

## TODO

- debug
- mongodb, mongoose
- postgresql, sequelize
- db transactions
- cache, redis, memcached, node cache-manager, cache implementation (KandaSoft project)
- typeorm
- microservices, rabbitmq (cloudamqp), kafka, event sourcing, event stores, CQRS
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
