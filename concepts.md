# Spine Event Engine Concepts

<p class="lead"> This document introduces some key Spine architecture concepts.</p> It assumes that you've read the [Introduction](README.md). For language-specific details, see the [Getting Started](/Getting Started/README.md).
The Diagram below represents architecture of the application build using Spine.

![Spine Event Engine Diagram](Diagram-SpineEventEngine.svg)


Spine provides realization for most important building blocks of the CQRS oriented application.


**Command** is an instruction to do something. 
Command focuses on what the user considers as an operation. In Spine [command](/java) is defined as a protobuf message. 

**Event** is something that happened in the past.
Capture all changes to an application state as a sequence of events. In Spine events are defined as prorobuf messages. Find out more about [Writing an Event] .

**Aggregate** is a pattern in Domain-Driven Design. According to  [Martin Fowler](http://martinfowler.com/bliki/DDD_Aggregate.html), a DDD aggregate is a cluster of domain objects that can be treated as a single unit. 

Specifically, an aggregate will handle commands, apply events, and have a state model encapsulated within it that allows it to implement the required command validation, thus upholding the invariants (business rules) of the aggregate.
Read more on declaring an [Aggregate](/java/aggregate.md)) in Spine.

**Aggregate State** - each aggregate has a state, which represents Aggregate structure. Aggregate State is defined as protobuf message in Spine. 

**Stream Projection**  - Stream Projection is a subset of Events from the Events Stream. 

**Projection** — (here we use traditional term from Relational Algebra) is subset of columns for use in operations, i.e. a projection is the list of columns selected.
Read more about [Projection](/docs/tutorials/basic/java.html) usage in Spine.

**Process Manager**  


