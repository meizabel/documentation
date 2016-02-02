# Spine Event Engine Concepts

<p class="lead"> This document introduces some key Spine architecture concepts.</p> It assumes that you've read the [Introduction](README.md). For language-specific details, see the [Getting Started](/Getting Started/README.md).
The Diagram below represents architecture of the application build using Spine.

![Spine Event Engine Diagram](Diagram-SpineEventEngine.svg)


Spine provides realization for most important building blocks of the CQRS oriented application.


**Command** is an instruction to do something. Commands are messages that instruct a specific entity to perform a certain action.They are named with a verb in the imperative mood plus and may include the aggregate type. Unlike an event, a command is not a statement of fact; it's only a request, and thus may be refused. (A typical way to convey refusal is to throw an exception).In Spine [command](/java) is defined as a protobuf message. 

**Event** is something that happened in the past.
Capture all changes to an application state as a sequence of events. In Spine events are defined as protobuf messages. Find out more about [Writing an Event] .

**Aggregate** handles commands, applies events, and have a state model encapsulated within it that allows it to implement the required command validation, thus upholding the invariants (business rules) of the aggregate.
Read more on declaring an [Aggregate](/java/aggregate.md)) in Spine.

**Aggregate Repository** manages Aggregates, sends events to Event Bus and latest Aggregate States to the Aggregate Stand.

**Command Bus**

**Command Handler**

**Command Store**


**Event Bus**

**Process Manager**

**Process Manager Repository** manages Process Manager ???


  

**Stream Projection**  - Stream Projection. 
