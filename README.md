# fluffyj-archetype
An improved variety of a Maven Java project archetype. Extra fluffy ❤  
  
Contains defaults for often used maven properties and common test dependencies, e. g. [JUnit](https://junit.org/junit5) & [AssertJ](https://assertj.github.io/doc).  

The latest release version always tries to include the latest versions of all used dependencies and plugins.  

Projects created with this archetype will also contain reasonable default configuration for your favorit IDE. Have a look at the directory `ide_setup` for details.  

## Build  
Note: JDK >=17 is required for the build. 
  
`mvn clean install`  

### Maven < 3.5.0
When building with older Maven versions (looking at you, 3.3.9), make sure to activate the corresponding profile:
  
`mvn clean install -Pmvn33`  
  
This is required, because Maven switched from Eclipse Aether to Maven Artifact Resolver since 3.5.0.
  
## Usage
Generate a new project with this command:  
`mvn archetype:generate -B -DarchetypeGroupId=com.itemis -DarchetypeArtifactId=fluffyj.archetype -DarchetypeVersion=1.17.0 -DgroupId=de.my.groupid -DartifactId=de.my.groupid.artifactid -Dversion=1.0.0-SNAPSHOT -Dpackage=de.my.groupid.artifactid`
  
Build the created project with `mvn clean install`. When building with Maven < 3.5.0, you need to activate the appropriate profile: `mvn clean install -Pmvn33`.

## Development
The latest snapshot lives on the `develop` branch. The latest release lives on the `main` branch. A tag will be created for every release.

## Further Reading
[https://maven.apache.org/guides/mini/guide-creating-archetypes.html](https://maven.apache.org/guides/mini/guide-creating-archetypes.html)
  
