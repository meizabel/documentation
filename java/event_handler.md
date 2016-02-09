# Event Handler

<a name="eventapplier"></a>
### Event Applier
Event applier is a method of an aggregate root which applies data from an event to the state of the aggregate.

Event appliers are part of the private API of aggregate roots. As such they are declared private by convention set in the Spine framework:

``````java
 @Apply
 private void on(MyEvent event) {
     MyState newState = getState().toBuilder()
       .setMyProperty(event.getProperty())
       .build();
     validate(newState);
     setState(newState);
 }
``````

### Event Handler
Event Handler is a method which reacts on a domain event after it's posted to the Event Bus. Unlike [event appliers](#eventapplier), event handlers must be declared public:

``````java
@Subscribe
public void on(MyEvent event) {
    // do something
}
``````