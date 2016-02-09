#  Writing Events

An Event, similarly to Aggregate State and Command, is defined as protobuf message. 

`Event` is something, which happened in the past.
//
// An event consists of two parts: event message and its context.
//
// The `message` is the domain model part of the event. Event messages are formulated in the past tense.
// The type of the event is defined by the type of the enclosed message.
// When we speak about a 'command' as a typed thing, we refer to the message of the event.
//
// Event handlers are associated with the type of the messages. There can be multiple handlers
// per event type.
//
// The event context contains attributes common for all events. It can also contain additional attributes
// added by the code handling the event.
//
message Event {
    // The message of the event message wrapped into `Any`.
    google.protobuf.Any message = 1;

    // The context of the event.
    EventContext context = 2;
}

// Meta-information for an event.
message EventContext {
    // The id of the event.
    EventId event_id = 1;

    // When the event occurred.
    google.protobuf.Timestamp timestamp = 2;

    // The context of the command, which generated this event.
    CommandContext command_context = 3;

    // The id of the aggregate the event was applied to.
    google.protobuf.Any aggregate_id = 4;

    // The version of the aggregate after the event was applied.
    int32 version = 5;

    // Service attributes that the system wants to store in addition to the domain attributes
    // defined in the event message.
    map<string, google.protobuf.Any> attributes = 6;
}