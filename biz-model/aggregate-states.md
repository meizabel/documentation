# Defining Aggregate State

An Aggregate State represents data structure and is defined as a protobuf message.

An **Aggregate** is defined as [Java class](../java/aggregate.md). The Aggregate handles commands, applies events, In response to a command an aggregate modifies its state and produces one or more events. These events are used later to restore the state of the aggregate.

An event consists of two parts: event message and its context.

The `message` is the domain model part of the event. Event messages are formulated in the past tense.The type of the event is defined by the type of the enclosed message.

When we speak about a **event** as a typed thing, we refer to the message of the event.
Event handlers are associated with the type of the messages. There can be multiple handlers
per event type.


