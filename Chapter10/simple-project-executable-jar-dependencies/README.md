```bash

$ tree -a .
.
├── README.md
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── packt
    │               └── cookbook
    │                   └── App.java
    └── test
        └── java
            └── com
                └── packt
                    └── cookbook
                        └── AppTest.java

11 directories, 4 files


$ mvn clean package

$ java -jar target/simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
[main] INFO com.packt.cookbook.App - Hello World

$ ll target/*.jar
-rw-r--r--  1 huzhi  staff   3406 10  4 22:00 target/simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
-rw-r--r--  1 huzhi  staff  32121 10  4 21:08 target/slf4j-api-1.7.9.jar
-rw-r--r--  1 huzhi  staff  10704 10  4 21:40 target/slf4j-simple-1.7.9.jar

$

$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── simple-project-executable-jar-dependencies
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
└── simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar

7 directories, 5 files

$ cat jar/META-INF/MANIFEST.MF
Manifest-Version: 1.0
Built-By: huzhi
Class-Path: slf4j-api-1.7.9.jar slf4j-simple-1.7.9.jar
Created-By: Apache Maven 3.6.3
Build-Jdk: 1.8.0_275
Main-Class: com.packt.cookbook.App

$


$ mvn dependency:list
$ mvn dependency:tree

$ mvn help:describe -Dcmd=dependency:copy-dependencies -Ddetail
[INFO] Scanning for projects...
[INFO]
[INFO] ---< com.packt.cookbook:simple-project-executable-jar-dependencies >----
[INFO] Building simple-project-executable-jar-dependencies 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-help-plugin:3.2.0:describe (default-cli) @ simple-project-executable-jar-dependencies ---
[INFO] 'dependency:copy-dependencies' is a plugin goal (aka mojo).
Mojo: 'dependency:copy-dependencies'
dependency:copy-dependencies
  Description: Goal that copies the project dependencies from the repository
    to a defined location.
  Implementation:
  org.apache.maven.plugins.dependency.fromDependencies.CopyDependenciesMojo
  Language: java
  Bound to phase: process-sources

  Available parameters:

    addParentPoms (Default: false)
      User property: mdep.addParentPoms
      Add parent poms to the list of copied dependencies (both current project
      pom parents and dependencies parents).

    classifier
      User property: classifier
      Specify classifier to look for. Example: sources

    copyPom (Default: false)
      User property: mdep.copyPom
      Also copy the pom of each artifact.

    excludeArtifactIds
      User property: excludeArtifactIds
      Comma separated list of Artifact names to exclude.

    excludeClassifiers
      User property: excludeClassifiers
      Comma Separated list of Classifiers to exclude. Empty String indicates
      don't exclude anything (default).

    excludeGroupIds
      User property: excludeGroupIds
      Comma separated list of GroupId Names to exclude.

    excludeScope
      User property: excludeScope
      Scope threshold to exclude, if no value is defined for include. An empty
      string indicates no dependencies (default).
      The scope threshold value being interpreted is the scope as Maven filters
      for creating a classpath, not as specified in the pom. In summary:
      - runtime exclude scope excludes runtime and compile dependencies,
      - compile exclude scope excludes compile, provided, and system
        dependencies,
      - test exclude scope excludes all dependencies, then not really a
        legitimate option: it will fail, you probably meant to configure
        includeScope = compile
      - provided exclude scope just excludes provided dependencies,
      - system exclude scope just excludes system dependencies.

    excludeTransitive (Default: false)
      User property: excludeTransitive
      If we should exclude transitive dependencies

    excludeTypes
      User property: excludeTypes
      Comma Separated list of Types to exclude. Empty String indicates don't
      exclude anything (default).

    failOnMissingClassifierArtifact (Default: false)
      User property: mdep.failOnMissingClassifierArtifact
      This only applies if the classifier parameter is used.

    ignorePermissions
      not used in this goal

    includeArtifactIds
      User property: includeArtifactIds
      Comma separated list of Artifact names to include. Empty String indicates
      include everything (default).

    includeClassifiers
      User property: includeClassifiers
      Comma Separated list of Classifiers to include. Empty String indicates
      include everything (default).

    includeGroupIds
      User property: includeGroupIds
      Comma separated list of GroupIds to include. Empty String indicates
      include everything (default).

    includeScope
      User property: includeScope
      Scope threshold to include. An empty string indicates include all
      dependencies (default).
      The scope threshold value being interpreted is the scope as Maven filters
      for creating a classpath, not as specified in the pom. In summary:
      - runtime include scope gives runtime and compile dependencies,
      - compile include scope gives compile, provided, and system dependencies,
      - test include scope gives all dependencies (equivalent to default),
      - provided include scope just gives provided dependencies,
      - system include scope just gives system dependencies.

    includeTypes
      User property: includeTypes
      Comma Separated list of Types to include. Empty String indicates include
      everything (default).

    markersDirectory (Default:
    ${project.build.directory}/dependency-maven-plugin-markers)
      User property: markersDirectory
      Directory to store flag files

    outputAbsoluteArtifactFilename (Default: false)
      User property: outputAbsoluteArtifactFilename
      Output absolute filename for resolved artifacts

    outputDirectory (Default:
    ${project.build.directory}/dependency)
      User property: outputDirectory
      Output location.

    overWriteIfNewer (Default: true)
      User property: overWriteIfNewer
      Overwrite artifacts that don't exist or are older than the source.

    overWriteReleases (Default: false)
      User property: overWriteReleases
      Overwrite release artifacts

    overWriteSnapshots (Default: false)
      User property: overWriteSnapshots
      Overwrite snapshot artifacts

    prependGroupId (Default: false)
      User property: mdep.prependGroupId
      Prepend the groupId during copy.

    silent (Default: false)
      User property: silent
      If the plugin should be silent.

    skip (Default: false)
      User property: mdep.skip
      Skip plugin execution completely.

    stripClassifier (Default: false)
      User property: mdep.stripClassifier
      Strip artifact classifier during copy

    stripVersion (Default: false)
      User property: mdep.stripVersion
      Strip artifact version during copy

    type
      User property: type
      Specify type to look for when constructing artifact based on classifier.
      Example: java-source,jar,war

    useBaseVersion (Default: true)
      User property: mdep.useBaseVersion
      Either append the artifact's baseVersion or uniqueVersion to the
      filename. Will only be used if isStripVersion() is false.

    useJvmChmod
      not used in this goal

    useRepositoryLayout (Default: false)
      User property: mdep.useRepositoryLayout
      Place each artifact in the same directory layout as a default repository.

      example:

       /outputDirectory/junit/junit/3.8.1/junit-3.8.1.jar

    useSubDirectoryPerArtifact (Default: false)
      User property: mdep.useSubDirectoryPerArtifact
      Place each file in a separate subdirectory. (example
      /outputDirectory/junit-3.8.1-jar)

    useSubDirectoryPerScope (Default: false)
      User property: mdep.useSubDirectoryPerScope
      Place each type of file in a separate subdirectory. (example
      /outputDirectory/runtime /outputDirectory/provided etc)

    useSubDirectoryPerType (Default: false)
      User property: mdep.useSubDirectoryPerType
      Place each type of file in a separate subdirectory. (example
      /outputDirectory/jars /outputDirectory/wars etc)


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.089 s
[INFO] Finished at: 2021-10-04T21:20:44+08:00
[INFO] ------------------------------------------------------------------------
$










$ pwd
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-project-executable-jar-dependencies/jar

$ tree -a .
.
├── simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
├── slf4j-api-1.7.9.jar
└── slf4j-simple-1.7.9.jar

0 directories, 3 files


$ java -jar simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
[main] INFO com.packt.cookbook.App - Hello World

$ java -classpath /Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home/:/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home/lib/:/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-project-executable-jar-dependencies/jar/ -jar simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
[main] INFO com.packt.cookbook.App - Hello World


$ java -classpath /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-project-executable-jar-dependencies/jar/ -jar simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
[main] INFO com.packt.cookbook.App - Hello World

$ java -classpath ./ -jar simple-project-executable-jar-dependencies-1.0-SNAPSHOT.jar
[main] INFO com.packt.cookbook.App - Hello World

```
