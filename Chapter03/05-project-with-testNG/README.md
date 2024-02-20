```bash
#####################################################################

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

#####################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml test
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------< com.packt.cookbook:project-with-testNG >---------------
[INFO] Building Project with testNG 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ project-with-testNG ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/05-project-with-testNG/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ project-with-testNG ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ project-with-testNG ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/05-project-with-testNG/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ project-with-testNG ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ project-with-testNG ---
[INFO] Using auto detected provider org.apache.maven.surefire.testng.TestNGProvider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
Set up run
Fast test
Slow test
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.837 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.271 s
[INFO] Finished at: 2024-02-20T11:44:17Z
[INFO] ------------------------------------------------------------------------

#####################################################################

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
    ├── surefire-reports
    │   ├── 2024-02-20T11-43-59_882-jvmRun1-commands.bin
    │   ├── 2024-02-20T11-43-59_882-jvmRun1-events.bin
    │   ├── bullet_point.png
    │   ├── collapseall.gif
    │   ├── com.packt.cookbook.AppTest.txt
    │   ├── emailable-report.html
    │   ├── failed.png
    │   ├── index.html
    │   ├── jquery-1.7.1.min.js
    │   ├── junitreports
    │   │   └── TEST-com.packt.cookbook.AppTest.xml
    │   ├── navigator-bullet.png
    │   ├── old
    │   │   ├── index.html
    │   │   └── Surefire suite
    │   │       ├── classes.html
    │   │       ├── groups.html
    │   │       ├── index.html
    │   │       ├── main.html
    │   │       ├── methods-alphabetical.html
    │   │       ├── methods.html
    │   │       ├── methods-not-run.html
    │   │       ├── reporter-output.html
    │   │       ├── Surefire test.properties
    │   │       ├── testng.xml.html
    │   │       └── toc.html
    │   ├── passed.png
    │   ├── skipped.png
    │   ├── Surefire suite
    │   │   ├── Surefire test.html
    │   │   └── Surefire test.xml
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   ├── testng.css
    │   ├── testng-reports.css
    │   ├── testng-reports.js
    │   └── testng-results.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

35 directories, 42 files
$

#####################################################################

```
