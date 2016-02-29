# Creating Business Model

Creating a business model is not something you can do very quickly. In fact, the Domain Modeling is an iterative process, and the model itself will constantly evolve and require refactoring. Scared already? — Don’t be! With protobufs, this process can greatly level down the complexity. 

Similarly to what we done as a part of the [“Hello Spine!”](../getting-started/index.md) example, developing your application on top of the Spine framework will include the following stages:
* Defining commands, events, aggregate and projection states in protobuf.
* Defining business logic of aggregates and projections.
* Creating repositories.
* Initiating Bounded Context with repositories and Storage Factory.
* Creating Application class and executing it.

This chapter will guide you through the major building blocks creation. 