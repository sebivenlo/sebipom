# sebipom
maven project file for use with sebi venlo projects. Split off from statewalker.


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

## Run an FX application with this parent pom

When you are building a JavaFX application, remember to use the **fx** profile defined in this pom.

You do that by invoking e.g.  `mvn -P fx package`. If your application is called **app** with version **1.0**, then this will make a FAT jar named
`app-1.0-jar-with-dependencies.jar`.