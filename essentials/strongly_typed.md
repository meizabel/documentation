# Strongly Typed

  Unlike some of  CQRS/ES frameworks that treat commands and events as Json objects, Spine promotes commands and events to be first class citizens in the applications, which gives a lot of benefits in business logic. Not having to convert back-and-forth with Json gives some performance advantage.

  The model [can be extended](https://developers.google.com/protocol-buffers/docs/proto3#updating) without breaking binary compatibility with client applications.