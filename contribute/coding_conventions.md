# Coding Conventions

### Class description
Please use the following layout.
```
/**
 * Class description goes here.
 *
 * <p>More details on the class.
 *
 * @author John Doe
 */
```

## Code in Prototobuf documentation and GitHub comments
Please use \` \` quotes (as in Markdown) to mark code names in Protobuf documentation and GitHub comments.

````
  // This field contains string representation of `AggregateId`.
  string aggregate_id = 5;
````

## Package local member declaration
In order to express package-visible members in an obvious way please use `/* package */` comment prior to the member declaration. 

````
  // This field must be accessible from the enclosing package.
  /* package */ MessageService messageService;
````

This rule also applies to the fields and methods of the private final inner classes to emphasize the intention to make them visible from the outer class.

````
public class Parent {

    // ...

    public void startProcessing(Message message) {
        // ...
        final Inner innerInstance = getInnerInstance();
        innerInstance.messageService.processMessage(message);
    }

    private static final class Inner {
        //This field is used in the parent scope
        /* package */ MessageService messageService;
    }
}
````
