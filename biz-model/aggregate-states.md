# Defining Aggregate State

An **Aggregate** is defined as [Java class](../java/aggregate.md). The aggregate handles commands. In response to a command the aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate.

An **Aggregate State** is a data structure and is defined as a protobuf message.
The aggregate state as a *typed* thing.


An Aggregate State consists of the: [Identifier](./identifiers.md) and aggregate components (Value Objects and Entities).

An identifier type should be already set by the time of creating an aggregate state. We recommend to have [typed](../motivation/strongly-typed.md) identifiers. For example, if you have an `Order` aggregate, there should be an `OrderId` defined as a protobuf message.

A `Message`-based ID, typically, would reside in the protobuf package of an aggregate.

Below you can see a sample of the `Order` aggregate state definition:

```protobuf
message Order {
    // The unique order id.
    sample.OrderId id = 1;

    // The conference id the order associated with.
    sample.ConferenceId conference_id = 2;

    // The lines of the order.
    repeated sample.OrderLine line = 3;

    // The order is confirmed when the registrant has successfully paid for the order items.
    bool is_confirmed = 4;
}
```

