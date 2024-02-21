```bash
###################################################################################

$ tree -a .
.
├── aggregate-child
│   ├── pom.xml
│   └── src
│       ├── main
│       │   └── java
│       │       └── com
│       │           └── packt
│       │               └── cookbook
│       │                   └── App.java
│       └── test
│           └── java
│               └── com
│                   └── packt
│                       └── cookbook
│                           └── AppTest.java
├── pom.xml
└── README.md

12 directories, 5 files
$


###################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package

###################################################################################

$ tree -a .
.
├── aggregate-child
│   ├── pom.xml
│   ├── src
│   │   ├── main
│   │   │   └── java
│   │   │       └── com
│   │   │           └── packt
│   │   │               └── cookbook
│   │   │                   └── App.java
│   │   └── test
│   │       └── java
│   │           └── com
│   │               └── packt
│   │                   └── cookbook
│   │                       └── AppTest.java
│   └── target
│       ├── aggregate-child-1.0-SNAPSHOT.jar
│       ├── classes
│       │   └── com
│       │       └── packt
│       │           └── cookbook
│       │               └── App.class
│       ├── generated-sources
│       │   └── annotations
│       ├── generated-test-sources
│       │   └── test-annotations
│       ├── maven-archiver
│       │   └── pom.properties
│       ├── maven-status
│       │   └── maven-compiler-plugin
│       │       ├── compile
│       │       │   └── default-compile
│       │       │       ├── createdFiles.lst
│       │       │       └── inputFiles.lst
│       │       └── testCompile
│       │           └── default-testCompile
│       │               ├── createdFiles.lst
│       │               └── inputFiles.lst
│       ├── surefire-reports
│       │   ├── com.packt.cookbook.AppTest.txt
│       │   └── TEST-com.packt.cookbook.AppTest.xml
│       └── test-classes
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.class
├── pom.xml
└── README.md

33 directories, 15 files
$

###################################################################################

```
