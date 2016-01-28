# Frequently Asked

 
### Why framework is called Spine?
 We want to be a framework that provides an infrastructure and connects so to say “service” parts of applications with their “brains” — business logic. 
 Find out how following [leading industry trends](/docs/guides/priorart.html) we were [inspired](/docs/guides/motivation.html) to create Spine. 

### Why Java 7?
The code of the framework is based on Java 7. Why not on Java 8, with Java 9 around the corner?

One of our implementations is for Google Cloud Platform. Google App Engine requires Java 7. Google recently announced [Java8](https://youtu.be/aKUlu9-psZo?t=15m30s)

This means Google is going to support it in the Sandbox mode (it is available under Managed VMs now). So we are going to migrate to Java 8 once it is available under App Engine.

### Why Protobuf
Have a look the comparison matrix created by the author of Protobuf v2 and the author of Cap'n Proto. The main features that make protobuf best choice for Spine are:
— Schema evolution — we need this as business models evolve as business grows.
— Usable as mutable state — we need this for transforming Aggregate States and Stream Projections.
— Other languages — we need support for client applications written on JavaScript, Objective-C, Swift, Java nano (for Android), etc.

