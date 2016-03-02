# Creating a Business Model

Domain Modeling is an iterative process, and the model itself will constantly evolve and require refactoring. 

### Persistence Ignorance
The Domain Model models real-life problems and solutions, it models **behavior**. That’s the core of an application and should  mimic the real situations the best it can.

You need to identify what are the items (objects) you need to accomplish the desired functionalities of your application. You need to identify the relationships among different objects and how they interact among themselves. You need to find if the business goal of your application is achievable using your domain model. 

You do not need to know how and where the data of your domain will persist while you do the model of the domain. So, Domain Model **knows nothing** about the database.

This ignorance makes your domain model free from any coupling with the persistence layer of the application. In result your application will be free from coupling with any data store and will be very easily unit testable.
All it will know is the [“Repository”](../java/repository.md.md) which will eventually manage your application’s persistence concern.


### Domain Model blocks 
If you already checked [Concepts](../concepts.md) chapter, you are aware of the major Domain model building blocks and that Spine provides you with classes to support domain model creation. 
To build a Business Model you need to define *commands, events, aggregate and projection states* as protobuf messages.

This chapter will guide you through the major building blocks creation. 