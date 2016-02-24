# Ubiquitous Language

Ubiquitous language — a language structured around the domain model and used by all team members to connect all the activities of the team with the software.

In Spine Event Engine a Domain Model, including commands, events and aggregates, projections and business failures, is described using Protocol Buffers.

##Cross-platform compatibility
Using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview) allows automatic code generation for events and commands on the variety of platforms hugely saving development team effort.

By default Spine Event Engine uses *Protocol Buffers*, Google’s mature open source mechanism for serializing structured data. You can find out lots more about Protocol Buffers in the [Protocol Buffers documentation](https://developers.google.com/protocol-buffers/docs/overview).

#### Protocol Buffer versions

While Protocol Buffers have been available for open source users for some time, Spine uses a new flavor of Protocol Buffers called proto3, which has a slightly simplified syntax, some useful new features, and supports more languages. This is currently available as an beta release in Java and C++, with an alpha release for JavaNano (Android Java), Python, and Ruby from [the Protocol Buffers Github repository](https://github.com/google/protobuf/releases), as well as a Go language generator from [the golang/protobuf Github repository](https://github.com/golang/protobuf), with more languages in development. You can find out more in the [proto3 language guide](https://developers.google.com/protocol-buffers/docs/proto3), and see the major differences from the current default version in the [release notes](https://github.com/google/protobuf/releases).


## Event Storming results instant implementataion
**Event storming** is a rapid, lightweight group modeling technique that is intense, fun, and useful for accelerating development teams. The brainchild of [Alberto Brandolini](https://skillsmatter.com/members/ziobrando#overview), it’s a synthesis of facilitated group learning practices from [Gamestorming](http://gamestorming.com/) and the principles of DDD.

An event storming session usually ran as a facilitated workshop. The group starts with domain events, walking through the model forwards and backwards to ensure that everything is covered. Then the group adds the commands, or triggers, that cause the events, and considers all sources of commands, including users, external systems, and even time.

The group identifies aggregates that accept commands and accomplish events, and begins to group aggregates together into bounded contexts. Finally, the relationships between bounded contexts are added to create a context map. The resulting model is then challenged with code in order to validate the group learning and verify the model.

It is important to remember that the domain expert is not interested in databases, web sockets, or design patterns, but in the business domain of the things that have to happen. 
**Protobuf** is an easy language, which means you can describe events, commands and aggregate states together with the domain experts just as you go through the Event Storming session in a way that specifies actual implementation.

## Domain model should be open for evolution 

No surprise that Domain model and our knowledge about it may evolve. So what it means to the application code? With traditional approach, when changing something in the Domain model on a backend side, means you have to manually update UI piece and all client applications.

### Problems with Java Serialization

The serialization mechanism automatically, at runtime, converts class objects into metadata so instances can be serialized with the least amount of programmer work.
This is great as long as the classes don't change. When classes change, the metadata, which was created from obsolete class objects, accurately describes the serialized information. But it might not correspond to the current class implementations.

Serialization is a generic marshalling and demarshalling algorithm, with many hooks for customization. Thus, serialization is, at times, both slow and bandwidth-intensive. There are three main performance problems with serialization: it depends on reflection, it has an incredibly verbose data format, and it is very easy to send more data than is required.

### Model evolution with Protobufs
Using Protocol Buffers allows extending model at your demand. As long as all Domain model building blocks are defined as protobuf messages, it becomes safe and easy to modify and version them. Moreover, it hugely saves developers effort

If an existing message type no longer meets all your needs – for example, you'd like the message format to have an extra field – but you'd still like to use code created with the old format, don't worry! It's very simple to update message types without breaking any of your existing code. 
More about updating message types you can read in [
Language Guide (proto3)](https://developers.google.com/protocol-buffers/docs/proto3#updating).