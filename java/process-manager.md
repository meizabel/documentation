# Process Manager

Process Manager coordinates and routes messages between aggregates within a given Bounded Context (BC). It is A central processing unit which maintains the state of the business process and determines the next processing step based on intermediate results.

Event and Command Handlers are invoked by the [ProcessManagerRepository](./repository.md) which manages the instances of a Process Manager class.

“Process Manager” pattern was first defined and brought to the common vocabulary by Kyle Brown and Bobby Woolf under the guidance of Martin Fowler in the book [“Enterprise Integration Patterns”](http://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html).

For more information on Process Managers (and the important difference between Process Manager and Saga), please see:  
[Clarifying the Saga pattern](http://kellabyte.com/2012/05/30/clarifying-the-saga-pattern/)  
[Are Sagas and Workflows Same Thing?](https://dzone.com/articles/are-sagas-and-workflows-same-t)

### How to Define a Process Manager

In Spine, a Process Manager consists from its [state](../biz-model/process-manager-states.md) defined as a protobuf message and a Java class which manages this state. 
The main steps to define a Process Manager are:

* Select a type for identifiers of the process managers. If you select to use a typed identifier (which is recommended), you need to define a protobuf message for the ID type.
* Define a Process Manager state structure as a protobuf message.
* Generate Java code for the ID and state types.
* Create a new Process Manager class derived from [org.spine3.server.procman.ProcessManager](https://github.com/SpineEventEngine/core-java/blob/037ac4d9e7133a95c75d927e5b649ab4f6f0f7f2/server/src/main/java/org/spine3/server/procman/ProcessManager.java) passing the ID and state type parameters.

#### Constructor 

An Aggregate must have a public constructor initializing an Aggregate ID. It must be public as it serves as a public API for Spine (it is used by the [Repository](./repository.md)).

```java
public OrderAggregate(OrderId id) {
        super(id);
}
```
### Command Handlers

An Aggregate contains [Command Handlers](/command-handler.md), which are methods annotated with `@Assign` and have a command message and a command context as parameters. An example of the Command Handler of the OrderAggregate:
