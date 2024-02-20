```bash
#######################################################################

$ tree -a .
.
├── pom.xml
├── README.md
├── report
│   └── temp.txt
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

12 directories, 5 files

#######################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package
[INFO] Scanning for projects...
[INFO]
[INFO] ------< com.packt.cookbook:project-with-clean-additional-folder >-------
[INFO] Building Project with clean additional folder 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ project-with-clean-additional-folder ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ project-with-clean-additional-folder ---
[INFO] Changes detected - recompiling the module! :source
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/classes
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ project-with-clean-additional-folder ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ project-with-clean-additional-folder ---
[INFO] Changes detected - recompiling the module! :dependency
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/test-classes
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ project-with-clean-additional-folder ---
[INFO] Using auto detected provider org.apache.maven.surefire.junit.JUnit3Provider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.017 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- jar:3.3.0:jar (default-jar) @ project-with-clean-additional-folder ---
[INFO] Building jar: /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/target/project-with-clean-additional-folder-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.179 s
[INFO] Finished at: 2024-02-20T11:17:59Z
[INFO] ------------------------------------------------------------------------

#######################################################################

$ tree -a .
.
├── pom.xml
├── README.md
├── report
│   └── temp.txt
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
    ├── project-with-clean-additional-folder-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 15 files

#######################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml clean
[INFO] Scanning for projects...
[INFO]
[INFO] ------< com.packt.cookbook:project-with-clean-additional-folder >-------
[INFO] Building Project with clean additional folder 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- clean:3.2.0:clean (default-clean) @ project-with-clean-additional-folder ---
[INFO] Deleting /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/target
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.294 s
[INFO] Finished at: 2024-02-20T11:18:07Z
[INFO] ------------------------------------------------------------------------

#######################################################################

$ tree -a .
.
├── pom.xml
├── README.md
├── report
│   └── temp.txt
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

12 directories, 5 files
$

#######################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package
[INFO] Scanning for projects...
[INFO]
[INFO] ------< com.packt.cookbook:project-with-clean-additional-folder >-------
[INFO] Building Project with clean additional folder 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ project-with-clean-additional-folder ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ project-with-clean-additional-folder ---
[INFO] Changes detected - recompiling the module! :source
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/classes
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ project-with-clean-additional-folder ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ project-with-clean-additional-folder ---
[INFO] Changes detected - recompiling the module! :dependency
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/test-classes
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ project-with-clean-additional-folder ---
[INFO] Using auto detected provider org.apache.maven.surefire.junit.JUnit3Provider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.015 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- jar:3.3.0:jar (default-jar) @ project-with-clean-additional-folder ---
[INFO] Building jar: /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/target/project-with-clean-additional-folder-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.087 s
[INFO] Finished at: 2024-02-20T11:20:05Z
[INFO] ------------------------------------------------------------------------
$ tree -a .
.
├── pom.xml
├── README.md
├── report
│   └── temp.txt
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
    ├── project-with-clean-additional-folder-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 15 files

#######################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml clean
[INFO] Scanning for projects...
[INFO]
[INFO] ------< com.packt.cookbook:project-with-clean-additional-folder >-------
[INFO] Building Project with clean additional folder 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- clean:2.6:clean (default-clean) @ project-with-clean-additional-folder ---
[INFO] Deleting /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/target
[INFO] Deleting /usr/src/Apache-Maven-Cookbook/Chapter03/03-project-with-clean-additional-folder/report (includes = [], excludes = [])
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.283 s
[INFO] Finished at: 2024-02-20T11:20:12Z
[INFO] ------------------------------------------------------------------------

#######################################################################

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

#######################################################################

```
