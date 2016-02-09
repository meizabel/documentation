# Prior Art

The demands on software projects increase rapidly as time progresses. So do architecture approaches to meet these needs. 
This section will give you an overview of the concepts and implementations Spine has inherited, while brought some important differences into play.


Spine is created for applications that follow[(CQRS)](http://martinfowler.com/bliki/CQRS.html) architectural pattern and [Event Sourcing](http://martinfowler.com/eaaDev/EventSourcing.html). 

Spine didn’t appear out of the blue, when the authors of the framework had nothing better to do. It is the result of observation of problems in real applications, and the experience from previous attempts to address or correct these problems, that has led to the Spine vision.

Major addition to the existent variety of tools, libraries and frameworks that Spine brings — is automatic code generation for multiple application clients. It is reached by using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview).

When creating an Event Sourcing application, you need to write classes for commands, events, command handlers, aggregates, aggregates repository, DTOs etc. 
And if your organization wants an application on, let's say a couple of mobile platforms, you would have to add a lot of work to deliver data to each client application. 
So you need to make your code work on another platform by writing it in another language manually, or translate it using tools like [J2ObjC](http://j2objc.org/), or we resort to using just Json in client apps.

Using [Protobuf](https://developers.google.com/protocol-buffers/docs/overview) for formulating business domain allows us
 to make this language [ubiquitous](http://martinfowler.com/bliki/UbiquitousLanguage.html) not only in human interaction, but in communication of computing devices too.
 
Immutability is another major concept we follow. 
Spine uses typed commands and events. Having commands and events as first class citizens in the applications gives a lot of benefits in business logic. Not having to convert back-and-forth with Json gives some performance advantage at the same time.

 Spine Event Engine synthesizes all of our experience and observations of the best-breed market products and solutions like [Axon](http://www.axonframework.org/), [Spring](https://spring.io/), [Event Store](https://geteventstore.com/), [InfluxDB](https://influxdata.com/), [Apache Zest](https://zest.apache.org/) and many others.
 
 Spine won't be a best fit for the trading or super highload solutions, where, for example, [LMAX](https://www.lmax.com/) does excellent job. Our motivation is to make modern applications development easier and more efficient, and to offer a set of practical solutions to bring this into life with accompanying approach and terminology. 

In terminology we heavily lean on Domain-Driven Design(DDD) [“Big Blue Book”](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)by Eric Evans, while borrowing some elements like “Process Manager” from [CQRS Jorney](https://msdn.microsoft.com/en-us/library/jj554200.aspx) by Microsoft. 








 


