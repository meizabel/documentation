# Using Gradle Snapshots

By default, Gradle build does not support snapshots. If you want to use snapshot Spine build, you should adjust your build scripts to contain the following setup. 

### Zero amount of seconds for caching
> ```        
    configurations.all { 
        resolutionStrategy.cacheChangingModulesFor 0, 'seconds' 
    }
```

### `Changing` property for dependency set to `true`
Set up your snapshot dependencies to have `changing` property. For example:
> ```
   compile group: 'org.spine3', name: 'core-java', version: '0.1-SNAPSHOT', changing:true
```

### Repeat for `buildscript`
Same for `buildscript` dependencies: `configurations` section should be repeated, and `changing` attribute should be applied to `classpath` and other dependencies.