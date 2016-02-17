# Welcome to Spine Event Engine

Spine Event Engine is a multi-language framework for building Command Query Responsibility Segregation ([CQRS](http://martinfowler.com/bliki/CQRS.html)) and Event Sourcing ([ES](http://martinfowler.com/eaaDev/EventSourcing.html)) applications.

Spine aims to free up developers from creating boilerplate code as much as possible. Our framework is built on top of [Protocol Buffers](https://developers.google.com/protocol-buffers/) (a.k.a. protobuf) and [gRPC](http://www.grpc.io/) to bring easiness and efficiency into development of applications with a microservice-oriented architecture. The goal is to allow developers to focus on the business logic, instead of the plumbing.

The primary language of the backend is Java. Client applications and server-side modules can be written in JavaScript, Java, JavaNano (Android), Swift, Objective-C, C, C++, C#, Go, Python, Ruby, and PHP.

### Why Spine?

*  **Domain model language is [Ubiquitous](http://martinfowler.com/bliki/UbiquitousLanguage.html)** not only in people interactions, but **in computer communications too**. The model is defined and maintained in protobuf. Most of the domain model code is automatically generated for all programming languages of your project.

*  **The domain model is strongly typed** and **open for evolution**. Unlike some of  CQRS/ES frameworks that treat commands and events as Json objects, Spine promotes strong typing of all parts of a business model. The model [can be extended](https://developers.google.com/protocol-buffers/docs/proto3#updating) without breaking binary compatibility with client applications.

*  **Choice of storage and deployment platforms.** The framework promotes writing code which does not depend on storage media or deployment platform. For example, you can start with JDBC-based storage and later switch to Google Cloud Platform Datastore by changing one line of the code. `TODO: link to the example.`

*  **Open Source.** Permissive [Apache  License](https://github.com/SpineEventEngine/core-java/blob/master/LICENSE) allows to use the framework in closed-source projects. You are welcome to [contribute](/contribute/index.html) to the framework development.

### Get Started

To get up and running with Spine, check the following articles:
* [Quick Start](/getting-started/index.md)

### Learn More

* Our [Motivation](/essentials.index.md) to build Spine
* [Java Documentation](/java.index.md)
* [Examples](/examples/index.md)