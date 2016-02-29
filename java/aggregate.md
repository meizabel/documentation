## Defining an Aggregate

In domain-driven design (DDD), an aggregate defines a consistency boundary. External references are restricted to one member of the Aggregate, designated as the root. A set of consistency rules applies within the Aggregate’s boundaries.

Typically, when you implement the CQRS pattern, the classes in the write model define your aggregates. Aggregates are the recipients of commands, and are units of persistence. After an aggregate instance has processed a command and its state has changed, the system must persist the new state of the instance to a storage. `TODO: create corresponding Article`.

In Spine an [**aggregate state**](../biz-model/aggregate-states.md) is defined in a protobuf message, while aggregate itself is a java class. 

An **aggregate** should be inherited from the Spine abstract `Aggregate` class. And have two parameters defined: ID and State.

```java
public class OrderAggregate extends Aggregate<OrderId, Order> {
}
```