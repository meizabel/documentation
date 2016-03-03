# Event Bus

An Event Bus dispatches incoming events to handlers, and provides ways for registering those handlers. One event can be published to more than one subscriber.

### Registering Events
To receive events a handler object should:
 * Expose a public method that accepts the type of the event as the first parameter and EventContext as the second parameter;
 * Mark the method with `@Subscribe` annotation;
 * Register with an instance of EventBus using `#subscribe(EventHandler)`.
 
 **Note:** Since Protobuf messages are final classes, a handler method cannot accept just `Message` as the first parameter. It must be an exact type of the event that needs to be handled.
 
### Posting Events
Events are posted to an EventBus using `#post(Event)` method. Normally this is done by an [Aggregate Repository](./repository.md) in the process of handling a command, or by a [Process Manager](./process-manager.md).
 
 The passed [Event](../biz-model/events.md) is stored in the [Event Store](./event-store.md) associated with the Event Bus.
 **before**  it is passed to handlers.
 *
 * <p>The execution of handler methods is performed by an {@link Executor} associated with the instance of
 * the {@code EventBus}.
 *
 * <p>If a handler method throws an exception (which in general should be avoided), the exception is logged.
 * No other processing occurs.
 *
 * <p>If there is no handler for the posted event, the fact is logged as warning, with no further processing.
 *















It also allows a subscriber to catch-up from a given timestamp on a certain event.