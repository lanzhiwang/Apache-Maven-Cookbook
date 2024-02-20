```bash
###########################################################################

$ tree .
.
├── pom.xml
├── README.md
└── src
    ├── main
    │   ├── java
    │   │   └── com
    │   │       └── packt
    │   │           └── cookbook
    │   │               └── App.java
    │   └── resources
    │       └── app.properties
    └── test
        └── java
            └── com
                └── packt
                    └── cookbook
                        └── AppTest.java

12 directories, 5 files
$

###########################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X package

###########################################################################

$ tree -a target/
target/
├── classes
│   ├── app.properties
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
├── project-with-resources-1.0-SNAPSHOT.jar
├── surefire
│   ├── surefire_0-20240220101435846_2tmp
│   ├── surefire-20240220101435846_1tmp
│   └── surefirebooter-20240220101435846_3.jar
├── surefire-reports
│   ├── 2024-02-20T10-14-35_485-jvmRun1-commands.bin
│   ├── 2024-02-20T10-14-35_485-jvmRun1-events.bin
│   ├── com.packt.cookbook.AppTest.txt
│   └── TEST-com.packt.cookbook.AppTest.xml
└── test-classes
    └── com
        └── packt
            └── cookbook
                └── AppTest.class

21 directories, 16 files
$

###########################################################################

$ jar -xvf project-with-resources-1.0-SNAPSHOT.jar
  created: META-INF/
 inflated: META-INF/MANIFEST.MF
  created: com/
  created: com/packt/
  created: com/packt/cookbook/
  created: META-INF/maven/
  created: META-INF/maven/com.packt.cookbook/
  created: META-INF/maven/com.packt.cookbook/project-with-resources/
 inflated: app.properties
 inflated: com/packt/cookbook/App.class
 inflated: META-INF/maven/com.packt.cookbook/project-with-resources/pom.xml
 inflated: META-INF/maven/com.packt.cookbook/project-with-resources/pom.properties

###########################################################################

$ tree -a .
.
├── app.properties
├── com
│   └── packt
│       └── cookbook
│           └── App.class
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── project-with-resources
│               ├── pom.properties
│               └── pom.xml
└── project-with-resources-1.0-SNAPSHOT.jar

7 directories, 6 files

###########################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X process-resources

###########################################################################

$ tree -a .
.
├── pom.xml
├── README.md
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com
│   │   │       └── packt
│   │   │           └── cookbook
│   │   │               └── App.java
│   │   └── resources
│   │       └── app.properties
│   └── test
│       └── java
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.java
└── target
    └── classes
        └── app.properties

14 directories, 6 files
$

###########################################################################

```
