# Immutability

An immutable object is one whose externally visible state cannot change after it is instantiated. 
Immutable objects greatly simplify your program, since they:

* are simple to construct, test, and use
* are automatically thread-safe and have no synchronization issues

In [Effective Java](http://www.amazon.com/exec/obidos/ASIN/0321356683/ref=nosim/javapractices-20), Joshua Bloch makes this compelling recommendation :
>Classes should be immutable unless there's a very good reason to make them mutable....If a class cannot be made immutable, limit its mutability as much as possible.

### Commands must be immutable.

### Events must be immutable.
Events that have happened are immutable. An event describes something that happened in the past and thus cannot be undone. Consequently the storage mechanism that we use to persist our events becomes very simple. It is basically a stack. We continuously append new events on top of the stack. Existing events are never touched again. No update or delete operation is defined, only add operations are ever possible.


### Isolation of storage and deployment aspects from the main code