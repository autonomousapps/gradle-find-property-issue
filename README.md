Minimal reproducer for https://github.com/gradle/gradle/issues/29600.

Run `./gradlew help` and observe the output.

Expected behavior:
`project.findProperty` will walk the project hierarchy from the current project, to the parent, ...,
to the root project (eventually).

Observed behavior:
If the current project has no property defined, then the global property (defined in the root
`gradle.properties` file) will be used, ignoring any intermediate property defined in a 
`parent/gradle.properties` file.

Relates to https://github.com/gradle/gradle/issues/24491.
