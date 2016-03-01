# Entitity Identifiers

An Entity identifier can be of one of the following types:
 * `String`
 * `Long`
 * `Integer`
 * A protobuf `Message`
 
Consider using `Message`-based IDs if you want to have [typed IDs](../motivation/strongly-typed.md) in your code and/or if you need to have Identifiers with some structure inside. Examples of such structural IDs are:
* EAN value used in bar codes
* ISBN
* Phone number
* email address with a local-part and domain
