# Command Bus

A Command Bus routs the incoming commands to the corresponding handler instantiating the required objects.  Unlike a [Command Handler](./command-handler.md) it does not change business model or produce events.

The command can be posted if it has either [dispatcher](./command-dispatcher.md) or handler registered with the command bus.
`TODO:Code sample` 