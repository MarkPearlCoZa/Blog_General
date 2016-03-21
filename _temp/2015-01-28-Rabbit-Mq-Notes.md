---
layout: post
title: Rabbit MQ Notes
tags: Messaging
category: General
---
### General ###

#### General Characteristics of Messaging ####

- Asynchronous  
- Can be reliable  
- Can be durable  
- Routing  
- Many message formats  
- Recipients pull messages from a queue  

#### Key Concepts of AMQP ####

- Message Broker (Centralized system that other systems would hook in to for messages)  
- Exchanges (Direct, Fan-Out, Topic, Headers)  
- Queues (FIFO)  
- Bindings (Binds an exchange to a queueu)   

#### Queue Persistance ####

- Durable (Msg saved to disk, Msg is still alive after server restart)  
- Non-Durable (Msg only held in memory, better performance)  

#### Messaging Patterns ####

- Simple One Way Message Pattern  
- Worker Queues Patter   
- Publish Subscribe Pattern  
- Remote Procedure Call Pattern  

-------------------------------------------------------------------------------------------------

### Installing RabitMq ###

- [Installing RabitMq on Windows](http://www.rabbitmq.com/install-windows.html)  

-------------------------------------------------------------------------------------------------

### RabbitMQ Web Portal ###

#### To Enable Web Portal ####

~~~
rabbitmq-plugins enable rabbitmq_management
~~~

#### Web Portal Default Url ####

~~~
http://server-name:15672/
~~~

[http://localhost:15672/](http://localhost:15672/)

Default web login credentials are :  
username : guest  
password : guest  

-------------------------------------------------------------------------------------------------

### Command Line Tools ###

- RabbitMqCtl (Stop, Reset, Stop_app, Start_app)  
- RabbitMq-Service (Stop, Start, Install)  

#### List all exchanges ####

~~~
rabbitmqctl list_exchanges
~~~



-------------------------------------------------------------------------------------------------

### .Net Specific Stuff ###

#### Nuget Install ####

- RabbitMQ.Client

~~~
Install-Package RabbitMQ.Client
~~~

#### Api Types with .Net ####

- IConnection
- IModel  
- ConnectionFactory  
- QueueingBasicConsumer  
- Protocols  

#### Basic Example ####

~~~
var connectionFactory = new RabbitMQ.Client.ConnectionFactory() { ... };
var connection = connectionFactory.CreateConnection();
var model = connection.CreateModel();
~~~

#### Send a Basic Message ####

~~~
static void SendMessage()
{
	var factory = new ConnectionFactory() {HostName = "localhost"};
	using (var connection = factory.CreateConnection())
	{
		using (var channel = connection.CreateModel())
		{
			channel.QueueDeclare("hello", false, false, false, null);
			var message = "Hello Worlds!";
			var body = Encoding.UTF8.GetBytes(message);
			channel.BasicPublish("", "hello", null, body);
			Console.WriteLine(" [x] Sent {0}", message);
		}
	}
}
~~~

#### Receive a Basic Message ####

~~~
static void ReceivedMessages()
{
	var factory = new ConnectionFactory() {HostName = "localhost"};
	using (var connection = factory.CreateConnection())
	{
		using (var channel = connection.CreateModel())
		{
			channel.QueueDeclare("hello", false, false, false, null);
			var consumer = new QueueingBasicConsumer(channel);
			channel.BasicConsume("hello", true, consumer);
			Console.WriteLine(" [*] Waiting for messages." + "To exit press Ctrl+C");

			while (true)
			{
				var ea = (BasicDeliverEventArgs) consumer.Queue.Dequeue();
				var body = ea.Body;
				var message = Encoding.UTF8.GetString(body);
				Console.WriteLine(" [x] Recieved {0}", message);
			}
		}
	}
}
~~~

#### Serialization & Data ####

##### Encoding a String #####

Object -> byte array = Serialization  

~~~
var message = "Hello Worlds!";
var body = Encoding.UTF8.GetBytes(message);
~~~

Byte array -> object = De-serialization

~~~
var message = Encoding.UTF8.GetString(body);
~~~

##### Encoding a Object #####

Assume you have an object of type MyMessage.  

Object -> byte array = Serialization  

~~~ 
var jsonString  = Newtonsoft.Json.JsonConvert.SerializeObject(myMessage);
byte[] messageBuffer = Encoding.Default.GetBytes(jsonString);
~~~

Byte array -> object = De-serialization

~~~
var jsonString = Encoding.Default.GetString(deliveryArgs.Body);
var myMessage = Newtonsoft.Json.JsonConvert.DeserializeObject<MyMessage>(jsonString);
~~~

#### References ####

[Explanation about AMQP on RabbitMQ](https://www.rabbitmq.com/tutorials/amqp-concepts.html)  
[Getting started tutorials](https://www.rabbitmq.com/tutorials)  
[PluralSight RabbitMQ for .Net Part 1](http://www.pluralsight.com/courses/rabbitmq-dotnet-developers)  
