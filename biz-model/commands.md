# Writing Commands

Commands, as well as Events and Aggregate State are defined as protobuf messages.
`Command` is an instruction to do something.

A command consists of two parts: 
* command message
* command context

The `message` is the domain model part of command. The type of the command is defined by
the type of its message. When we speak about a **command** as a typed thing, we refer to the message of the command.

A `CommandContext` is meta-information of the command. The context contains attributes common for all commands. For details of the `CommandContext` fields, please see the type declaration in `command.proto` in our [GitHub repo](https://github.com/SpineEventEngine/core-java/blob/8ddee17753fe27a2bb92ae96f2bf2f266b4da5a8/client/src/main/proto/spine/base/command.proto).

A command message is a protobuf message:

``````protobuf
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


# Command Validation

Each command has additional attributes that are *required* from the business logic stand point and  are not obligatory from the [protocol](https://developers.google.com/protocol-buffers/docs/proto#customoptions) stand point.

Spine  supports an automatic command validation on a `Message` level. In case you need more sophisticated validation, it can be implemented manually for the objects that handle a command — [Process Manager](../java/process-manager.md) or [Aggregate](../java/aggregate.md) and so on.
## Command Validator

