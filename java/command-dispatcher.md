# Command Dispatcher

Command Dispatcher delivers commands to their [handlers](./command-handler.md) invoking a corresponding handler method for the received command.  

A dispatcher can deliver more than one class of commands.

Unlike a [Command Handler](./command-handler.md) the dispatcher does not change the state of the business model, neither it produces events.

The dispatcher should be registered within the [Command Bus](./command-bus.md) to route the corresponding type of commands. 

``````java
// Initialize Command Bus.
InMemoryStorageFactory storageFactory = InMemoryStorageFactory.getInstance();
CommandStorage commandStorage = storageFactory.createCommandStorage();
CommandBus commandBus = CommandBus.create(new CommandStore(commandStorage));

// Register an aggregate repository which dispatches commands to aggregates (command handlers).
commandBus.register(new OrderAggregateRepository());

// Post a command to Order aggregates.
DoSmth commandMessage = DoSmth.newBuilder().setSmth(smth).build();
Command command = Commands.create(commandMessage, commandContext);
commandBus.post(command);
```