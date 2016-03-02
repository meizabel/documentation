# Process Manager

Process Manager coordinates and routes messages between aggregates within a Bounded Context (BC). It is a central processing unit which maintains a state of a business process and determines the next processing step based on intermediate results.

Event and Command Handlers are invoked by the [ProcessManagerRepository](./repository.md) which manages instances of a Process Manager class.

“Process Manager” pattern was first defined and brought to the common vocabulary by Kyle Brown and Bobby Woolf under the guidance of Martin Fowler in the book [“Enterprise Integration Patterns”](http://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html).

For more information on Process Managers (and the important difference between Process Manager and Saga), please see:
* [Clarifying the Saga pattern](http://kellabyte.com/2012/05/30/clarifying-the-saga-pattern/)  
* [Are Sagas and Workflows Same Thing?](https://dzone.com/articles/are-sagas-and-workflows-same-t)

### How to Define a Process Manager

A Process Manager is defined as a Java class which encapsulates and manages its [state](../biz-model/process-manager-states.md) which is defined as a protobuf message.  
The main steps to define a Process Manager are:

* Select a type of identifiers of this kind of process managers. If you decide to use a typed identifier (which is recommended), you need to define it as a protobuf message.
* Define a Process Manager state structure as a protobuf message.
* Generate Java code for the ID and state types.
* Create a new Process Manager class derived from [ProcessManager](https://github.com/SpineEventEngine/core-java/blob/037ac4d9e7133a95c75d927e5b649ab4f6f0f7f2/server/src/main/java/org/spine3/server/procman/ProcessManager.java) abstract base class, passing the ID and state type parameters:

```java
public class RegistrationProcessManager extends ProcessManager<ProcessManagerId, RegistrationProcess> {
    // code of the process manager
}
```

#### Constructor 

A Process Manager must have a public constructor initializing a Process Manager ID. It must be public as it serves as a public API for Spine (it is used by the [ProcessManagerRepository](./repository.md)).

```java
public RegistrationProcessManager(ProcessManagerId id) {
    super(id);
}
```
### Event Handlers
A Process Manager handles domain events. In [Event Handler](./event-handler.md), it usually performs the following:
* sends commands to Aggregates based on conditions like current process state;
* changes the current process state;
* throws a [Business Failure](../biz-model/failures.md) if the process is in an inappropriate state, etc.

```java
@Subscribe
public void on(PaymentCompleted event, EventContext context) throws IllegalProcessStateFailure {
    final RegistrationProcess.State processState = getState().getProcessState();
    if (processState == RESERVATION_CONFIRMED) {
        setProcessState(PAYMENT_COMPLETED);
        sendConfirmOrderCommand(event);
    } else {
        throw new IllegalProcessStateFailure(event);
    }
}
```

### Command Handlers

Process Managers can also [handle commands](./command-handler.md), for example, to stop or restart the process. Handling commands is more rare case than handling events. Here is an example of Command Handler:

```java
@Assign
public CommandRouted handle(StopRegistrationProcess stopCmd, CommandContext context) {
    final RegistrationProcess.State state = getState().getProcessState();
    if (state != COMPLETED) {
        setIsCompleted(true);
        final RejectOrder rejectOrderCmd = newRejectOrderCommand();
        final CancelSeatReservation cancelReservationCmd = newCancelSeatReservationCommand();
        return newRouter().of(stopCmd, context)
                .add(rejectOrderCmd)
                .add(cancelReservationCmd)
                .route();
    } else {
        throw newIllegalProcessStateFailure();
    }
}
```
Use a **Command Router** to create and post command(s) in response to a command received by the Process Manager. 
The routed commands are created on behalf of the actor of the original command. That is, the actor and zoneOffset fields of created CommandContext instances will be the same as in the incoming command.