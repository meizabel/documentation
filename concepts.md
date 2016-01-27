# Spine Event Engine Concepts

<p class="lead"> This document introduces some key Spine architecture concepts and terms usage specifics.</p> It assumes that you've read the [Overview](/docs/index.html). For language-specific details, see the [Quick Start](/docs/guides/start), [tutorial](/docs/tutorials/basic/java.html), and reference documentation for your chosen language(s).

![Spine Event Engine Diargram](Grey-Blue-SpineEventEngine.svg)

**Command** is an instruction to do something. 
Command is any method that mutates state. In Spine [command](/docs/tutorials/basic/java.html) is as protobuf message. 

**Event** is something that happened in the past.
Capture all changes to an application state as a sequence of events. In Spine events are defined as prorobuf messages. Find out more about [Writing an Event](/docs/tutorials/basic/java.html).

**Aggregate** is a pattern in Domain-Driven Design. According to  [Martin Fowler](http://martinfowler.com/bliki/DDD_Aggregate.html), a DDD aggregate is a cluster of domain objects that can be treated as a single unit. 

Specifically, an aggregate will handle commands, apply events, and have a state model encapsulated within it that allows it to implement the required command validation, thus upholding the invariants (business rules) of the aggregate.
Read more on [Aggregate definition](/docs/tutorials/basic/java.html) in Spine.

**Aggregate State** - each aggregate has a state, which represents Aggregate structure. Aggregate State is defined as protobuf message in Spine. 

**Stream Projection**  - Stream Projection is a subset of Events from the Events Stream. 

**Projection** — (here we use traditional term from Relational Algebra) is subset of columns for use in operations, i.e. a projection is the list of columns selected.
Read more about [Projection](/docs/tutorials/basic/java.html) usage in Spine.

**Process Manager**  


