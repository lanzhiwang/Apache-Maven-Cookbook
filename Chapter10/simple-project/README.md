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
    ├── simple-project-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   └── com.packt.cookbook.AppTest.txt
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

32 directories, 14 files

$ java -jar target/simple-project-1.0-SNAPSHOT.jar
target/simple-project-1.0-SNAPSHOT.jar中没有主清单属性


$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── simple-project
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
└── simple-project-1.0-SNAPSHOT.jar

7 directories, 5 files

$ cat jar/META-INF/MANIFEST.MF
Manifest-Version: 1.0
Built-By: huzhi
Created-By: Apache Maven 3.6.3
Build-Jdk: 1.8.0_275

$

```
