# Motivation

We started working on Spine after two CQRS/ES projects. Having the experience
of tons of manual work for:
- creating commands, events, etc.
- delivering events and data to web and mobile clients.

Being a team that strives for efficiency in each product we create, implementing a great deal of cutting edge technologies to make development process easier and more productive, we could not just accept it.
Instead, we decided to create a framework that can help us and development groups like us to build CQRS/ES apps easier.


There are four fundamental principles Spine is based on:
* Events and Commands should be [strongly typed](../motivation/strongly-typed.md). 
* Ubiquitous language must be really [ubiquitous](../motivation/ubiquitous-language.md).
* [Bounded Context](../motivation/bounded-context.md) definition is a key to successful architecture.
* Classes must be [immutable](../motivation/immutability.md) unless there is a
good reason not to do so.

To get in depth understanding of these principles read the articles in this chapter.

---
When you are ready to dig into further details, check  Architecture and Domain Model [Concepts](../concepts.md) to find out what is lying in the Spine’s foundation.