# Event Handler

Event Handler is a method that reacts on a domain event after it's posted to the Event Bus. Unlike [event appliers](/java/aggregate.md), event handlers must be declared public:

``````java
@Subscribe
public void on(MyEvent event) {
    // do something
}
``````