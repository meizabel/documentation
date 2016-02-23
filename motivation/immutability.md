# Bebefit of Immutability

An immutable object is one whose externally visible state cannot change after it is instantiated. The string type in Java and C# is a familiar example; you never actually change an existing string value, you just create new string values based on old ones.

Immutable objects greatly simplify your program, since they:

* are simple to construct, test, and use
* can be freely shared and references to immutable objects cached without having to copy or clone them
* are automatically thread-safe and have no synchronization issues

In [Effective Java](http://www.amazon.com/exec/obidos/ASIN/0321356683/ref=nosim/javapractices-20), Joshua Bloch makes this compelling recommendation :
>Classes should be immutable unless there's a very good reason to make them mutable....If a class cannot be made immutable, limit its mutability as much as possible.

### Commands must be immutable.
Commands are immutable because their expected usage is to be sent directly to the domain model side for processing. They do not need to change during their projected lifetime in traveling from client to server.

Commands form part of the lexicon or ubiquitous language. Naming a command is a careful process. It should be intention revealing. It should also be understandable by the domain experts.

Upgrading commands becomes necessary when new requirements cause existing commands not to be sufficient. Maybe a new field needs to be added, for example, or maybe an existing field should really have been split into several different ones.

#### How do I upgrade my commands?

How you do the upgrade depends how much control you have over your clients. If you can deploy your client updates and server updates together, just change things in both and deploy the updates. Ta da! You are done. If not, it’s usually best to have the updated command be a new type and have the command handler accept both for a while.


### Events must be immutable.
The idea of having immutable events is incredibly powerful because it completely solves one of the primary challenges in computing-concurrency and the need for a single, authoritative source of truth. 

Once an event has been accepted and committed, it becomes an established fact — as unalterable as a decree from Pharaoh — and it can be copied everywhere. The only way to “undo” an event is to add a compensating event on top — like a negative transaction in accounting.

Consequently the storage mechanism that we use to persist our events becomes very simple. It is basically a stack. We continuously append new events on top of the stack. Existing events are never touched again. No update or delete operation is defined, only add operations are ever possible.

Similarly to Commands, events may need to be updated as application and business model evolves. Scenarios where event modification can occure.

#### Redundant events
If your system no longer uses a particular event type, you may be able to simply remove it from the system. However, if you are using event sourcing, your event store may hold many instances of this event, and these instances may be used to rebuild the state of your aggregates. Your aggregates must continue to be able to handle these old events when they are replayed from the event store even though the system will no longer raise new instances of this event type.

#### New event types
If you introduce new event types into your system, this should have no impact on existing behavior. Typically, it is only new features or functionality that use the new event types.

#### Changing existing event definitions
Handling changes to event type definitions requires more complex changes to your system. For example, your event store may hold many instances of an old version of an event type while the system raises events that are a later version, or different bounded contexts may raise different versions of the same event. Your system must be capable of handling multiple versions of the same event. Some ways to handle versioning are described in the “CQRS Journey” [Reference 4: A CQRS and ES Deep Dive](https://msdn.microsoft.com/en-us/library/jj591577.aspx) chapter.


### Isolation of storage and deployment aspects from the main code
Another level you can apply immutability at is the data store. With Event sourcing notion, you can write your application in a way that it stores data in “append-only” fashion to pretty much any data store technology that exists.

The CQRS pattern enables data and objects segregation in your applications. The write model can use a database that is optimized for writes by being fully normalized. The read model can use a database that is optimized for reads by being denormalized to suit the specific queries that the application must support on the read side.

Several benefits come from this: 
* better performance because each database is optimized for a particular set of operations, 
* better scalability because you can scale out each side independently, and 
* simpler locking schemes. On the write side you no longer need to worry about how your locks impact queries, and on the read side your database can be read-only.

If you capture changes in your write model as events, you can save all of your changes simply by appending those events to your database or data store on the write side using only Insert operations.

You can also use those same events to push your changes to the read side. You can use those events to build projections of the data that contain the data structured to support the queries on the read side.