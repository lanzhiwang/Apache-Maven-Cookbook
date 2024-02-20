```bash
#####################################################################################

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

#####################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X package

#####################################################################################

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
    ├── simple-project-1.0-SNAPSHOT.jar
    ├── surefire
    │   ├── surefire_0-20240220104737282_2tmp
    │   ├── surefire-20240220104737282_1tmp
    │   └── surefirebooter-20240220104737282_3.jar
    ├── surefire-reports
    │   ├── 2024-02-20T10-47-37_168-jvmRun1-commands.bin
    │   ├── 2024-02-20T10-47-37_168-jvmRun1-events.bin
    │   ├── com.packt.cookbook.AppTest.txt
    │   └── TEST-com.packt.cookbook.AppTest.xml
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

33 directories, 19 files

#####################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X clean

#####################################################################################

```
