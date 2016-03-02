# Event Handler

Event Handler is a method that reacts on a domain event after it's posted to the Event Bus. Unlike [event appliers](/java/aggregate.md), event handlers must be declared public:

``````java
@Subscribe
public void on(MyEvent event) {
    // do something
}
``````
An event handler method must have two parameters. The class of the event will be indicated by the first parameter.

The second parameter must be EventContext. If the annotation
 * is applied to a method with less or more than two parameters, the method will not be
 * registered for event delivery from {@link EventBus}.