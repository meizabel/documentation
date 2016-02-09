# Writing Command Handlers


For the majority of commands, a handler would be corresponding aggregate root object. Such a method takes two parameters: 
* Message for command instance
* CommandContext for meta-information on the command. 

The method can have any name. We recommend call them handle:

```java
@Assign
public void handle(Message command, CommandContext ctx) {
   ...
}
```

To be dispatched to the aggregate root, the command must have an attribute with an ID of the aggregate. See Writing Aggregate Commands for details.

**Note:** the annotation `@Susbscribe` tells that the method participates in automatic dispatching of commands.

A command handler method can throw [business failures](/java/command_validation.md). This means the API of each command handler allows:

* Either produce an event (or a list of events). Or,
* It can throw one or more business failures (which are clearly visible in the method signature).

## Abstract Command Handlers
* Writes Status to Command Store
* Writes Events to Event Store
* Accepts Bounded Context in c'tor

TODO: describe implementing an interface.

## Registering Command Handlers

TODO: automatic registration of aggregate handlers by registering the corresponding repository. TODO: registering general command handlers with the engine.


