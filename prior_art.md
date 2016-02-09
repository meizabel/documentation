# Prior Art

The demands on software projects increase rapidly as time progresses. So do architecture approaches to meet these needs. 
This section will give you an overview of the concepts and implementations Spine has inherited, while brought some important differences into play.

<<<<<<< HEAD

Spine is created for applications that follow [(CQRS)](http://martinfowler.com/bliki/CQRS.html) architectural pattern and [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html). 

Spine didn’t appear out of the blue, when the authors of the framework had nothing better to do. It is the result of observation of boilerplate code in real applications, and the experience from previous attempts to address this issue, that has led to the Spine vision.

Major addition to the existent variety of tools, libraries and frameworks that Spine brings — is automatic **code generation** for multiple application clients. It is reached by using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview).

When creating an Event Sourcing application, you need to write classes for commands, events, command handlers, aggregates, aggregates repository, DTOs etc. 
And if your organization wants an application on, let's say a couple of mobile platforms, you would have to add a lot of work to deliver data to each client application. 
So you need to make your code work on another platform by writing it in another language *manually*, or translate it using tools like [J2ObjC](http://j2objc.org/), or resort to using just Json in client apps.

Using [Protobuf](https://developers.google.com/protocol-buffers/docs/overview) for formulating business domain allows us
 to make this language [ubiquitous](http://martinfowler.com/bliki/UbiquitousLanguage.html) not only in human interaction, but in communication of computing devices too.
=======
While creating Spine Event Engine we followed steps of [(CQRS)](http://martinfowler.com/bliki/CQRS.html) architectural pattern and [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html). 

We were inspired by major frameworks on the market like [Axon](http://www.axonframework.org/) and [Event Store](https://geteventstore.com/). 
The important difference though is that we decided not to use JSON Objects for data transmission. This allows to avoid additional transformation and thus has event better performance. 

Using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview) allows automatic code generation for events and commands on variety of platforms.

Currently to transform code from one language to another you have to use translators, or back-and-force with JSON. We also want to make a ubiqutous language ubiquites in technical
>>>>>>> master
 
**Immutability** is another major concept we follow. 
Spine uses typed commands and events. Having commands and events as first class citizens in the applications gives a lot of benefits in business logic. Not having to convert back-and-forth with Json gives some performance advantage at the same time.

 Spine Event Engine synthesizes all of our experience and observations of the best-breed market products and solutions like [Axon](http://www.axonframework.org/), [Spring](https://spring.io/), [Event Store](https://geteventstore.com/), [InfluxDB](https://influxdata.com/), [Apache Zest](https://zest.apache.org/) and many others. Yet, trying to find it's own niche.
 
 Spine won't be a best fit for the trading or highly loaded applications, where, for example, [LMAX](https://www.lmax.com/) does excellent job. Our motivation is to make modern applications development easier and more efficient, and to offer a set of practical solutions to bring this into life with accompanying approach and terminology. 

In terminology we heavily lean on Domain-Driven Design(DDD) [“Big Blue Book”](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)by Eric Evans, while combining some elements like “Process Manager” from [CQRS Jorney](https://msdn.microsoft.com/en-us/library/jj554200.aspx) by Microsoft and adding our own, like [“Aggregate Stand”](concepts.md).

We are yet at the beginning of our journey using Spine in the wild. Join us and share how it goes!




The contributors to this document have been directly involved in the development and deployment of hundreds of apps, and indirectly witnessed the development, operation, and scaling of hundreds of thousands of apps via our work on the Heroku platform.

This document synthesizes all of our experience and observations on a wide variety of software-as-a-service apps in the wild. It is a triangulation on ideal practices for app development, paying particular attention to the dynamics of the organic growth of an app over time, the dynamics of collaboration between developers working on the app’s codebase, and avoiding the cost of software erosion.

<<<<<<< HEAD
 


=======
Our motivation is to raise awareness of some systemic problems we’ve seen in modern application development, to provide a shared vocabulary for discussing those problems, and to offer a set of broad conceptual solutions to those problems with accompanying terminology. The format is inspired by Martin Fowler’s books Patterns of Enterprise Application Architecture and Refactoring.
>>>>>>> master
