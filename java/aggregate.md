## Defining an Aggregate

In domain-driven design (DDD), an aggregate defines a consistency boundary. External references are restricted to one member of the Aggregate, designated as the root. A set of consistency rules applies within the Aggregate’s boundaries.

Typically, when you implement the CQRS pattern, the classes in the write model define your aggregates. Aggregates are the recipients of commands, and are units of persistence. After an aggregate instance has processed a command and its state has changed, the system must persist the new state of the instance to a storage. `TODO: create corresponding Article`.

In Spine an [**aggregate state**](../biz-model/aggregate-states.md) is defined in a protobuf message, while aggregate itself is a java class. 

An **aggregate** should be inherited from the Spine abstract `Aggregate` class. And have two parameters defined: ID and  Aggregate State.

```java
public class OrderAggregate extends Aggregate<OrderId, Order> {
}
```
Then create a new instance of the aggregate using a `Constructor`. Constructor method should be `public` as it serves as a public API for Spine. With its help new instances of the aggregate will be added to the Repository. 
```java
 public OrderAggregate(OrderId id) {
        super(id);
}
```
An aggregate should also contain at least one [Command Handler](/java/command-handler.md) method and one Event Applier.


```java
 @Assign
    public List<Message> handle(RegisterToConference command, CommandContext context) {
        checkNotConfirmed(getState(), command);
        validateCommand(command);

        final ImmutableList.Builder<Message> result = ImmutableList.builder();
        final boolean isNew = getVersion() == 0;
        if (isNew) {
            final OrderPlaced placed = EventFactory.orderPlaced(command);
            result.add(placed);
        } else {
            final OrderUpdated updated = EventFactory.orderUpdated(command);
            result.add(updated);
        }
        final OrderTotalsCalculated totalsCalculated = buildOrderTotalsCalculated(command.getOrderId(),
                command.getConferenceId(), command.getSeatList());
        result.add(totalsCalculated);
        return result.build();
    }
```
### Event Applier
Event applier is a method of an aggregate root which applies data from an event to the state of the aggregate.

Event appliers are part of the private API of aggregate roots. As such they are declared private by convention set in the Spine framework:

``````java
 @Apply
 private void on(MyEvent event) {
     MyState newState = getState().toBuilder()
       .setMyProperty(event.getProperty())
       .build();
     validate(newState);
     setState(newState);
 }
``````