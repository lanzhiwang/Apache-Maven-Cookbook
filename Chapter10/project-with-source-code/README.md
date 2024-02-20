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

$ tree -a .
.
├── README.md
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── packt
│   │               └── cookbook
│   │                   └── App.java
│   └── test
│       └── java
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.java
└── target
    ├── classes
    │   └── com
    │       └── packt
    │           └── cookbook
    │               └── App.class
    ├── generated-sources
    │   └── annotations
    ├── generated-test-sources
    │   └── test-annotations
    ├── maven-archiver
    │   └── pom.properties
    ├── maven-status
    │   └── maven-compiler-plugin
    │       ├── compile
    │       │   └── default-compile
    │       │       ├── createdFiles.lst
    │       │       └── inputFiles.lst
    │       └── testCompile
    │           └── default-testCompile
    │               ├── createdFiles.lst
    │               └── inputFiles.lst
    ├── project-with-source-code-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   └── com.packt.cookbook.AppTest.txt
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

32 directories, 14 files
$


############################################################

$ mvn help:describe -DgroupId=org.apache.maven.plugins -DartifactId=maven-source-plugin -Dversion=3.2.1
source:aggregate
source:generated-test-jar
source:help
source:jar
source:jar-no-fork
source:test-jar
source:test-jar-no-fork

$ mvn help:describe -Dcmd=source:jar-no-fork -Ddetail
[INFO] 'source:jar-no-fork' is a plugin goal (aka mojo).
Mojo: 'source:jar-no-fork'
source:jar-no-fork
  Description: This goal bundles all the sources into a jar archive. This
    goal functions the same as the jar goal but does not fork the build and is
    suitable for attaching to the build lifecycle.
  Implementation: org.apache.maven.plugins.source.SourceJarNoForkMojo
  Language: java
  Bound to phase: package

  Available parameters:

    archive
      The archive configuration to use. See Maven Archiver Reference.
      Note: Since 3.0.0 the resulting archives contain a maven descriptor. If
      you need to suppress the generation of the maven descriptor you can
      simply achieve this by using the archiver configuration..

    attach (Default: true)
      User property: maven.source.attach
      Specifies whether or not to attach the artifact to the project

    classifier (Default: sources)
      User property: maven.source.classifier
      (no description available)

    defaultManifestFile (Default:
    ${project.build.outputDirectory}/META-INF/MANIFEST.MF)
      Required: true
      Path to the default MANIFEST file to use. It will be used if
      useDefaultManifestFile is set to true.

    excludeResources (Default: false)
      User property: maven.source.excludeResources
      Specifies whether or not to exclude resources from the sources-jar. This
      can be convenient if your project includes large resources, such as
      images, and you don't want to include them in the sources-jar.

    excludes
      List of files to exclude. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    finalName (Default: ${project.build.finalName})
      The filename to be used for the generated archive file. For the
      source:jar goal, '-sources' is appended to this filename. For the
      source:test-jar goal, '-test-sources' is appended.

    forceCreation (Default: false)
      User property: maven.source.forceCreation
      Whether creating the archive should be forced. If set to true, the jar
      will always be created. If set to false, the jar will only be created
      when the sources are newer than the jar.

    includePom (Default: false)
      User property: maven.source.includePom
      Specifies whether or not to include the POM file in the sources-jar.

    includes
      List of files to include. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    outputDirectory (Default: ${project.build.directory})
      The directory where the generated archive file will be put.

    outputTimestamp (Default: ${project.build.outputTimestamp})
      Timestamp for reproducible output archive entries, either formatted as
      ISO 8601 yyyy-MM-dd'T'HH:mm:ssXXX or as an int representing seconds since
      the epoch (like SOURCE_DATE_EPOCH).

    skipSource (Default: false)
      User property: maven.source.skip
      A flag used to disable the source procedure. This is primarily intended
      for usage from the command line to occasionally adjust the build.

    useDefaultExcludes (Default: true)
      User property: maven.source.useDefaultExcludes
      Exclude commonly excluded files such as SCM configuration. These are
      defined in the plexus FileUtils.getDefaultExcludes()

    useDefaultManifestFile (Default: false)
      User property: maven.source.useDefaultManifestFile
      Set this to true to enable the use of the defaultManifestFile.


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.189 s
[INFO] Finished at: 2021-10-05T14:20:06+08:00
[INFO] ------------------------------------------------------------------------
$

$ mvn clean package

$ tree -a .
.
├── README.md
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── packt
│   │               └── cookbook
│   │                   └── App.java
│   └── test
│       └── java
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.java
└── target
    ├── classes
    │   └── com
    │       └── packt
    │           └── cookbook
    │               └── App.class
    ├── generated-sources
    │   └── annotations
    ├── generated-test-sources
    │   └── test-annotations
    ├── maven-archiver
    │   └── pom.properties
    ├── maven-status
    │   └── maven-compiler-plugin
    │       ├── compile
    │       │   └── default-compile
    │       │       ├── createdFiles.lst
    │       │       └── inputFiles.lst
    │       └── testCompile
    │           └── default-testCompile
    │               ├── createdFiles.lst
    │               └── inputFiles.lst
    ├── project-with-source-code-1.0-SNAPSHOT-sources.jar
    ├── project-with-source-code-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   └── com.packt.cookbook.AppTest.txt
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

32 directories, 15 files

$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── project-with-source-code
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.java
└── project-with-source-code-1.0-SNAPSHOT-sources.jar

7 directories, 5 files

```
