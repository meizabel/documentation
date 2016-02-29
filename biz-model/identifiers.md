# Entitity Identifiers

An entity identifier can be of one of the following types:
 * String
 * Long
 * Integer
 * A class implementing `Message`
 

Consider using `Message`-based IDs if you want to have [typed IDs](../motivation/strongly-typed.md) in your code and/or if you need to have IDs with some structure inside. Examples of such structural IDs are:
* EAN value used in bar codes
* ISBN
* Phone number
* email address

