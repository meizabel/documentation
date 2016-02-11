# Defining Business Failures

Spine makes a distinction between _error_ and _business failure_ (or just _failure_).

**An error** is a technical issue (a programming error, a resource lack, a technical malfunction). The end user usually cannot do much about an error.

**A business failure** is state of the business logic, which can be handled by the end user. Examples are “credit card validation declined”,  “order cannot be empty”, “insufficient funds”, etc.

In Spine failures are defined (surprise, surprise!) as protobuf messages:

``````protobuf
message OrderCannotBeEmpty {
    OrderId order_id = 1;
}
``````

Failures that are created in the `failures.proto` file under the package of an aggregate or a process manager.

The Spine model compiler takes the failure messages and generates Java classes with corresponding `Throwable`s, which can be used in corresponding parts of business logic.


 Below you can see a sample of the aggregate that throws a business failure on a command, which cannot be performed due to the current state of the aggregate.
 
``````java
@Assign
public TaskCancelled handle(CancelTask command, CommandContext context)
        throws CannotCancelTaskInProgress {
    final Task task = getState();
    if (task.getStatus() == Task.Status.IN_PROGRESS) {
            throw new CannotCancelTaskInProgress(task.getId());
        }

    return TaskCancelled.newBuilder().setId(task.getId()).build();
}
``````