# Welcome to Spine Event Engine

Spine Event Engine is a multi-language framework for building Command Query Responsibility Segregation (CQRS) and Event Sourcing (ES) applications.

Spine aims to free up developers from creating boilerplate code as much as possible. Our framework is built on top of [Protocol Buffers](https://developers.google.com/protocol-buffers/docs/overview) (a.k.a. protobuf) and [gRPC](http://www.grpc.io/docs/) to bring easiness and efficiency into development of applications with a microservice-oriented architecture. You can focus on business logic, instead of the plumbing.

### Why Spine?

*  **Domain model language is [Ubiquitous](http://martinfowler.com/bliki/UbiquitousLanguage.html)** not only in people communications, but **in computer communications too**. The model is defined and maintained in protobuf. Most of the implementation code is automatically generated.

*  **The domain model is strongly typed and open for evolution**. Unlike some of  CQRS/ES frameworks that treat commands and events as Json objects, Spine promotes strong typing of all parts of a business model. The model [can be extended](https://developers.google.com/protocol-buffers/docs/proto3#updating) without breaking binary compatibility with client applications.

*  **Choice of storage and deployment platforms.** The framework promotes writing code which does not depend on storage media or deployment platform. For example, you can start with JDBC-based storage and later switch to Google Cloud Platform Datastore by changing one line of code. *TODO: link to the example.*

*  **Open Source.** The permissive [Apache V2 licence](https://github.com/SpineEventEngine/core-java/blob/master/LICENSE) allows to use the framework in closed-source projects. You are welcome to [contribute](/contribute/index.html) to the framework development.

Spine allows building applications with Java backend and any UI framework, as well as building client applications on Java, JavaScript, Android and iOS (Swift).




### Get Started

To get up and running with Spine, check the following articles:
* [Quick Start](
* Tutorials for Java Projects - TBD



### Learn More


* Spine Essentials
* Java Documentation
* Sample Projects