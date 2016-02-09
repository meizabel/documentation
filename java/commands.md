# Writing Commands

Commands, as well as Events and Aggregate State are defined as protobuf messages.
`Command` is an instruction to do something.

A command consists of two parts: 
* command message
* command context.

The `message` is the domain model part of command. The type of the command is defined by
the type of its message. When we speak about a **command** as a typed thing, we refer to the message of the command.

The context contains attributes common for all commands.
A command message is a protobuf message:

``````java
message MyCommand {
    // The first field of an aggregate command must be the ID of the aggregate.
    MyAggregateId target_id = 1;
    string some_string = 2;
    uint32 some_int = 3;
}
``````
If a command is for an aggregate or a process manager, the first field must contain the ID of the aggregate or the process manager.

By convention command messages are defined in the file named`commands.proto`. Typically the file would reside in the protobuf package of an aggregate or a process manager.

There should be **one and only one** handler associated with the type of the command.

``````java
message Command {
    // The message of the command wrapped into `Any`.
    google.protobuf.Any message = 1;
    
    // Command context.
    spine.base.CommandContext context = 2;
}

``````

Meta-information about the command and the environment, which generated the command.

``````java
message CommandContext {
    // The id of the command.
    CommandId command_id = 1;

    // The user who created the command.
    UserId actor = 2;

    // Date/time at which the command was created.
    google.protobuf.Timestamp timestamp = 3;

    // The zone offset from which the command is made.
    time.ZoneOffset zone_offset = 4;

    // The `namespace` attribute must be defined for commands in multitenant applications.
    Namespace namespace = 5;
}
``````


