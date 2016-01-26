### Writing Command Handlers

For the majority of commands, a handler would be corresponding aggregate root object. Such a method takes two parameters: <code>Message</code> for command instance and <code>CommandContext</code> for meta-information on the command. The method can have any name. We recommend call them <code>handle</code>:

<pre>
@Assign
public void handle(Message command, CommandContext ctx) {
   ...
}
</pre>

To be dispatched to the aggregate root, the command must have an attribute with an ID of the aggregate. See Writing Aggregate Commands for details.

Notice the annotation @Susbscribe, which tells that the method participates in automatic dispatching of commands.