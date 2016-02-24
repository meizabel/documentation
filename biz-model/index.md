# Creating Business Model

Creating a business model is not something you can do very quickly.  In fact the Domain Model will constantly evolve and require refactoring. 

Similarly to what we done as a part of very simple [“Hello Spine!”](/getting-started/index.md) example, your application development on top of Spine framework will consist of the following stages:
* Define commands, events, aggregate and projection states in protobuf.
* Define business logic of aggregates and projections.
* Create repositories.
* Init Bounded Context with repositories and Storage Factory.
* Create Application class and execute.