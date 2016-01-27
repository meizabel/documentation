# Spine Developer Starter Guide

### General Information
Spine uses Gradle project build system.

### Gradle Configuration

1. Checkout and open project.
2. Sync Gradle. Wait for Maven repositories to be updated and indexes downloaded and built.
3. Build project.

Use Gradle wrapper instead of local Gradle distrubution. To do so you should use `gradlew clean` instead of `gradle clean` and so on.

### Note
- you must give Gradle wrapper execution rights first on Unix-based systems (`chmod +x ./gradlew`).