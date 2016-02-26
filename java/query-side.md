# Query Side

## Projection

TBD

## Entity Fragment

**Entity Fragment** — a message with partial state of an entity. It returns a fragment of the entire state filtered using `FieldMasks` provided in a query.

Field masks are used to specify a subset of fields that should be returned by a get operation or modified by an update operation

As [protobuf documentation](https://developers.google.com/protocol-buffers/docs/reference/csharp/class/google/protobuf/well-known-types/field-mask) states:
>When used in the context of a projection, a response message or sub-message is filtered by the API to only contain those fields as specified in the mask. 

##Query
 TBD

## Service
TBD