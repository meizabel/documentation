# Command Bus

A Command Bus routes incoming commands to corresponding handlers. Unlike a [Command Handler](./command-handler.md) it does not change a business model or produce events.

The command can be posted if it has **either** [dispatcher](./command-dispatcher.md) **or** handler registered with the Command Bus.

**Note:** If the passed dispatcher deals with commands, for which another dispatcher is already registered, the dispatch entries for such commands will not be unregistered, and warning will be logged.

``````java
CommandStorage commandStorage = InMemoryStorageFactory.getInstance().createCommandStorage();
CommandBus commandBus = CommandBus.create(new CommandStore(commandStorage));
``````