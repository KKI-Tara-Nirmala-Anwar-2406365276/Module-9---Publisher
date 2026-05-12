Module 9 - Publisher

1. How much data will the publisher program send to the message broker in one run?
The publisher program will send five data messages to the message broker in one run. 
Each message is a UserCreatedEventMessage that contains two fields, which are user_id and user_name. 
The first message has user_id 1 and user_name 2406365276-Amir. 
The second message has user_id 2 and user_name 2406365276-Budi. 
The third message has user_id 3 and user_name 2406365276-Cica. 
The fourth message has user_id 4 and user_name 2406365276-Dira. 
The fifth message has user_id 5 and user_name 2406365276-Emir.

2. The URL amqp://guest:guest@localhost:5672 is the same as in the subscriber program, what does it mean?
The URL is the AMQP connection URL used to connect the publisher to RabbitMQ. 
The first guest is the username used to access RabbitMQ. 
The second guest is the password for that username. 
The localhost part means RabbitMQ is running on my own local computer. 
The number 5672 is the default port used by RabbitMQ for AMQP connections. 
This URL is the same as the subscriber because both publisher and subscriber need to connect to the same message broker.

3. Running RabbitMQ as message broker
![RabbitMQ Running](rabbitmq-running.png)

4. Sending and processing event

When I ran the subscriber program, it connected to RabbitMQ and waited for messages from the user_created queue. 
Then when I ran the publisher program, it sent five UserCreatedEventMessage events to the message broker. 
The subscriber received those five events and printed each message in the console. 
RabbitMQ also showed an active connection, channel, queue, and consumer, which means the message broker was running and connected to the subscriber. 
This proves that the publisher and subscriber communicate indirectly through RabbitMQ instead of calling each other directly. 
The event-driven flow worked because the publisher only sent events to the broker, while the subscriber consumed and processed them from the broker.

![Sending and processing event](sending-event.png)

5. Monitoring chart based on publisher

After running the publisher program again, the RabbitMQ message rate chart showed a spike. 
The spike appeared because the publisher sent five UserCreatedEventMessage events to RabbitMQ in one run. 
RabbitMQ recorded this publishing activity in the message broker chart. 
The subscriber was also connected, so the messages could be delivered and processed after being published. 
This shows that the publisher does not send data directly to the subscriber, but sends events through RabbitMQ. 
The chart proves that RabbitMQ can monitor message traffic between the publisher and subscriber.

![Monitoring chart based on publisher](monitoring-chart.png)