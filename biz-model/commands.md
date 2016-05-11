# Writing Commands

Commands, as well as Events and Aggregate State are defined as protobuf messages.
`Command` is an instruction to do something.

A command consists of two parts: 
* command message
* command context

The `message` is the domain model part of command. The type of the command is defined by
the type of its message. When we speak about a **command** as a typed thing, we refer to the message of the command.

A `CommandContext` is meta-information of the command. The context contains attributes common for all commands. For details of the `CommandContext` fields, please see the type declaration in `command.proto` in our [GitHub repo](https://github.com/SpineEventEngine/core-java/blob/8ddee17753fe27a2bb92ae96f2bf2f266b4da5a8/client/src/main/proto/spine/base/command.proto).

See a command example below:

``````protobuf
message MyCommand {
    // The first field of an aggregate command must be the ID of the aggregate.
    MyAggregateId target_id = 1;
    string some_string = 2;
    uint32 some_int = 3;
}
``````
If a command is for an aggregate or a process manager, the first field must contain the ID of the aggregate or the process manager.

By convention command messages are defined in the file named`commands.proto`. Typically the file would reside in the protobuf package of a corresponding aggregate or a process manager.

There should be **one and only one** handler associated with the type of the command.


# Command Validation
Spine supports an automatic command validation on a `Message` level. The validation uses custom [proto](https://github.com/SpineEventEngine/core-java/blob/5ae42af2a4035eab27dc92245d1b09d891f7cb5f/client/src/main/proto/spine/validation.proto) options. 

In case you need more sophisticated validation, it can be implemented manually for the objects that handle a command — [Process Manager](../java/process-manager.md) or [Aggregate](../java/aggregate.md) and so on.

To validate a command, define it in the `commands.proto` file. Basically, the file could have any name ending with “commands”(e.g. ordercommand.proto). 

With that, commands being posted to the Command Bus will be validated in accordance with custom options described in `Commandvalidation.proto`. 
More about validated attributes you can find [here](https://github.com/SpineEventEngine/core-java/wiki/Proposal-for-validation-attributes). 

на прото ленгвиж гайд тихочнечко. если не знают что такое есть.   


валидация эта может использоваться для ивентов и чего угодно. но пока только для команд в команд бас. 

Each command has some attributes that are *required* from the business logic stand point and  are not obligatory from the [protocol](https://developers.google.com/protocol-buffers/docs/proto#customoptions) stand point.

```protobuf
message MyCommand {
    // an ID in commands is checked anyway
    MyAggregateId id = 1  [(required).value = true];

    double number = 2 [(min).value = "16.5"];

    google.protobuf.Timestamp time = 3 [(when).in = FUTURE];
}
```
Note, you do not need to mark the first field in a command as required as it will be validated it anyway.

## Command Validator

