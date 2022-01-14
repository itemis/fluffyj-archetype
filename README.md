# fluffyj-archetype
An improved variety of a Maven Java project archetype. Extra fluffy ❤  
  
Contains defaults for often used maven properties and common test dependencies, e. g. [JUnit](https://junit.org/junit5) & [AssertJ](https://assertj.github.io/doc).  

The latest release version always tries to include the latest versions of all used dependencies and plugins.  

Projects created with this archetype will also contain reasonable default configuration for your favorit IDE. Have a look at the directory `ide_setup` for details.  

## Build
`mvn clean install`  

### Maven < 3.5.0
When building with older Maven versions (looking at you, 3.3.9), make sure to activate the corresponding profile:
  
`mvn clean install -Pmvn33`  
  
This is required, because Maven switched from Eclipse Aether to Maven Artifact Resolver since 3.5.0.
  
## Usage
Generate a new project with this command:  
`mvn archetype:generate -B -DarchetypeGroupId=com.itemis -DarchetypeArtifactId=fluffyj.archetype -DarchetypeVersion=1.9.0 -DgroupId=de.my.groupid -DartifactId=de.my.groupid.artifactid -Dversion=1.0.0-SNAPSHOT -Dpackage=de.my.groupid.artifactid`
  
Build the created project with `mvn clean install`. When building with Maven < 3.5.0, you need to activate the appropriate profile: `mvn clean install -Pmvn33`.
  
### Note on usage with Java >=16
When running Maven with Java >16 make sure to use the latest archetype plugin version (currently 3.2.0). You can force the version by calling Maven like this:  
  
`mvn org.apache.maven.plugins:maven-archetype-plugin:3.2.0:generate ...`  
  
Background: The fluffy archetype is using a post generation script based on Groovy. Java 16 is the first Java version not permitting old Groovy versions to do any reflection without providing a proper module configuration. If you use an old archetype plugin version (e. g. 3.0.1), you are also going to use an old Groovy version. This will result in an error like this:  
  
`
 Unable to make protected void java.lang.Object.finalize() throws java.lang.Throwable accessible: module java.base does not "opens java.lang" to unnamed module
 `  

Until Java 16 this used to be:  
`[INFO] Executing META-INF/archetype-post-generate.groovy post-generation script
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.codehaus.groovy.reflection.CachedClass$3$1 (file:/C:/Users/itsme/.m2/repository/org/codehaus/groovy/groovy/1.8.3/groovy-1.8.3.jar) to method java.lang.Object.finalize()
WARNING: Please consider reporting this to the maintainers of org.codehaus.groovy.reflection.CachedClass$3$1
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release`  
  
In order to prevent this, an up to date Groovy version must be used, which is only the case with up to date versions of the archetype plugin.  

## Development
The latest snapshot lives on the `develop` branch. The latest release lives on the `main` branch. A tag will be created for every release.

## Further Reading
[https://maven.apache.org/guides/mini/guide-creating-archetypes.html](https://maven.apache.org/guides/mini/guide-creating-archetypes.html)
  
