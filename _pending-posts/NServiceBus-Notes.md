Install binaries from NuGet

RunMeFirst.bat is a quick way to do a default installation on a clean machine


2 assemblies are required if you are going to host a service bus
NServiceBus
NServiceBus.Core

What is a host
- a host is something that can host and run a connection point to the bus inside of it (websites, windows services, etc)
- connections to a bus are called end points
- on a single server you can have as many hosts and end points as you like


Nservicebus host is a general purpose host that comes with NService bus that makes it easy to run the host environment


## Basics of one way messaging ##

Both the intent and payload are sent with the message - this means we can use a queuing system (think of it like a mailbox)

compare messaging vs rpc (remote procedure call)

RPC - Intent and payload are physically separated
Messaging - Intent and Data is transported as one physical package


- Good practice for message definitions to be in their own separate assembly

### Sending a message ###

Use IBus interface, this is the primary way of interacting with the message bus

~~~
Bus.Send("where", objectToSend);
~~~

or 

~~~
Bus.Send(objectToSend);

// Specify message endpoint mappings in app.config file
~~~


- Use the same serializer on all end points otherwise it will not be able to deserialize messages


#### Endpoints and Queues ####

- Each endpoint has its own queue (think of it like a house having a physical mailbox)
- Convention is to name the input queue the same as the end point

It is the responsbility of an endpoint to create its own queues

Default msm queues for an endpoint are (assuming endpoint name is BusStop):
- 

### Falacies of distributed computing ###

- If you assume these to be true, you are in deep trouble when building distributed systesm

1) The network is reliable
2) Latency isn't a problem
3) Bandwidth isn't a problem
4) The network is secure
5) The topology won't change
6) The admin will know what to do when things fail
7) Transport cost ins't a problem
8) The network is homogenous

Challenges with RPC
- RPC is easy to code, fooled that it is a linear path of execution
- Can't reason about the time between on line of code and another

Messaging makes this all explicit

How does async messaging help us with the falacies of DC

- No threads are blocked on the client side
- Uses store and forward writes to disk which makes it resilient in the face of failures

#### Dangers of store and forward ####

- target server off for an extended period of time - running out of space or crash)

## Exception Management ##

Basics of exceptions
- Deadlock in a DB
- Database is down
- Message deserialization fails

(Transient vs Permannent Exceptions) Transient expections often are resolved with a retry

NServiceBus has the built in capability of doing retries (by default 5 quick retries)
SecondLevelRetries with a time interval between retries solves database down issues
Messages that always fail are moved to an error queue

DTC - distributed transaction coordinate

To find it, in Windows:
Under component services > Compoent services > My Computer > Distributed Transaction Coordinator > Local DTC






