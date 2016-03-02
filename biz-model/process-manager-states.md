# Process Manager State

A **Process Manager** is defined as [Java class](../java/process-manager.md). It serves as a centralized processing unit that maintains the state sequence and defines the next processing step based on intermediate results.

A **Process Manager State** is a data structure and is defined as a protobuf message.
The process manager state is *typed*.

The Process Manager State consists of the: [Identifier](./identifiers.md), constants describing its states and additional info it may need for processing steps, like Aggregate IDs etc.

An identifier type should be already set by the time of creating a process manager state. We recommend to have [typed](../motivation/strongly-typed.md) identifiers.

A `Message`-based ID, typically, would reside in the protobuf package of a process manager.