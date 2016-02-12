  

# Spine Event Engine Concepts

This chapter introduces some key concepts Spine is based on. The framework provides implementation for most important building blocks of a CQRS/ES application. In terminology we heavily lean on [Domain-Driven Design](https://www.wikiwand.com/en/Domain-driven_design) (DDD) and the [“Big Blue Book”](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) by Eric Evans, and on [“Enterprise Integration Patterns”](http://www.amazon.com/o/asin/0321200683/ref=nosim/enterpriseint-20) by Kyle Brown and Bobby Woolf. 

Below you can find a typical Spine Event Engine application architecture. The concepts behind these building blocks are desrcibed in the sections below.

![Spine Event Engine Diagram](Diagram-SpineEventEngine.svg)

`TODO: rename the file to Spine-Application-Architecture.svg`

---


## Domain Model Concepts

**Command** are messages that instruct a specific entity to perform a certain action. Unlike an event, a command is not a statement of fact; it is only a request, and thus may be refused. A typical way to convey refusal is to throw an error or failure. In Spine [command](/java/commands.md) is defined as a protobuf message.

**Event** is something that happened in the past.
All changes to an application state are captured as a sequence of events. Events is the main “database” of the application. In Spine [events](/java/event.md) are defined as protobuf messages as well.

**Error** — `TODO: define`

**Failure** — `TODO: define`

**Command Handler** is an object, which receives commands, modifies the state of the application, and generates events if the modification was successful. `TODO: links?`

**Aggregate** is the main building block of a business model. [Aggregates](http://martinfowler.com/bliki/DDD_Aggregate.html) guarantee consistency of data modifications in response to commands they receive. Aggregate is the most common case of Command Handler. In response to a command an aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate. In Spine aggregates are [defined as Java classes](/java/aggregate.md), and their states are [defined as protobuf messages](/biz_model/aggregate_states.md).

** Event Handler** is an object that is subscribed to receive events.

** Process Manager** `TODO: new description needed.` A process manager can be both Command Handler and Event Handler.

**Projection** is an Event Handler, which transforms multiple events data into a structural representation. Projections are main building blocks of Query side of the application. `TODO: links.` 

**Entity Fragment** `TODO: define`.

## Architectural Concepts

**Bounded Context** — `TODO: define. Mention multiple contexts and how they interact.`

**Repository** is a mechanism for encapsulating storage, retrieval, and search behavior which emulates a collection of objects. It isolates domain objects from details of the database access code. *Aggregate Repository*, *Process Manager Repository*, and *Projection Repository* are types of the repositories your application would have.

**Command Bus** is responsible for routing the command to its handler. Unlike a Command Handler it does not change business model or produce events.

**Event Bus** allows publish-subscribe-style communication between components without requiring the components to explicitly register with one another (and thus be aware of each other).

**Command Store** keeps the history of all the commands of the application and statuses of their execution.

**Event Store ** keeps all the events of the application in the chronological order, which is also called *Event Stream*. New projections are built by passing the event stream “throught” them. `TODO: link to the example.`

**Query Service** returns data to the client applications in response to a query. The query is the request for:
* state of one or more aggregates or their fragments;
* one or more projection states or their fragments.


** Aggregate Stand ** serves latest states of aggregates. It is called that way to emphasize its _“read”_ nature. It may return complete state, or its fragment, if corresponding query requests partial representation.

___

For more information read [Creating Business Model](/biz_model/java.md) and [Java](/java/README.md) chapters.
