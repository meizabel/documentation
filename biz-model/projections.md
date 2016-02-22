#Projections

Projection is an important [concept](https://msdn.microsoft.com/en-us/library/dn589792.aspx) while building event-centric systems. At the same time, it is extremely simple. Projection is about deriving current state from the stream of events.

However, there is an important concept behind this simplicity. Given the stream of events, we can project them to any structural representation. Structural representation here refers not only to the schema of a read model, but also to the implementation details of how this model is stored and accessed.



