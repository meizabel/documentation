# Essentials

In this chapter we will highlight some key concepts we follow and important building blocks we use in the framework.

We started working on Spine after two CQRS/ES projects. Having the experience
of:
- tons of manual work for creating commands, events, etc.
- delivering events and data to web and mobile clients.
- 

...



We decided to create a framework that can help us and development groups like us to build CQRS/ES apps easier.

* In Spine Event Engine a Domain Model, including commands, events and aggregates, Projections and Business Failures, is described using [Protocol Buffers](essentials/principles.md).
* Events and Commands are [ strongly typed](essentials/strongly-typed.md).
* Ubiquitous language is [ubiquitous](/essentials/ubiquitous-language.md) across human communications and computing devices interactions.
* [Bounded Context](/essentials/bounded-context.md) is important.
