```bash
#######################################################################################

$ tree -a .
.
├── pom.xml
├── README.md
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
$

#######################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X package

#######################################################################################

$ tree -a .
.
├── pom.xml
├── README.md
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
    ├── project-with-clean-disabled-1.0-SNAPSHOT.jar
    ├── surefire
    │   ├── surefire_0-20240220110507531_2tmp
    │   ├── surefire-20240220110507531_1tmp
    │   └── surefirebooter-20240220110507531_3.jar
    ├── surefire-reports
    │   ├── 2024-02-20T11-05-07_418-jvmRun1-commands.bin
    │   ├── 2024-02-20T11-05-07_418-jvmRun1-events.bin
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 19 files
$

#######################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X clean

#######################################################################################

$ tree -a .
.
├── pom.xml
├── README.md
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
    ├── project-with-clean-disabled-1.0-SNAPSHOT.jar
    ├── surefire
    │   ├── surefire_0-20240220110507531_2tmp
    │   ├── surefire-20240220110507531_1tmp
    │   └── surefirebooter-20240220110507531_3.jar
    ├── surefire-reports
    │   ├── 2024-02-20T11-05-07_418-jvmRun1-commands.bin
    │   ├── 2024-02-20T11-05-07_418-jvmRun1-events.bin
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 19 files
$

#######################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-Ddetail \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-clean-plugin \
-Dversion=2.6 \
-Dcmd=clean:clean
[INFO] Scanning for projects...
[INFO]
[INFO] -----------< com.packt.cookbook:project-with-clean-disabled >-----------
[INFO] Building Project with clean disabled 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ project-with-clean-disabled ---
[INFO] 'clean:clean' is a plugin goal (aka mojo).
Mojo: 'clean:clean'
clean:clean
  Description: Goal which cleans the build.


    This attempts to clean a project's working directory of the files that were
    generated at build-time. By default, it discovers and deletes the
    directories configured in project.build.directory,
    project.build.outputDirectory, project.build.testOutputDirectory, and
    project.reporting.outputDirectory.



    Files outside the default may also be included in the deletion by
    configuring the filesets tag.
  Implementation: org.apache.maven.plugin.clean.CleanMojo
  Language: java

  Available parameters:

    excludeDefaultDirectories (Default: false)
      User property: clean.excludeDefaultDirectories
      Disables the deletion of the default output directories configured for a
      project. If set to true, only the files/directories selected via the
      parameter {@link #filesets} will be deleted.

    failOnError (Default: true)
      User property: maven.clean.failOnError
      Indicates whether the build will continue even if there are clean errors.

    filesets
      The list of file sets to delete, in addition to the default directories.
      For example: <filesets> <fileset>
      <directory>src/main/generated</directory>
      <followSymlinks>false</followSymlinks>
      <useDefaultExcludes>true</useDefaultExcludes> <includes>
      <include>*.java</include> </includes> <excludes>
      <exclude>Template*</exclude> </excludes> </fileset> </filesets>

    followSymLinks (Default: false)
      User property: clean.followSymLinks
      Sets whether the plugin should follow symbolic links while deleting files
      from the default output directories of the project. Not following
      symlinks requires more IO operations and heap memory, regardless whether
      symlinks are actually present. So projects with a huge output directory
      that knowingly does not contain symlinks can improve performance by
      setting this parameter to true.

    retryOnError (Default: true)
      User property: maven.clean.retryOnError
      Indicates whether the plugin should undertake additional attempts (after
      a short delay) to delete a file if the first attempt failed. This is
      meant to help deleting files that are temporarily locked by third-party
      tools like virus scanners or search indexing.

    skip (Default: false)
      User property: clean.skip
      Disables the plugin execution.

    verbose
      User property: clean.verbose
      Sets whether the plugin runs in verbose mode. As of plugin version 2.3,
      the default value is derived from Maven's global debug flag (compare
      command line switch -X).


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.892 s
[INFO] Finished at: 2024-02-20T11:10:38Z
[INFO] ------------------------------------------------------------------------
$

```
