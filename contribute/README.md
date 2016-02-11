# How to Contribute

## Spine Development

If you plan to contribute to Spine development, please read the following documents:
* [Starter Guide Page](https://github.com/SpineEventEngine/core-java/wiki/Spine-Developer-Starter-Guide)
* [Coding Conventions](https://github.com/SpineEventEngine/core-java/wiki/Coding-Conventions)
* [InteliJ IDEA Configuration](https://github.com/SpineEventEngine/core-java/wiki/IntelliJ-IDEA-Configuration)
* [Using Gradle Snapshots](https://github.com/SpineEventEngine/core-java/wiki/Using-Gradle-Snapshots)

`TODO: we need to have one contrubutor guide`.

## Spine Documentation 

This documentation is built using [GitBook](https://www.gitbook.com/). 
If you’d like to help us improving the [Documentation](https://github.com/SpineEventEngine/documentation), you can do it in few ways.

###Leave a Comment
If you’d like to suggest a better definition or comment something — it’s easy through GitBook “Discussions”. 
1. Hover the paragraph you'd like to comment on, and  click `+` sign to open “New Discussion”.
2. Click “Post”. That’s it!

All comments reviewed and processed weekly.
 

### Add an Article or Text

If you’d like to add a new article or section to the documentation, work with GitBook as with any other Git Repository:
 1. Create a separate branch (you can do it even in GitBook online editor)
 2. Create a Pull Request and assign to [eugeniakotlyar](https://github.com/eugeniakotlyar) to review and approve.

Note: [**master**](https://github.com/SpineEventEngine/documentation) is a branch that goes to production.

### Documentation Conventions

#### Use syntax highlighting
Code examples should be given with syntax highlighting. To highlight blocks of code properly, use three back-ticks and corresponding language name.
For example:
<pre>```java
    // Some java code here.
```</pre>

<pre>```protobuf
    // Some protobuf code here.
```</pre>
 
#### Mark TODOs as code
If you leave a TODO comment in text, frame it as a code:

```
   `TODO: add link here.`
```
It would appear in the text like this: `TODO: add link here.`
