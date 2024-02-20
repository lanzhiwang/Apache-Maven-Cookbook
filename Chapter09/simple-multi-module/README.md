```bash
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
└── pom.xml

15 directories, 8 files





$ pwd
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module

$ mvn clean package
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] simple-multi-module                                                [pom]
[INFO] Child Project                                                      [jar]
[INFO]
[INFO] ---------------< com.packt.cookbook:simple-multi-module >---------------
[INFO] Building simple-multi-module 1.0-SNAPSHOT                          [1/2]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ simple-multi-module ---
[INFO]
[INFO] ----------------------< com.packt.cookbook:child >----------------------
[INFO] Building Child Project 1.0-SNAPSHOT                                [2/2]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ child ---
[INFO] Deleting /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/target
[INFO]
[INFO] --- build-helper-maven-plugin:1.9.1:add-resource (add-resource) @ child ---
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ child ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/src/main/resources
[INFO] Copying 2 resources to xml
[INFO] Copying 1 resource to json
[INFO]
[INFO] --- maven-compiler-plugin:3.2:compile (default-compile) @ child ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/target/classes
[INFO]
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ child ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/src/test/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.2:testCompile (default-testCompile) @ child ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/target/test-classes
[INFO]
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ child ---
[INFO] Surefire report directory: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/target/surefire-reports

-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running com.packt.cookbook.AppTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.006 sec

Results :

Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

[INFO]
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ child ---
[INFO] Building jar: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/simple-multi-module/child/target/child-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for simple-multi-module 1.0-SNAPSHOT:
[INFO]
[INFO] simple-multi-module ................................ SUCCESS [  0.098 s]
[INFO] Child Project ...................................... SUCCESS [  1.089 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.257 s
[INFO] Finished at: 2021-10-05T16:16:13+08:00
[INFO] ------------------------------------------------------------------------

$ tree -a .
.
├── README.md
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
│       │   ├── TEST-com.packt.cookbook.AppTest.xml
│       │   └── com.packt.cookbook.AppTest.txt
│       └── test-classes
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.class
└── pom.xml

38 directories, 22 files
$

```
