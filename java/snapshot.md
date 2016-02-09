# Snapshot

A Snapshot is a projection of the current state of an aggregate at a given point in time. It represents the state when all events to that point in time have been replayed. Snapshots are used as a heuristic to prevent the need to load all events for the entire history of an aggregate. 

### Catch-up Subscription
This is the process. 
