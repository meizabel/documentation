# Immutability

Classes must be made immutable unless there’s a
reason not to make them. Even if they need to be made mutable, it must be
limited as much as possible.`

In [Effective Java](http://www.amazon.com/exec/obidos/ASIN/0321356683/ref=nosim/javapractices-20), Joshua Bloch makes this compelling recommendation :
"Classes should be immutable unless there's a very good reason to make them mutable....If a class cannot be made immutable, limit its mutability as much as possible."

### Commands must be immutable.

### Events must be immutable.

### Isolation of storage and deployment aspects from the main code