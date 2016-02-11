## Defining an Aggregate

As [DDD Glossary](http://dddcommunity.org/resources/ddd_terms/) suggests, an Aggregate is a cluster of associated objects that are treated as a unit for the purpose of data changes. External references are restricted to one member of the AGGREGATE, designated as the root. A set of consistency rules applies within the AGGREGATE’S boundaries.

Aggregate handles commands, applies events, and have a state model encapsulated within it that allows it to implement the required command validation, thus upholding the invariants (business rules) of the aggregate.

In Spine aggregate state is defined in a protobuf message. 

