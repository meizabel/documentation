# Prior Art

The demands on software projects increase rapidly as time progresses. So do architecture approaches to meet these needs. 
This section will give you an overview of the concepts and implementations Spine has inherited, while brought some important differences into play.

Spine didn’t appear out of the blue, when the authors of the framework had nothing better to do. It is the result of observation of problems in real applications, and the experience from previous attempts to address or correct these problems, that has led to the Spine vision.

Major addition to the existent variety of tools, libraries and frameworks that Spine brings — is automatic code generation for multiple application clients. It is reached by using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview), which allow automatic code generation for events and commands on variety of platforms.

Spine is created for applications that follow[(CQRS)](http://martinfowler.com/bliki/CQRS.html) architectural pattern and [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html). 


This document synthesizes all of our experience and observations on a wide variety of software-as-a-service apps.
We were inspired by major frameworks on the market like [Axon](http://www.axonframework.org/) and 

[Event Store](https://geteventstore.com/). 
The important difference though is that we decided not to use JSON Objects for data transmission. This allows to avoid additional transformation and thus has even better performance. 



Currently to transform code from one language to another you have to use translators, or back-and-force with JSON. We also want to make a ubiqutous language ubiquites in technical
 
Immutability is one of the corner concepts used in Spine. 

Spine uses typed commands and events. JSON is nice, but having commands and events as first class citizens in the applications gives a lot of benefits in business logic. Not having to convert back-and-forth with Json gives some performance advantage.








---

The contributors to this document have been directly involved in the development and deployment of hundreds of apps, and indirectly witnessed the development, operation, and scaling of  apps via our work on .

 
Our motivation is to raise awareness of some systemic problems we’ve seen in modern application development, to provide a shared vocabulary for discussing those problems, and to offer a set of practical solutions to those problems with accompanying terminology. 

is inspired by Martin Fowler’s books Patterns of Enterprise Application Architecture and Refactoring.
