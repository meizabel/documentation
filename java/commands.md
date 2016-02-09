# Writing Commands

Commands, as well as Events and Aggregate State are defined as protobuf messages
`Command` is an instruction to do something.

A command consists of two parts: command message and command context.

The `message` is the domain model part of command. The type of the command is defined by
the type of its message. When we speak about a *command* as a typed thing, we refer to the message of the command.

The context contains attributes common for all commands.
A command can hold any valid Protobuf message, but in most cases, it would be a type defined in `commands.proto` file of the corresponding aggregate or process manager.
There should be **one and only one** command handler associated with the type of the command.

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
message CommandContext {The id of the command.
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

<a name = "commandcontext"></a>
``````


<a name="bizfailure"></a>
### Business Failure 
 In Spine system errors are separated from business logic failures that can be fixed by user (e.g. not enough money on credit card). 
 Below you can see a sample of the aggregate that throws a business failure on a command, which cannot be performed.
<pre>
@Assign
public TaskCancelled handle(CancelTask command, CommandContext context) throws CannotCancelTaskInProgress {
    final Task task = getState();
    if (task.getStatus() == Task.Status.IN_PROGRESS) {
            throw new CannotCancelTaskInProgress(task.getId());
        }

       return TaskCancelled.newBuilder().setId(task.getId()).build();
    }
</pre>