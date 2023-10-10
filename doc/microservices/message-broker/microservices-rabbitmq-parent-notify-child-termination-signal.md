# Microservices: RabbitMQ - a parent service that notifies child services with a termination signal

In this example:

- The parent service sends a termination signal by publishing a message to an exchange (broadcasting to all queues).

- Each child service consumes messages from the termination queue and performs any necessary cleanup actions upon receiving the termination signal.

Make sure you have RabbitMQ running, and modify the connection URL in both the parent and child services as needed.

## Parent service

```js
const amqp = require('amqplib');

async function notifyChildServices() {
  try {
    const connection = await amqp.connect('amqp://localhost'); // RabbitMQ server connection
    const channel = await connection.createChannel();

    const exchangeName = 'termination_exchange';
    const queueName = 'termination_queue';

    // Declare an exchange and a queue
    await channel.assertExchange(exchangeName, 'fanout', { durable: false });
    const { queue } = await channel.assertQueue(queueName);

    // Bind the queue to the exchange
    channel.bindQueue(queue, exchangeName, '');

    // Send the termination signal
    channel.publish(exchangeName, '', Buffer.from('Termination signal'));

    console.log('Termination signal sent to child services.');

    // Close the channel and connection
    await channel.close();
    await connection.close();
  } catch (error) {
    console.error('Error:', error);
  }
}

// Call the function to send the termination signal
notifyChildServices();
```

## Child service

Each child service should consume messages from the termination queue.

```js
const amqp = require('amqplib');

async function startChildService() {
  try {
    const connection = await amqp.connect('amqp://localhost'); // RabbitMQ server connection
    const channel = await connection.createChannel();

    const queueName = 'termination_queue';

    // Declare the same queue
    const { queue } = await channel.assertQueue(queueName);

    // Consume messages from the termination queue
    channel.consume(queue, (message) => {
      if (message) {
        console.log('Received termination signal:', message.content.toString());
        // Perform cleanup or any necessary actions here
        channel.ack(message); // Acknowledge the message
      }
    });

    console.log('Child service started. Waiting for termination signal...');
  } catch (error) {
    console.error('Error:', error);
  }
}

// Start the child service
startChildService();
```
