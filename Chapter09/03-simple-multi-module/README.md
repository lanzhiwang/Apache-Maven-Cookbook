```bash
#############################################################################################

$ tree -a .
.
├── child
│   ├── pom.xml
│   └── src
│       ├── main
│       │   └── java
│       │       └── com
│       │           └── packt
│       │               └── cookbook
│       │                   └── App.java
│       ├── resources
│       │   ├── json
│       │   │   ├── exclude.json
│       │   │   └── include.json
│       │   └── xml
│       │       ├── one.xml
│       │       └── two.xml
│       └── test
│           └── java
│               └── com
│                   └── packt
│                       └── cookbook
│                           └── AppTest.java
├── pom.xml
└── README.md

15 directories, 9 files
$

#############################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml dependency:tree
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] simple-multi-module                                                [pom]
[INFO] Child Project                                                      [jar]
[INFO]
[INFO] ---------------< com.packt.cookbook:simple-multi-module >---------------
[INFO] Building simple-multi-module 1.0-SNAPSHOT                          [1/2]
[INFO]   from pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- dependency:3.6.1:tree (default-cli) @ simple-multi-module ---
[INFO] com.packt.cookbook:simple-multi-module:pom:1.0-SNAPSHOT
[INFO]
[INFO] ----------------------< com.packt.cookbook:child >----------------------
[INFO] Building Child Project 1.0-SNAPSHOT                                [2/2]
[INFO]   from child/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- dependency:3.6.1:tree (default-cli) @ child ---
[INFO] com.packt.cookbook:child:jar:1.0-SNAPSHOT
[INFO] \- junit:junit:jar:3.8.1:test
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for simple-multi-module 1.0-SNAPSHOT:
[INFO]
[INFO] simple-multi-module ................................ SUCCESS [  2.477 s]
[INFO] Child Project ...................................... SUCCESS [  0.085 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.848 s
[INFO] Finished at: 2024-02-21T12:39:46Z
[INFO] ------------------------------------------------------------------------
$

#############################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package

#############################################################################################

$ tree -a .
.
├── child
│   ├── pom.xml
│   ├── src
│   │   ├── main
│   │   │   └── java
│   │   │       └── com
│   │   │           └── packt
│   │   │               └── cookbook
│   │   │                   └── App.java
│   │   ├── resources
│   │   │   ├── json
│   │   │   │   ├── exclude.json
│   │   │   │   └── include.json
│   │   │   └── xml
│   │   │       ├── one.xml
│   │   │       └── two.xml
│   │   └── test
│   │       └── java
│   │           └── com
│   │               └── packt
│   │                   └── cookbook
│   │                       └── AppTest.java
│   └── target
│       ├── child-1.0-SNAPSHOT.jar
│       ├── classes
│       │   ├── com
│       │   │   └── packt
│       │   │       └── cookbook
│       │   │           └── App.class
│       │   ├── json
│       │   │   └── include.json
│       │   └── xml
│       │       ├── one.xml
│       │       └── two.xml
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

38 directories, 22 files
$

#############################################################################################

```
