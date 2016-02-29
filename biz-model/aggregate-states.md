# Defining Aggregate State

An **Aggregate** is defined as [Java class](../java/aggregate.md). The aggregate handles commands. In response to a command the aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate.

An **Aggregate State** represents data structure and is defined as a protobuf message. The `message` is the domain model part of the Aggregate.
When we speak about an aggregate state as a *typed* thing, we refer to the message of the Aggregate.


An Aggregate State consists of the: 
* Aggregate [Identifier](./biz-model/identifiers.md)
* At least one other attribute (Entity or Value object)

An identifier type should be already set by the time of creating an aggregate state. We recommend to have [typed](../motivation/strongly-typed) identifiers. So, if you have the `Order` class for one of your aggregates, there should be an `OrderId`.

A `Message`-based ID type, typically, would reside in the protobuf package of an aggregate.

Below you can see a sample of the `Order` aggregate state definition:

```protobuf
message Order {
    // The unique order id.
    spine.samples.lobby.common.OrderId id = 1;

    // The conference id the order associated with.
    spine.samples.lobby.common.ConferenceId conference_id = 2;

    // The set of seat items representing seat quantities of different types.
    repeated spine.samples.lobby.registration.contracts.SeatQuantity seat = 3;

    // The order is confirmed when the registrant has successfully paid for the order items.
    bool is_confirmed = 4;
}
```

