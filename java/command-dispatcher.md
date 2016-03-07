# Command Dispatcher

Command Dispatcher invokes a handler method for the received command. 
A dispatcher can deliver more than one class of commands.

Unlike a [Command Handler](./command-handler.md) the dispatcher does not change the state of the business model, neither it produces events.

The dispatcher should be registered within the [Command Bus](./command-bus.md) to route the corresponding type of commands. 

`TO DO: Code Sample`