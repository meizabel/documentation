# Command Bus

A Command Bus routes incoming commands to corresponding handlers. Unlike a [Command Handler](./command-handler.md) it does not change a business model or produce events.

### Posting Commands
Commands are posted to the Command Bus using `CommandBus.post(Command)` method.

The passed [Command](../biz-model/command.md) is stored in the [Command Store](./command-store.md) associated with the Command Bus **before** it is passed to handlers.

If there is no handler for the posted command, an exception is thrown.

The command can be posted if it has **either** [dispatcher](./command-dispatcher.md) **or** handler registered with the Command Bus.

**Note:** If the passed dispatcher deals with commands, for which another dispatcher is already registered, the dispatch entries for such commands will not be unregistered, and warning will be logged.


``````java
// Initialize Command Bus.
InMemoryStorageFactory storageFactory = InMemoryStorageFactory.getInstance();
CommandStorage commandStorage = storageFactory.createCommandStorage();
CommandBus commandBus = CommandBus.create(new CommandStore(commandStorage));

// Register a command handler (see `Command Handler` section on how to define it).
commandBus.register(new MyCommandHandler());

// Post a command.
DoSmth commandMessage = DoSmth.newBuilder().setSmth(smth).build();
Command command = Commands.create(commandMessage, commandContext);
commandBus.post(command);

``````