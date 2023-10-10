# Microservices: RabbitMQ - a child service notifies a parent service when a task is completed

In a microservices architecture, communication between services is typically asynchronous, and services should be decoupled as much as possible. To notify a parent task when a child task is done, you can use various messaging patterns and technologies. One common approach is to employ a message broker, such as Apache Kafka, RabbitMQ, or AWS SQS, to facilitate communication between microservices. Here's a high-level overview of how you can achieve this:

1. **Messaging Queue Setup**: Set up a message queue or topic on your chosen message broker. You will use this queue to publish messages about the completion of child tasks.

2. **Child Service**: In the microservice responsible for handling the child task, implement logic to publish a message to the message queue when the task is complete. This message should contain information about the task's status, ID, or any relevant data.

3. **Parent Service**: In the microservice responsible for the parent task, subscribe to the message queue or topic. When it receives a message about a child task being completed, it can process the message and take any necessary actions, such as updating its own state or triggering additional tasks.

4. **Message Payload**: When designing the message payload, ensure it includes enough information for the parent service to identify which child task has completed and take appropriate action. This might involve including task IDs or other metadata.

5. **Error Handling**: Implement error handling and retry mechanisms to handle situations where messages are not delivered or processing fails. You may need to ensure message delivery guarantees based on your application's requirements.

6. **Scalability**: Ensure that your messaging system and services are designed to scale horizontally to handle increased message volume and service load.

Here's a simplified example in Python using a message broker (RabbitMQ) and the `pika` library:

## Child service

```python
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

# Declare a queue for task completion notifications
channel.queue_declare(queue='task_completed')

# Perform the child task
# ...

# Publish a message when the task is done
channel.basic_publish(exchange='', routing_key='task_completed', body='Child Task ID 123 is done')

# Close the connection
connection.close()
```

## Parent services

```python
import pika

def callback(ch, method, properties, body):
    print(f"Received message: {body}")
    # Process the message and update the parent task's state

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

# Declare the same queue for task completion notifications
channel.queue_declare(queue='task_completed')

# Set up a callback function to handle incoming messages
channel.basic_consume(queue='task_completed', on_message_callback=callback, auto_ack=True)

print('Waiting for child task completion notifications. To exit, press Ctrl+C')
channel.start_consuming()
```
