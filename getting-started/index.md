# Getting Started 


<p class="lead">To get up and running with Spine straight away, see the quick start, which provides links to installation instructions, quick instructions for building the example used in this guide, and more.</p>

## Add Spine dependencies to Gradle project
There are three artifacts that need to be added to your project:
1. Client-side library.
2. Model compiler and checker — for the server-side code with your business model.
3. Server-side library — for the server-side code.


### Add model compiler and checker
TODO

### Add client-side library
For client-side applications written in Java, please add the following:
<pre>
dependencies {
    compile group: 'org.spine3', name: 'client', version: '1.+'

}
</pre>


### Add server-side library
For server-side modules of your app, please add the following:
<pre>
dependencies {
...
    compile group: 'org.spine3', name: 'server', version: '1.+'

version: '3.0.0-beta-1'
}
</pre>


### “Hellow Spine!” Sample Project
* Define commands, events, aggregate and projection states in protobuf.
* Define business logic of aggregates and projections.
* Create repositories.
* Init Bounded Context with repositories and Storage Factory.
* Create Application class and execute.


 ** TODO:** create sample classes/proto for pp 1 to 3
 
 **TODO:** establish maven dependency?
You can find Spine source code in the [GitHub repositories](https://github.com/SpineEventEngine).
