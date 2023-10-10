# Microservices: a child service notifies a parent service when a task is completed (RabbitMQ)

The child service simulates completing a task and sends a JSON message to the taskCompleted queue when the task is done.

The parent service connects to the same taskCompleted queue and sets up a callback function to handle incoming messages. When a message is received, it parses the JSON content and processes the notification.

Both services use the amqplib library to interact with RabbitMQ.

Make sure you have RabbitMQ installed and running locally on the default configuration (amqp://localhost) for this code to work. You can adjust the logic in the parent service's callback function to perform any actions required when a child task is completed.

## Child service

```js
const amqp = require('amqplib');

async function main() {
  // Connect to RabbitMQ server
  const connection = await amqp.connect('amqp://localhost');
  const channel = await connection.createChannel();

  // Declare a queue for task completion notifications
  const queueName = 'taskCompleted';
  await channel.assertQueue(queueName);

  // Simulate a child task completion
  const task = {
    taskId: '123',
    status: 'completed',
  };

  // Convert the task object to JSON and send it to the queue
  const message = JSON.stringify(task);
  channel.sendToQueue(queueName, Buffer.from(message));

  console.log('Child task completed and notification sent');

  // Close the connection
  setTimeout(() => {
    connection.close();
  }, 500);
}

main().catch((err) => {
  console.error(err);
});
```

## Parent service

```js
const amqp = require('amqplib');

async function main() {
  // Connect to RabbitMQ server
  const connection = await amqp.connect('amqp://localhost');
  const channel = await connection.createChannel();

  // Declare the same queue for task completion notifications
  const queueName = 'taskCompleted';
  await channel.assertQueue(queueName);

  // Set up a callback function to handle incoming messages
  channel.consume(queueName, (message) => {
    const task = JSON.parse(message.content.toString());
    console.log(`Received notification for Task ID: ${task.taskId}, Status: ${task.status}`);

    // Perform any necessary actions in response to the task completion notification
    // For example, update the parent task's state, trigger additional tasks, etc.

    // Acknowledge the message
    channel.ack(message);
  });

  console.log('Waiting for child task completion notifications. To exit, press Ctrl+C');
}

main().catch((err) => {
  console.error(err);
});
```
