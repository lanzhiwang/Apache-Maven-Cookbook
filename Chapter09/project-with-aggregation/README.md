```bash

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
└── pom.xml

12 directories, 4 files


$ pwd
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation

$ mvn clean package
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] Aggregate Child Project                                            [jar]
[INFO] project-with-aggregation                                           [pom]
[INFO]
[INFO] -----------------< com.packt.cookbook:aggregate-child >-----------------
[INFO] Building Aggregate Child Project 1.0-SNAPSHOT                      [1/2]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ aggregate-child ---
[INFO]
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ aggregate-child ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/src/main/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ aggregate-child ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/target/classes
[INFO]
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ aggregate-child ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/src/test/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ aggregate-child ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/target/test-classes
[INFO]
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ aggregate-child ---
[INFO] Surefire report directory: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/target/surefire-reports

-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running com.packt.cookbook.AppTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.005 sec

Results :

Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

[INFO]
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ aggregate-child ---
[INFO] Building jar: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-aggregation/aggregate-child/target/aggregate-child-1.0-SNAPSHOT.jar
[INFO]
[INFO] ------------< com.packt.cookbook:project-with-aggregation >-------------
[INFO] Building project-with-aggregation 1.0-SNAPSHOT                     [2/2]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ project-with-aggregation ---
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for project-with-aggregation 1.0-SNAPSHOT:
[INFO]
[INFO] Aggregate Child Project ............................ SUCCESS [  1.075 s]
[INFO] project-with-aggregation ........................... SUCCESS [  0.003 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.146 s
[INFO] Finished at: 2021-10-05T15:54:14+08:00
[INFO] ------------------------------------------------------------------------

$ tree -a .
.
├── README.md
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

29 directories, 15 files
$










```

