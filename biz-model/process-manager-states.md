# Process Manager State

A [Process Manager](../java/process-manager.md) is defined as a Java class. It serves as a centralized processing unit that maintains the state sequence and defines the next processing step based on intermediate results.

A **Process Manager State** reflects a state of a business process. It is a data structure which is defined as a protobuf message.
The process manager state is *typed*.

The Process Manager State consists of the: [Identifier](./identifiers.md), constants describing its states and additional info it may need for processing steps, like Aggregate IDs etc.

An identifier type should be already set by the time of creating a process manager state. We recommend to have [typed](../motivation/strongly-typed.md) identifiers.

A `Message`-based ID, typically, would reside in the protobuf package of a process manager.

```protobuf
message RegistrationProcess {

    ProcessManagerId id = 1;

    State process_state = 2;

    OrderId order_id = 3;

    enum State {
        NOT_STARTED = 0;
        AWAITING_RESERVATION_CONFIRMATION = 1;
        RESERVATION_CONFIRMED = 2;
        PAYMENT_RECEIVED = 3;
    }
}

message ProcessManagerId {
    string uuid = 1;
}
```