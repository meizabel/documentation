# Strongly Typed

We believe that domain language, being the most important part of the
application, must be strongly [typed](http://martinfowler.com/ieeeSoftware/whenType.pdf).

Unlike some of  CQRS/ES frameworks that treat commands and events as Json objects, Spine promotes commands and events to be first class citizens in the applications, which gives a lot of benefits in business logic. Defining events and commands as classes, and not having to convert back-and-forth with Json gives some performance advantage at the same time.

  The model [can be extended](https://developers.google.com/protocol-buffers/docs/proto3#updating) without breaking binary compatibility with client applications.
  
A general heuristic is that value objects should be entirely immutable. If you want to change a value object you should replace the object with a new one and not be allowed to update the values of the value object itself - updatable value objects lead to aliasing problems.
TODO: link to TinyTypes. Quote Fowler on typed value objects (http://martinfowler.com/bliki/ValueObject.html).


Identifiers must be typed too. The framework does allow to have IDs of type
`String`, `Long`, or `Integer`.
But we recommend to have typed identifiers. So if you have the
`Order` class for one of your aggregates, there should be an `OrderId`.

There are two benefits of this:
1. **Strong typing eliminates errors** related to passing wrong value by mistake.
Suppose you have a command like this:
```java
    CreateOrder cmd = CreateOrder.newBuilder()
                                 .setId(orderId)
                                 .setCustomerId(customerId)
                                 .setCostCenter(costCenterId)
                                 .setDepartmentId(departmntId)
                                 .setNotes(notes)
                                 .build();
```
It’s easy to pass a wrong ID if it’s a string. With typed identifiers, your
IDE (and compiler) would point the error.

2. **Identifiers can be extended as business grows**
Imagine, you have customer IDs that are auto-generated and are `long`.
Then you decide to integrate with another system in which customer IDs
are based on email addresses, and with another system in which customer IDs are
phone numbers. Having `CustomerId` class in the first place would make the
integration much easier.