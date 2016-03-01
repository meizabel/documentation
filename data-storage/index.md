# Repositories and Data Storages

## Repository
The repository is the mechanism that provides access to aggregates. The repository acts as a gateway to the actual storage mechanism used to persist the data. In CQRS, the repositories only need to be able to find aggregates based on their unique identifier. Any other types of queries should be performed against the query database, not the Repository.

In this section we will describe what data storage you can use building an application with Spine.

* [Datastore Environment](../data-storage/configuring-local-datastore-environment.md)
