# Command Bus

A Command Bus routs the incoming commands to the corresponding handler.  Unlike a [Command Handler](./command-handler.md) it does not change business model or produce events.


The command can be posted if it has either dispatcher or handler registered with the command bus.
The method intended to be used with the instances of command messages extracted from [Command](../java/command.md).
     *
     * <p>If {@code Command} instance is passed, its message is extracted and validated.
     *