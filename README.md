# sebipom
Maven parent project file for use with sebi venlo projects. Split off from statewalker.

*Mavenitis* is not avoidable, but *Configuritis* is.
If you did not know: If you use maven, maven will be quite diligent ant ensure that all your
dependencies are up to date. This may and will lead to the behaviour of downloading the whole maven universe to
your machine, or at least the pieces (dependencies) that are in use by your project, directly or indirectly or transitivitely.

Once you get past the first symptoms of mavinitis, by simple accepting the dilligence that maven exhibts, because it takes
it task as serious as it does, you can avoid Configuritis by NOT configure every plugin in each and every project, but use something
similiar to sebipom as parent pom in your project. Since a parent pom can have a parent, this does not limit you when you want or need to define a multi-module project with a parent pom defining the modules.

You can use the configuration by defining sebipom as the parent by simply adding
```
  <parent>
        <groupId>nl.fontys.sebivenlo</groupId>
        <artifactId>sebipom</artifactId>
        <version>1.4.5</version>
	<relativePath/>
  </parent>
```
to your project's pom.

## Rationale

Sebi pom has some goodies that make it easy to use features with maven+java without falling into an install fest.
Feature:

* Nicely formatted code in javadoc by a highlighter plugin with configuration
* Java Coverage with JaCoCo
* PIT testing plugin
* JavaFX integration when using profile fx (e.g. mvn -P fx package)

From now on sebipon will have a repo on its own.

## For TDD fans.

**TL;DR:** Don't do `mvn package` or build (in your IDE) , do `mvn test` instead.


For those that are into test driven something:
Make it a habit to do `mvn test` instead of `mvn package`. `mvn package` typically does much more work than really required to get your tests do thier work. Enjoy the better maven experience this way.

Also, minimize the dependencies on SNAPSHOT versions of external dependencies, thereby avoiding a bit of mavenitis. You may also want to
minimize the number of indexing that your maven does. But DO index (once), every time you increment the versions on you local maven projects.

### JaCoCo

Since version 1.4.3, jacoco is now a profile that must be enabled. Rationale: during normal TDD cycles, you do not want the overhead of instrumented classes, so this move speeds up test builds.


## Run an FX application with this parent pom

When you are building a JavaFX application, remember to use the **fx** profile defined in this pom.

You do that by invoking e.g.  `mvn -P fx package`. If your application is called **app** with version **1.0**, then this will make a FAT jar named
`app-1.0-jar-with-dependencies.jar`.
