## Defining an Aggregate

In domain-driven design (DDD), an aggregate defines a consistency boundary. External references are restricted to one member of the AGGREGATE, designated as the root. A set of consistency rules applies within the AGGREGATE’S boundaries.

Typically, when you implement the CQRS pattern, the classes in the write model define your aggregates. Aggregates are the recipients of commands, and are units of persistence. After an aggregate instance has processed a command and its state has changed, the system must persist the new state of the instance to storage.

In Spine **aggregate state** is defined in a protobuf message, while aggregate itself is a java class. 


