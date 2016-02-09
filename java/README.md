# Spine Event Engine Basics: Java

<p class="lead">This tutorial provides a basic Java programmer's introduction to working with Spine. </p>


TODO:
### Stream Projection

### Projection



### Command Handler

For the majority of commands, a handler would be corresponding aggregate root object. Such method takes two parameters: <code>Message</code> for command instance and [CommandContext] (#commandcontext) for meta-information on the command. The method can have any name. We recommend call them <code>handle</code>:

<pre>
@Assign
public void handle(Message command, CommandContext ctx) {
   ...
}

</pre>

To be dispatched to the aggregate root, the command must have an attribute with an ID of the aggregate. See [Writing Aggregate Commands](/docs/tutorials/basic/java.html) for details.

Notice the annotation <code>@Assign</code>, which tells that the method participates in automatic dispatching of commands. 

A command handler method can throw [business failures] (#bizfailure). This means the API of each command handler allows:

* Either produce an event (or a list of events). Or,
* It can throw one or more business failures (which are clearly visible in the method signature).




### Command Dispatcher
Command Dispatcher invokes a handler method for the received command.

There can be **only** one handler method for one command type.

### Event Bus.
EventBus allows publish-subscribe-style communication between components without requiring the components to explicitly register with one another (and thus be aware of each other).


### Command Store

### Event Store

### Storage

### Repository 

### Query

### Service

### Catchup Subscription

### Snapshot

### Command Validation



<a name = "commandcontext"></a>
### Command Context

<a name="bizfailure"></a>
### Business Failure 
 In Spine system errors are separated from business logic failures that can be fixed by user (e.g. not enough money on credit card). 
 Below you can see a sample of the aggregate that throws a business failure on a command, which cannot be performed.
<pre>
@Assign
public TaskCancelled handle(CancelTask command, CommandContext context) throws CannotCancelTaskInProgress {
    final Task task = getState();
    if (task.getStatus() == Task.Status.IN_PROGRESS) {
            throw new CannotCancelTaskInProgress(task.getId());
        }

       return TaskCancelled.newBuilder().setId(task.getId()).build();
    }
</pre>