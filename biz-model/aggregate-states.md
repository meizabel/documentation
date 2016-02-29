# Defining Aggregate State

An **Aggregate** is defined as [Java class](../java/aggregate.md). The Aggregate handles commands. In response to a command an aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate.

An **Aggregate State** represents data structure and is defined as a protobuf message. The `message` is the domain model part of the Aggregate.

An Aggregate State consists of the Aggregate Identifier and  at least one more field.

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