# Command Validation

Each command has additional additional attributes that are *required* from the business logic stand point, they are not obligatory from the [protocol](https://developers.google.com/protocol-buffers/docs/proto#customoptions) stand point.

## Command Validator

<a name="bizfailure"></a>
## Business Failure 
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