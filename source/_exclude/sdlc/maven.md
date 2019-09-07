# Maven
Maven is a build tool for Java, in Java.
1. All actual work is done by plugins
2. Plugins have goals
3. A lifecycle defines a sequence of phases
4. Phases are mapped to goals.
5. It's like `lifecycle :: [phase] ~ plugin :: [goal]`.

## Things Maven can manage
1. Builds
2. Documentation
3. Reporting
4. Dependencies
5. SCMs
6. Releases
7. Distribution

## Configuration
1. `<user_home>/.m2/settings.xml`
2. `<project_root>/.mvn/`: `maven.config`, `jvm.config`, and `extensions.xml`

## Built-in Build Lifecycles
1. **clean -** pre-clean, clean, post-clean
2. **default -** validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes, generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, verify, install, deploy
3. **site -** pre-site, site, post-site, site-deploy

See [Lifecycle Reference](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference)

## Project Object Model (POM)
Each Maven project has a `pom.xml`. It defines the project name, version number, dependencies and many other things.

## Dependencies
Dependencies are declared in `pom.xml`. Maven will look for `jar` files in `<user_home>/.m2/repositories/` (local repository). If it is not there, it will download it from a remote repository (by default, Maven Central: http://repo.maven.apache.org/maven2/). You can set up your own remote repository.

## Multiple Modules
In parent `pom.xml` (packaging must be `pom`) add `<modules>` and in child `pom.xml` add `<parent>`. Internal dependencies are solved automatically. 

- `<modules>` leftarrow; aggregation <kbd>rightarrow;</kbd> <kbd>rightarrow</kbd> &#8593;
- `<parent>` - inheritance
Note that by adding `<parent>` in child `pom.xml`, child `pom.xml` can inherent some elements from parent `pom.xml`.

## Binding Phases and Goals
Depending on the packaging (e.g. `jar`, `war`, `ear` and `pom`), a list of goals to bind to a particular phase. But you can custom it by adding `<plugins>` in `<build>` in `pom.xml` to add plugins which will bind its goals to phases, and adding `<executions>` in `<plugin>` to have more control.

See [Built-in Lifecycle Bindings](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Built-in_Lifecycle_Bindings)
