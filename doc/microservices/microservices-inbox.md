# Microservices: Inbox

- Using nodemon as child process <https://github.com/remy/nodemon/blob/HEAD/doc/events.md#Using_nodemon_as_child_process>
- <https://www.rabbitmq.com/getstarted.html>, <https://customer.cloudamqp.com/login>
- <https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern>
- <https://aws.amazon.com/what-is/pub-sub-messaging/>
- <https://ably.com/blog/pub-sub-pattern-examples>
- <https://medium.com/geekculture/system-design-basics-pub-sub-messaging-88dfd98e67b7>
- <https://www.baeldung.com/cs/publisher-subscriber-model>

- Event-driven architecture: this is the use of events as a central object for services and applications to interact with each other. AsyncAPI is an open source community worth checking out here.

```text
API Gateway example

An API Gateway is a server that acts as an API front-end, receiving API requests, enforcing throttling and security policies, passing requests to the back-end service, and then passing the response back to the requester. It's often used to manage, secure, and optimize the communication between different microservices or between client applications and a collection of microservices.

Here's a simple example of how an API Gateway might work, using a hypothetical e-commerce application as an illustration:

Scenario: E-commerce API Gateway

Suppose you have an e-commerce application with various microservices, including:

1. Product Service: Provides information about products.
2. Cart Service: Manages the shopping cart.
3. Order Service: Handles order processing.

An API Gateway can sit in front of these services to provide a unified API for the client applications.

1. Request Routing: The API Gateway routes incoming requests based on the URL or request path to the appropriate microservice. For example:

    - GET /products is routed to the Product Service.
    - POST /cart/add is routed to the Cart Service.
    - POST /order/place is routed to the Order Service.

2. Authentication and Authorization: The API Gateway can handle authentication and authorization checks. It might require API keys, tokens, or session cookies to access certain endpoints. For example, a user must be authenticated to place an order.

3. Load Balancing: If you have multiple instances of a microservice running, the API Gateway can load balance requests across them to ensure even distribution of traffic.

4. Rate Limiting: To prevent abuse or overuse of your APIs, you can set rate limits. For example, a client might be limited to making 100 requests per minute.

5. Response Aggregation: Sometimes, a client request may require data from multiple microservices. The API Gateway can aggregate responses and send a single response back to the client. For example, when viewing a product page, the API Gateway can fetch product details from the Product Service and related product reviews from another service, and combine them into a single response.

6. Caching: The API Gateway can cache responses to reduce the load on microservices and improve response times for frequently requested data.

7. Logging and Analytics: It can log requests and responses for monitoring and analytics purposes. This can help you identify and troubleshoot issues and understand how your APIs are being used.

8. Error Handling: Handle errors and provide meaningful error messages to clients. If a microservice is down, the API Gateway can return a suitable error response.

9. Security: Implement security policies such as Cross-Origin Resource Sharing (CORS) to secure your APIs and protect against common web vulnerabilities.

10. SSL Termination: Handle SSL encryption and decryption so that the microservices behind the gateway don't need to worry about SSL/TLS.

Here's a simplified example in pseudocode to illustrate the concept:

# Pseudocode for an API Gateway
if request.path == "/products":
    if request.method == "GET":
        response = ProductService.fetch_products()
    else:
        response = "Method not allowed"
elif request.path == "/cart/add":
    if request.method == "POST":
        response = CartService.add_to_cart(request.body)
    else:
        response = "Method not allowed"
elif request.path == "/order/place":
    if request.method == "POST":
        response = OrderService.place_order(request.body)
    else:
        response = "Method not allowed"
else:
    response = "Not found"

# Apply security, logging, rate limiting, caching, etc. here

return response
```

- gRPC vs. WebSocket: Key differences and which to use <https://ably.com/topic/grpc-vs-websocket>

- HTTP/1.1 vs HTTP/2: What's the Difference? <https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference>

- Service Discovery in Microservices <https://www.baeldung.com/cs/service-discovery-microservices>

- try to implement "parallel streams of data"

- investigate "web workers"

- terminology: worker, job, task, process, root and parent and child processes (id and pid), depended task

- How do WebSockets work? <https://ably.com/topic/how-do-websockets-work>

- MQTT vs AMQP <https://www.cloudamqp.com/blog/amqp-vs-mqtt.html>

- Kafka vs RabbitMQ <https://aws.amazon.com/compare/the-difference-between-rabbitmq-and-kafka>

- Heres why you should use gRPC for everything <https://snede.net/heres-why-you-should-use-grpc-for-everything/>

- Теорема CAP <https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D0%BE%D1%80%D0%B5%D0%BC%D0%B0_CAP>

- gRPC vs. REST: Key Similarities and Differences <https://blog.dreamfactory.com/grpc-vs-rest-how-does-grpc-compare-with-traditional-rest-apis/>

- Open Telemetry (OTEL)?

- In a more decoupled environment, you can even split the request and the actual writing operation by subscribing the write operation to the input event, though that assumes the write operation will always be successful - but makes things faster overall.

- Typically, Kafka environments enforce that only those microservices who own the data (have write access, which per typical microservices architecture, only one single microservice should have on each piece of data)

- When do you prefer a message broker over an RPC framework for microservice? <https://www.quora.com/When-do-you-prefer-a-message-broker-over-an-RPC-framework-for-microservice>

- How should I choose between gRPC and Kafka when building microservices? <https://www.quora.com/How-should-I-choose-between-gRPC-and-Kafka-when-building-microservices>

```text
How should I choose between gRPC and Kafka when building microservices?

In Kafka you publish events, and listeners subscribed to those events react to them, so microservices become highly decoupled. A typical example is to perform a write operation to a microservice’s database, and all the same publish that information to some data lake as a log. In a more decoupled environment, you can even split the request and the actual writing operation by subscribing the write operation to the input event, though that assumes the write operation will always be successful - but makes things faster overall.

In gRPC you communicate directly microservices in a similar way you would do with REST or SOAP, just that the performance is a lot faster (I’ve seen benchmarks at 25x speed improvement). Generally this can be used for synchronizing data between different microservices. For example, microservice A may need an operation and information return from microservice B, so internally a call using gRPC can be generated between A and B.

If you tried to do the same in Kafka, you have to publish an event that has B as subscriber, and then B has to publish the answer with A as subscriber. The approach from gRPC is a lot more direct, as the queue may take a lot more time to reach from A to B, and back.

So if you just want to communicate microservices, it will largely depend on the synchronization requirements and who owns the data. Typically, Kafka environments enforce that only those microservices who own the data (have write access, which per typical microservices architecture, only one single microservice should have on each piece of data) can actually work with that data in write requests, while read-only requests may be synchronized lazily using the data pipeline and data shadowing - where other microservices subscribe to get read-only copies of the last up-to-date data.
```

```text
How should I choose between gRPC and Kafka when building microservices?


Right tool for the job. All depends on how you design your microservices.

I will use a very simple example of an order service which creates an invoice.

consumer (browser, etc) => order-write-v1
order-write-v1 => create-order topic
create-order-topic => order-manager (creates the order, business logic)
order-manager => order-created topic (who cares about this)
order-manager => (gRPC) create-invoice-write-v1
create-invoice-write-v1 => create-invoice topic
create-invoice topic => invoice-manager (creates the invoice, business logic)

Components:

- Create order Kafka topic (command)
- Order created Kafka topic (event)
- Create invoice Kafka topic (command)
- Invoice created Kafka topic (event)
- order-write-v1 (CQRS write side)
- invoice-write-v1 (CQRS write side)
- order-manager (async processing of messages)
- invoice-manager (async processing of messages)

So this design is saying that the order manager will asynchronously receive a command to create an order. When it finishes it will broadcast the event that the order was created. You may have other consumers (could even be invoice-manager) listening for that.

We are next saying that the order-manager (based on some requirement) needs to call the invoice-write-v1 microservice. Since we are talking internally, we use a gRPC service instead of REST for performance.

I guess my point is there is no A or B, but A *and* B.
```

- Examples of RPCs include: REST APIs, HTTP requests in general, SOAP APIs, websocket calls, database queries.

- Microservice architecture with RabbitMQ, why? <https://larionov.pro/en/articles/2019/msa-rabbitmq-why/>

- RPC vs. Messaging – which is faster? <https://particular.net/blog/rpc-vs-messaging-which-is-faster>

- Streaming APIs and Protocols: SSE, WebSocket, MQTT, AMQP, gRPC <https://www.aklivity.io/post/streaming-apis-and-protocols-sse-websocket-mqtt-amqp-grpc>

- A Comprehensive Guide to Long Polling in Node.js Framework <https://www.esparkinfo.com/blog/node-js-long-polling.html>

- Short Polling vs Long Polling vs Web Sockets <https://anuradha.hashnode.dev/short-polling-vs-long-polling-vs-web-sockets>

- What is streaming data? <https://aws.amazon.com/streaming-data/>

- What is a Message Queue? <https://aws.amazon.com/message-queue/>

- What is Pub/Sub? <https://cloud.google.com/pubsub/docs/overview>

- AMQP vs MQTT?

- resume example <https://lukasatkinson.de/2023/available-for-hire/>

```text
Microservice communication
https://softwareengineering.stackexchange.com/questions/373950/microservice-communication

There's no general answer for this. When you are using (micro-)services, you are building a distributed system. Distributed systems are massively more complex than a monolithic system exactly because we have to think about such things like partial failures and maintaining consistency – it's great that you immediately spotted these problems!

Therefore, microservices are not always a good choice, particularly not if you can easily solve your problems without them. They tend to become attractive when you are having other really big problems (like organizational requirements, or having to scale horizontally for performance), so that the potential drawbacks of microservices look acceptable in comparison.

There are a few general strategies and recommendations that can help, depending on your exact requirements:

Each instance of the service should be stateless. Any data must be stored externally of the service. This allows us to:

Run multiple instances of a service and load-balance between them. This allows us to perform horizontal scaling on a per-service granularity, and maintains availability if one instance fails.

Define clear transactions. A transactional operation has no effect until it is complete. This ensures that there are no partially-done operations. If a transaction is aborted, it can be retried. Because each service instance should be stateless this usually requires support of a DB, but please note that NoSQL DBs differ drastically in what kinds of transactions they support.

Not all processes can be modeled as a single transaction, especially when you have to interact with external services. Here, splitting the process into multiple transactional steps and keeping track of the state of the process may be a solution.

Consider whether processes have to be synchronous (every request gets a response) or can be asynchronous (events/jobs/messages are added to a queue and processed later). Asynchronous operations allow for much more flexibility. Then, adding the job to the queue is a transactional operation which promises that the job will be processed “soon”, at some point in the future. A job is removed from the queue after it was successfully processed. But the actual processing is not part of the transaction. This allows you to retry the job in the background, or hold it until another service is available again.

Make a distinctions between errors within the problem domain and failures of your system. System failures are likely temporary and can be solved by retrying the same request later. In HTTP, this is roughly the difference between 400 and 500 response codes. In single-page web applications, a common “failure” is that the client simply has no network connection. Consider whether updates can be queued for later. To check whether the service is available again, prefer a strategy like exponential backoff to avoid DDOSing yourself.

Consider various consistency strategies for concurrently updating data. One simple approach is last one wins. However, this might overwrite a change that has happened in the meantime.

A more sophisticated approach is test-and-set / optimistic locking: An update contains both the old data and the new data. The old data might simply be an ID or hash instead of the full data. Within the protection of a transaction, the new data is only written if the relevant old data is in the expected state, otherwise an error is returned. In SQL this is as simple as an UPDATE ... WHERE ... statement that verifies the old state. An error will usually require a (human) user to reconcile the new state with the intended change and resubmit the change.

The HTTP protocol has built-in support for optimistic locking via ETags + the If-Match header, and could respond with a 409 Conflict or 412 Precondition Failed status if a POST or PUT could not be applied.

Having a clear strategy to ensure consistency is important if a request is retried that was already handled. E.g. consider a service that has processed a transaction successfully but crashes before the success response can be sent.
```

```text
What if service B is not available? How should it reflect on the Front end?
https://softwareengineering.stackexchange.com/questions/373950/microservice-communication

I'm not sure what you mean by 'front end'? Is that service A? At any rate, if service A calls service B, and service B fails, there are two classes of cases. If the error was 4xx, then you should service A should fail the request (that triggered it calling service B) - probably with a 5xx error because there is likely a bug with service A.

If service B returned a 5xx error (indicating a possibly temporary) failure in its execution - you should generally have the call service A is handling (which triggers the call to service B) fail with a the same 500 error from upstream (indicating if the problem is temporary or more permanent to the caller).

If you meant for serviceA to be "the front end" - then the question is is answered. If you meant in general how to display on a ui that you are getting errors from backend services, this depends on the nature of the service requests (calls to service A from the frontend / gui) - but usually some sort of dialog box indicating failure is the least bad choice. This is really much more complicated, but as I'm not sure its really what you are asking, I'll skip detail there.

What about the data being passed on? should I assume the it is already lost?

If you call any service and get back a 4xx or 5xx error, you should assume your request has not been processed. So the short answer is - yes - your data is lost.

The slightly longer answer, is that its sometimes good architectural choice to have the first 'service' handling requests from the GUI - to be some sort message queuing service (e.g. Apache Kafka), which can handle retries with the upstream processing services fail.
```

- gRPC vs Message Broker <https://devpress.csdn.net/opensource/62f355067e668234661867af.html>

- Go, RabbitMQ and gRPC Clean Architecture microservice <https://dev.to/aleksk1ng/go-rabbitmq-and-grpc-clean-architecture-microservice-2kdn>

- gRPC vs Message Broker <https://memphis.dev/blog/grpc-vs-message-broker/>

- Performance comparison: REST vs gRPC vs asynchronous communication <https://medium.com/l3montree-techblog/performance-comparison-rest-vs-grpc-vs-asynchronous-communication-3ad27d144a13>

- When to NOT use a message broker such as RabbitMQ in a micro-services architecture?

- It's important to note that while Node.js excels at handling many concurrent I/O-bound requests, it may not be the best choice for CPU-bound tasks. For CPU-bound operations, consider offloading the work to worker threads or using other technologies better suited for parallel computation.

- Communication in a microservice architecture <https://learn.microsoft.com/en-us/dotnet/architecture/microservices/architect-microservice-container-applications/communication-in-microservice-architecture>

- Decoupling Microservices using Message-based RPC IPC, with Spring, RabbitMQ, and AMPQ <https://programmaticponderings.com/2017/05/08/decoupling-microservices-using-message-based-rpc-ipc-with-spring-rabbitmq-and-ampq/>

- What’s the Difference Between Kafka and RabbitMQ? <https://aws.amazon.com/compare/the-difference-between-rabbitmq-and-kafka/>

- API Showdown: REST vs. GraphQL vs. gRPC – Which Should You Use? <https://www.infoq.com/presentations/rest-graphql-grpc/>

- GraphQL vs gRPC: Which One Creates More Secure APIs? <https://www.trendmicro.com/en_th/devops/22/g/graphql-vs-grpc.html>

- Demystifying edge functions <https://blog.logrocket.com/demystifying-edge-functions/>

- gRPC service in Node.js: Tutorial, Examples and Best practices <https://daily.dev/blog/build-a-grpc-service-in-nodejs>

```text
Should I use a message queue for service to service communication, or a task queue?

https://www.reddit.com/r/microservices/comments/te16hf/should_i_use_a_message_queue_for_service_to/

I actually just popped into this sub for the first time ever while thinking about a similar problem.

To your question, task queues mostly build on message queues with state management. A good example of this is if you have a job that needs processing and it might exist as pending, in-progress, success, or failure states. You'd typically throw tasks into something like celery and then have a worker or series of workers that pull jobs from the task queue to process them, updating the status as it transitions through those lifecycles.

The other piece of this is that you'd typically have the more real-time task queuing component that I mentioned above, and then some kind of longer-term storage, e.g. saving your final job state to a database for reference. Celery also handles this.

It's not hard to build this stuff yourself, Rabbit, Redis, or the like, and I agree with you that do-it-yourself often ends up being simpler and more adaptable. That said, you do have to be more careful to define your internal API and make sure all of your components are all aligned. For example, don't set a status of "failure" in one place and "failed" in another. Language choice and especially using typing constructs can help a lot with this. Since you mentioned Python and JS, you can lean on enums and structural typing in Python and minimally constants in JS (like redux), or possibly typescript or flow.

The interprocess communication and notification flow is an entirely different piece of this. If you go with "build-your-own," and Redis works for your queuing needs, then going with Redis for all of this is a good choice. Redis has reliable pub/sub and robust clients, so you can use it for both the queuing component of this and the interprocess notification. These are two entirely different capabilities. For example, workers would subscribe to a channel in Redis and when new jobs come in a worker would pick up the task and handle it. Redis has transactions too, so you can avoid the problem of multiple workers racing to grab the same job.

If not using Redis for this, then you just need some kind of interprocess communication channel. HTTP JSON APIs are super easy and universally supported, and it can be a tiny, purposeful web server. Fetch and Requests on the client side and maybe express and fastAPI for the server side, and just use JSON. gRPC is another option. IMO the code side of it is a bit complex for simpler designs, but has some really good performance advantages.

Websockets or nanomsg are a reasonable way of handling this and nanomsg is especially lightweight and insanely simple. Just make sure you consider what happens if one or both services are restarted. Server services will typically start themselves just fine, but clients may need to reconnect, and you might need some kind of hello messages or error handling/restart to address a server going away. This is a non-issue with something like HTTP where each request is a new connection, but becomes a concern when you have a long-standing communication channel.

This is more of an architectural thing, but if possible you may also want to consider how you can aggregate most of the interaction with the task queue in one language. This might make the interaction with the task distribution functionality more robust, especially if you piece together your own solution. For example, instead of workers pulling jobs from the queue, a central worker hands jobs to workers. Workers are sort of like Lambda functions where they just take an input and return a result, and only your central task distribution process knows about the internals of this.

In my experience, the industry standard is all over the place, but using Celery or building your own wrapped around Redis or RabbitMQ certainly won't be forging new ground.
```

- task statuses: pending, in-progress, success, failure.

- "or a worker process, graceful shutdown is achieved by returning the current job to the work queue. For example, on RabbitMQ the worker can send a NACK;" (edit: use "transactions" for this)

- "Instead, each running process writes its event stream, unbuffered, to stdout. The event stream for an app can be routed to a file, or watched via realtime tail in a terminal."

- event sourcing, event stores, CQRS

- distributed systems, clusters

- Scaling your Node.js app using distributed queues <https://blog.logrocket.com/scale-node-js-app-using-distributed-queues/>

- Queue Data Structures: How to Build a Node Task Queue <https://www.sitepoint.com/implement-task-queue-node-js/>

```text
job, task and process, what's the difference?

https://stackoverflow.com/questions/3073948/job-task-and-process-whats-the-difference

Fundamentally a job/task is what work is done, while a process is how it is done, usually anthropomorphised as who does it. A job is an overall unit of work, and is composed of tasks. In practice usage is very inconsistent, and often “task” == “process”, though formally a process performs a task.

The job is not done until the processes complete, and a job can be stopped, resumed, or terminated, which corresponds to suspending, resuming, or terminating the processes.

A process is an instance of a program that is being executed, and is the basic unit of resources: a process consists of or “owns” its image, execution context, memory, files, etc.; etymologically a process is the steps done by a processor. A process consists of one or more threads, which are the unit of scheduling, and consist of some subset of a process (possibly shared with other threads): execution context and perhaps more. Traditionally a thread is the unit of execution on a processor (a thread is “what is executing”).

There is a (big, potentially unlimited) queue of incoming tasks (pending), which are performed by a (small, often fixed) set of threads (processes / workers), each task being performed by a single thread, and each thread performing a single task at a time: the active tasks correspond to the active threads.

A job is a unit of work that has been submitted by user.
```

```js
interface Job {
    id: string;
    createdOn: number;
    createdBy: string;
}

interface Task {
    id: string;
    jobId: string; // reference to a parent job
    createdOn: number;
    status: TaskStatus;
    action: TaskAction;
}

enum TaskStatus {
    PENDING = 'pending',
    RUNNING = 'running',
    COMPLETED = 'completed', // success
    FAILED = 'failed' // error
}

interface TaskAction {
    type: string;
    payload: Record<string, unknown>;
}

interface Worker {
    id: string;
    taskId: string // reference to a performing task
    createdOn: number;
}
```

- Use Bull to Manage Job Queues in a Node.js Micro-Service Stack <https://betterprogramming.pub/using-bull-to-manage-job-queues-in-a-node-js-micro-service-stack-7a6257e64509>

- BullMQ with ExpressJS <https://www.thisdot.co/blog/bullmq-with-expressjs/>

- Celery <https://celery-node.js.org/#/>

- Implementing worker queues for processing datasets in Node.js <https://techsparx.com/nodejs/async/queue-processing.html>

- Background Jobs in Node.js with Redis <https://devcenter.heroku.com/articles/node-redis-workers>

- How To Handle Asynchronous Tasks with Node.js and BullMQ <https://www.digitalocean.com/community/tutorials/how-to-handle-asynchronous-tasks-with-node-js-and-bullmq>

- Introduction to Node.js Queues and Jobs: A Practical Guide with Examples <https://www.linkedin.com/pulse/introduction-nodejs-queues-jobs-practical-guide-examples-iqbal/>

- Node Job Queue Libraries <https://byby.dev/node-job-queue-libraries>

- How to Implement Queues In Node.js <https://levelup.gitconnected.com/how-to-implement-queues-in-node-js-8b3a06ce0dd0>

- How to Use Queues in Web Applications – Node.js and Redis Tutorial <https://www.freecodecamp.org/news/how-to-use-queues-in-web-applications/>

- Task Queuing the Easy Way With Node.js and BullMQ <https://www.makeuseof.com/task-queuing-nodejs-bullmq/>

- Boosting Server Performance with Job Queue in Node.js <https://blog.devgenius.io/boosting-server-performance-with-job-queue-in-node-js-3d480079cf31>

- Implementing a job queue in Nodejs <https://sliceofdev.com/posts/implementing-a-job-queue-in-nodejs>

- An Introduction To Queues In Node.js <https://adevait.com/nodejs/introduction-to-queues-nodejs>

- Implementing a Worker Queue using Child Processes <https://www.youtube.com/watch?app=desktop&v=E-01bE2LjxM>

- Worker queues for Node.js <https://www.youtube.com/watch?app=desktop&v=wAEMXVcRbgU>

- Using Temporal as a Node.js Task Queue <https://temporal.io/blog/using-temporal-as-a-node-task-queue>

- A Distributed Work Queue <https://www.yld.io/blog/a-distributed-work-queue/>

- What is an Event-Driven Architecture? <https://aws.amazon.com/event-driven-architecture/>

- Event Creation and Handling Techniques in TypeScript <https://hackwild.com/article/event-handling-techniques/>

- Difference between Event Bus, Message Queue, and Message Broker <https://pandaquests.medium.com/difference-between-event-bus-message-queue-and-message-broker-a8630a8823f7>

- rabbitmq vs kafka

- ACID, CAP, and BASE <https://medium.com/@pranabj.aec/acid-cap-and-base-cc73dee43f8c>

- Distributed System / Databases: CAP, ACID, and BASE <https://www.linkedin.com/pulse/distributed-system-databases-cap-acid-base-kuldeep-pal/>

- how indexes work?

- types of locks in transactions?
