# Ubiquitous Language

Ubiquitous language — a language structured around the domain model and used by all team members to connect all the activities of the team with the software.

In Spine Event Engine a Domain Model, including commands, events and aggregates, Projections and Business Failures, is described using Protocol Buffers.

###Cross-platform compatibility
Using [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview) allows automatic code generation for events and commands on variety of platforms hugely saving development team effort.

By default Spine Event Engine uses *Protocol Buffers*, Google’s mature open source mechanism for serializing structured data. Youcan find out lots more about Protocol Buffers in the [Protocol Buffers documentation](https://developers.google.com/protocol-buffers/docs/overview).

#### Protocol Buffer versions

While Protocol Buffers have been available for open source users for some
time, Spine uses a new flavor of Protocol Buffers called proto3,
which has a slightly simplified syntax, some useful new features, and supports
lots more languages. This is currently available as an beta release in
Java and C++, with an alpha release for JavaNano (Android Java), Python, and
Ruby from [the Protocol Buffers Github
repo](https://github.com/google/protobuf/releases), as well as a Go language
generator from [the golang/protobuf Github repo](https://github.com/golang/protobuf), with more languages in development. You can find out more in the [proto3 language guide](https://developers.google.com/protocol-buffers/docs/proto3), and see
the major differences from the current default version in the [release notes](https://github.com/google/protobuf/releases).


TODO: faster implementation of results of Event Storming.
Protobuf is an easy language.

### Domain model should be open for evolution

TODO: problems with Java Serialization