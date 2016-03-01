# Creating a Business Model

Domain Modeling is an iterative process, and the model itself will constantly evolve and require refactoring. 

### Persistence Ignorance
The Domain Model models real-life problems and solutions, it models **behavior**. It knows nothing about the database

You need to identify what are the items (objects) you need to accomplish the desired functionalities of your application. You need to identify the relationships among different objects and how they interact among themselves. You need to find if the business goal of your application is achievable using your domain model. 
You do not need to know how and where the data of your domain will persist or even if the data do need to persist while you do the model of the domain.

This ignorance about your persistence medium will make your domain model free from any coupling with the persistence layer of the application. 

In result your application will be free from coupling with any data store and will be very easily unit testable.
 All it will know is the [“Repository”](../data-storage/index.md) which will eventually manage your application’s persistence concern.


------

The command handler retrieves domain objects (Aggregates) from a repository and executes methods on them to change their state. These aggregates typically contain the actual business logic and are therefore responsible for guarding their own invariants. The state changes of aggregates result in the generation of Domain Events

Spine provides supporting classes to help you build a domain model. So to create a Business Model with Spine you need to define:
commands, events, aggregate and projection states as protobuf messages.


This chapter will guide you through the major building blocks creation. 