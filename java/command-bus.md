# Command Bus

A Command Bus routes the incoming commands to the corresponding handler.  Unlike a [Command Handler](./command-handler.md) it does not change business model or produce events.

The command can be posted if it has **either** [dispatcher](./command-dispatcher.md) **or** handler registered with the Command Bus.

**Note:** If the passed dispatcher deals with commands for which another dispatcher already registered the dispatch entries for such commands will not be unregistered, and warning will be logged.

`TODO:Code sample` 