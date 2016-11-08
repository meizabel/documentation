# Frequently Asked

 
### Why framework is called Spine?
 We want to be a framework that provides an infrastructure and connects so to say “service” parts of applications with their “brains” — business logic. 
 Find out how following [leading industry trends](prior-art.html) we were [inspired](/docs/guides/motivation.html) to create Spine. 

### Why Java 7?
**The code of the framework is based on Java 7. Why not on Java 8, with Java 9 around the corner?**

One of the major deployment platforms for us is Google App Engine (GAE). The latest version of Java supported under GAE is Java 7. Google recently [announced Java 8 support under GAE](https://youtu.be/aKUlu9-psZo?t=15m30s). We will be able to migrate once Sandbox mode of GAE works on Java 8.

### Why Protobuf and not Json?
Because Protocol Buffers are implemented in a variety of languages, they make interoperability between polyglot applications in your architecture that much simpler. If you’re introducing a new service with one in Ruby or Go, or even communicating with a backend written in Node, or Clojure, you simply have to hand the proto file to the code generator written in the target language and you have some nice guarantees about the safety and interoperability between those architectures. 

The finer points of platform specific data types should be handled for you in the target language implementation, and you can get back to focusing on the hard parts of your problem instead of matching up fields and data types in your ad hoc JSON encoding and decoding schemes.

### Why Protobuf instead of Cap'n Proto, or SBE, or FlatBuffers?
Have a look the [comparison matrix](https://capnproto.org/news/2014-06-17-capnproto-flatbuffers-sbe.html) created Kenton Varda, the author of Protobuf v2 and Cap'n Proto. The main features that make Protobuf best choice for Spine are:

* **Schema evolution** — we need this as business models evolve as business grows.
* **Usable as mutable state** — we need this for transforming Aggregate States and Stream Projections.
* **Other languages** — we need a support of client applications written on JavaScript, JavaNano, Swift, Objective-C, etc.

Also, the experience Google gained through years of using this technology internally is a major factor of preferring Protobuf over alternatives.

### Which version of Protobuf do you use?
The framework is based on [proto3 dialect](https://developers.google.com/protocol-buffers/docs/proto3).

