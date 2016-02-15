# Bounded Context

Bounded Context is the delimited applicability of a particular model. BOUNDING CONTEXTS gives team members a clear and shared understanding of what has to be consistent and what can develop independently

As [DDD book](https://www.wikiwand.com/en/Domain-driven_design) advises:
```
“Explicitly define the context within which a model applies. Explicitly set boundaries in terms of team organization, usage
within specific parts of the application, and physical manifestations such as code bases and database schemas.
Keep the model strictly consistent within these bounds, but don’t be distracted or confused by issues outside.”

```
Smaller models provide many benefits, allowing teams to define clear boundaries relating to design and development responsibilities. They also lead to better maintainability — because a context has a smaller surface area, you have fewer side effects to worry about when making modifications.


## Interaction between Bounded Contexts
Bounded contexts are autonomous components, with their own domain models and their own ubiquitous language. They should not have any dependencies on each other at run time and should be capable of running in isolation. However they are a part of the same overall system and do need to exchange data with one another. If you are implementing the CQRS pattern in a bounded context, you should use **Integration events** `TODO: link to the spine documentation article` for this type of communication.

Integration Events have the same nature as events within the bounded context.  They are one-way, asynchronous messages that publish information about something that has already happened. 

Your bounded context can respond to events that are raised outside of the bounded context, and your bounded context can publish events that other bounded contexts may subscribe to. This enables you to maintain the loose coupling between your bounded contexts.
