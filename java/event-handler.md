# Event Handler

Event Handler is a method that reacts on a domain event after it is posted to the Event Bus. Unlike [Event Appliers](/aggregate.md), event handlers must be declared public:

``````java
@Subscribe
public void on(MyEvent event, EventContext context) {
    // do something
}
``````
A handler method must be annotated with [@Subscribe](https://github.com/SpineEventEngine/core-java/blob/dc073660ee72af118f036fcb2768e511223908d7/server/src/main/java/org/spine3/server/Subscribe.java).

It must have two parameters. The class of the event will be indicated by the first parameter.

The second parameter must be an event context — the meta-information on the event. 

If the annotation is applied to a method with less or more than two parameters, the method will not be registered for event delivery from [EventBus](./event-bus.md).

