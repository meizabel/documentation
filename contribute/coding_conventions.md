# Coding Conventions
## General Rules
We use [Google Style](https://google.github.io/styleguide/javaguide.html) conventions with the following modifications:
* 4 spaces instead of 2 for indentation;
* 120 characters right margin (instead of 80 or 100);
* other extensions and changes described in the sections below.

## Package local member declaration
In order to express package-visible members in an obvious way please use `/* package */` comment prior to the member declaration. 

````
  // This field must be accessible from the enclosing package.
  /* package */ MessageService messageService;
````

This rule also applies to the fields and methods of the private final inner classes to emphasize the intention to make them visible from the outer class.

``````java
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
``````

## JavaDocs
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

## Dealing with `null`s

### `@ParametersAreNonnullByDefault`
This annotation must be set in `package-info.java` of all the framework packages.

### Use `@Nullable` when required
Everything which is not annotated with `@Nullable` is not `null` by default.

### Checking multiple parameters with `checkNotNull()`
Non-nullity of parameters should be checked in `public` and `protected` methods to catch incorrect use of the API as early as possible.

If a method accepts two or more parameters that cannot be `null` we call `Preconditions.checkNotNull()` in the order of parameters. `checkNotNull()` must be statically imported:

`````java
    protected void dispatch(Message message, CommandContext context) {
        checkNotNull(message);
        checkNotNull(context);
        ...
    }
````` 

### Check `null` state with `checkNotNull()`
By convention checking nullity of a state should be done via `checkNotNull()`, not via `checkState()`. For example, a `Product.Builder`’s method `build()` should look like this: 

``````java
    ...

    public Product build() {
        checkNotNull(this.name, "Product name must be set.");
        checkNotNull(this.price, "Product price must be set.");
        ...
    }
``````

