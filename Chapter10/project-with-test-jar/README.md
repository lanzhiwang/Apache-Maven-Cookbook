```bash

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
    ├── project-with-test-jar-1.0-SNAPSHOT.jar
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

##########################################


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
    ├── project-with-test-jar-1.0-SNAPSHOT-test-sources.jar
    ├── project-with-test-jar-1.0-SNAPSHOT.jar
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
│           └── project-with-test-jar
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── AppTest.java
└── project-with-test-jar-1.0-SNAPSHOT-test-sources.jar

7 directories, 5 files
$

```
