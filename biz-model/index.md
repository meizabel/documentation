# Creating Business Model

Creating a business model is not something you can do very quickly. In fact, Domain Modeling is an iterative process, and the model itself will constantly evolve and require refactoring. 


The command handler retrieves domain objects (Aggregates) from a repository and executes methods on them to change their state. These aggregates typically contain the actual business logic and are therefore responsible for guarding their own invariants. The state changes of aggregates result in the generation of Domain Events. 

Spine provides supporting classes to help you build a domain model. 

* Defining commands, events, aggregate and projection states in protobuf.


This chapter will guide you through the major building blocks creation. 