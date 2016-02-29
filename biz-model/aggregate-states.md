# Defining Aggregate State

An **Aggregate** is defined as [Java class](../java/aggregate.md). The Aggregate handles commands. In response to a command an aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate.

An **Aggregate State** represents data structure and is defined as a protobuf message. The `message` is the domain model part of the Aggregate.

When we speak about a **event** as a typed thing, we refer to the message of the event.
Event handlers are associated with the type of the messages. There can be multiple handlers
per event type.

An Aggregate State consists of the Aggregate Identifier and  at least one more field.
