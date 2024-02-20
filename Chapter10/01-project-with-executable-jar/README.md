```bash
#####################################################################

$ tree -a .
.
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

11 directories, 3 files
$

#####################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X clean package

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
    ├── logback-classic-1.1.2.jar
    ├── logback-core-1.1.2.jar
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
    ├── project-with-executable-jar-1.0-SNAPSHOT.jar
    ├── slf4j-api-1.7.9.jar
    ├── surefire
    │   ├── surefire_0-20240220130424668_2tmp
    │   ├── surefire-20240220130424668_1tmp
    │   └── surefirebooter-20240220130424668_3.jar
    ├── surefire-reports
    │   ├── 2024-02-20T13-04-24_475-jvmRun1-commands.bin
    │   ├── 2024-02-20T13-04-24_475-jvmRun1-events.bin
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 22 files
$

#####################################################################

$ java -jar target/project-with-executable-jar-1.0-SNAPSHOT.jar
13:10:55.350 [main] INFO  com.packt.cookbook.App - Hello World
$

#####################################################################

```
