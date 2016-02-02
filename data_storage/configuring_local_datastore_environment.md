# Configuring Local Datastore Environment

To run the sample on a local installation of Google Cloud Datastore, or to use it for working with the Datastore in your tests, please perform the following steps:

1. Download the [GCD tool](https://cloud.google.com/datastore/docs/downloads) and unzip it.  
   You may also want to download sources from [GCD GitHub Repository](https://github.com/GoogleCloudPlatform/google-cloud-datastore/).

2. Set the `GCD_HOME` OS environment variable to the path to the GCD tool root directory.  

3. Open the console, go to the GCD tool root directory. Then execute the following command

###### for Linux or Mac OS X:
```
./gcd.sh create -d spine-local-dataset my-project
````  

###### for Windows:
```
gcd create -d spine-local-dataset my-project
````  
Where `my-project` is your local project directory.  
You can also pass [DatastoreOptions](https://cloud.google.com/datastore/docs/apis/javadoc/com/google/api/services/datastore/client/DatastoreOptions) with a custom dataset name to `LocalDatastoreStorageFactory.newInstance(DatastoreOptions)` method and use this name instead of `spine-local-dataset` in this command.

#### Temporarily: start Local Datastore Server
To run tests, it is required to start the local Datastore Server manually, until this [issue](https://code.google.com/p/google-cloud-platform/issues/detail?id=10&thanks=10&ts=1443682670) is fixed and this [fix](https://github.com/GoogleCloudPlatform/google-cloud-datastore/commit/a077c5b4d6fa2826fd6c376b692686894b719fd9) is added to the next GCD library release.  
To start the local Datastore Server, please run the following command:

###### for Linux or Mac OS X:
```
./gcd.sh start --testing my-project
````  

###### for Windows:
```
gcd start --testing my-project
```` 

Where `my-project` is your local project directory.

#### Temporarily: install Spine core-java to the local Maven repository

It is also required to checkout [Spine core-java](https://github.com/SpineEventEngine/core-java) project, build it via Gradle and install to the local Maven repository.  
Please run the following command:
```
gradlew publishToMavenLocal
```


#### See Also
* [Using the GCD tool](https://cloud.google.com/datastore/docs/tools/)