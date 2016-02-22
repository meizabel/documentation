# Ubiquitous Language

Ubiquitous language — a language structured around the domain model and used by all team members to connect all the activities of the team with the software.

In Spine Event Engine a Domain Model, including commands, events and aggregates, projections and business failures, is described using Protocol Buffers.

##Cross-platform compatibility
Using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview) allows automatic code generation for events and commands on variety of platforms hugely saving development team effort.

By default Spine Event Engine uses *Protocol Buffers*, Google’s mature open source mechanism for serializing structured data. You can find out lots more about Protocol Buffers in the [Protocol Buffers documentation](https://developers.google.com/protocol-buffers/docs/overview).

#### Protocol Buffer versions

While Protocol Buffers have been available for open source users for some time, Spine uses a new flavor of Protocol Buffers called proto3, which has a slightly simplified syntax, some useful new features, and supports more languages. This is currently available as an beta release in Java and C++, with an alpha release for JavaNano (Android Java), Python, and Ruby from [the Protocol Buffers Github repo](https://github.com/google/protobuf/releases), as well as a Go language generator from [the golang/protobuf Github repo](https://github.com/golang/protobuf), with more languages in development. You can find out more in the [proto3 language guide](https://developers.google.com/protocol-buffers/docs/proto3), and see the major differences from the current default version in the [release notes](https://github.com/google/protobuf/releases).


## Event Storming results implementataion
**Event storming** is a rapid, lightweight group modeling technique that is intense, fun, and useful for accelerating development teams. 

An event storming session usually ran as a facilitated workshop. Everyone participates, and the facilitator keeps the group focused and engaged, guiding progress toward a complete model of the domain. The group starts with domain events, walking through the model forwards and backwards to ensure that everything is covered. Then the group adds the commands, or triggers, that cause the events, and considers all sources of commands, including users, external systems, and even time.

The group identifies aggregates that accept commands and accomplish events, and begins to group aggregates together into bounded contexts. Along the way, key test scenarios, users, and goals are identified and incorporated into the model. Finally, the relationships between bounded contexts are added to create a context map. The resulting model is then challenged with code in order to validate the group learning and verify the model.

The domain expert is not interested in databases, web sockets, or design patterns, but in the business domain of the things that have to happen. 
Protobuf is an easy language. And you can describe events, commands and aggregate states together with domain experts just as you go through the Event Storming session in a way that doesn't specify a particular implementation.

## Domain model should be open for evolution

`TODO: problems with Java Serialization`