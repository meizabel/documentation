# Event Bus

An Event Bus dispatches incoming events to [handlers](./event-handler.md), and provides ways for registering those handlers. One event can be published to more than one subscriber.

### Registering Events
To receive events a handler object should:
 * Expose a public method that accepts the type of the event as the first parameter and EventContext as the second parameter;
 * Mark the method with `@Subscribe` annotation;
 * Register with an instance of EventBus using `EventBus.subscribe(EventHandler)` method.
 
 **Note:** Since Protobuf messages are final classes, a handler method cannot accept just `Message` as the first parameter. It must be an exact type of the event that needs to be handled.
 
### Posting Events
Events are posted to an EventBus using `EventBus.post(Event)` method. Normally this is done by an [Aggregate Repository](./repository.md) in the process of handling a command, or by a [Process Manager Repository](./repository.md).

The passed [Event](../biz-model/event.md) is stored in the [Event Store](./event-store.md) associated with the Event Bus **before**  it is passed to handlers.

The execution of handler methods is performed by an `Executor` associated with the instance of the Event Bus.

If a handler method throws an exception which is not a Business Failure, the exception is logged.

If there is no handler for the posted event, the fact is logged as warning, with no further processing.

``````java
// Initialize Event Bus.
InMemoryStorageFactory storageFactory = InMemoryStorageFactory.getInstance();
EventStore eventStore = EventStore.newBuilder()
        .setStreamExecutor(MoreExecutors.directExecutor())
        .setStorage(storageFactory.createEventStorage())
        .setLogger(EventStore.log())
        .build();
EventBus eventBus = EventBus.newInstance(eventStore);

// Register event handlers (see `Event Handler` section on how to define them).
eventBus.subscribe(new MyEventSubscriber());

// Post an event.
MyEvent eventMessage = MyEvent.newBuilder().setSmth(smth).build();
Event event = Events.createEvent(eventMessage, eventContext);
eventBus.post(event);

``````

## Catch-up Subscription

An Event Bus also allows a subscriber to catch-up from a given timestamp on a certain event.

`TODO: code sample`