```bash
###########################################################################################

$ tree -a .
.
├── common-one
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
├── dev-two
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

30 directories, 16 files
$

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -P dev package
[INFO] Scanning for projects...
...
[INFO] Reactor Summary for two-multi-module 1.0-SNAPSHOT:
[INFO]
[INFO] two-multi-module ................................... SUCCESS [  0.002 s]
[INFO] First Child Project ................................ SUCCESS [  2.570 s]
[INFO] Second Child Project ............................... SUCCESS [  1.679 s]
...
$

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml clean
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] two-multi-module                                                   [pom]
[INFO] First Child Project                                                [jar]
[INFO]
[INFO] ----------------< com.packt.cookbook:two-multi-module >-----------------
[INFO] Building two-multi-module 1.0-SNAPSHOT                             [1/2]
[INFO]   from pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- clean:3.2.0:clean (default-clean) @ two-multi-module ---
[INFO]
[INFO] -------------------< com.packt.cookbook:common-one >--------------------
[INFO] Building First Child Project 1.0-SNAPSHOT                          [2/2]
[INFO]   from common-one/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- clean:3.2.0:clean (default-clean) @ common-one ---
[INFO] Deleting /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/target
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for two-multi-module 1.0-SNAPSHOT:
[INFO]
[INFO] two-multi-module ................................... SUCCESS [  0.177 s]
[INFO] First Child Project ................................ SUCCESS [  0.049 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.309 s
[INFO] Finished at: 2024-02-21T12:53:28Z
[INFO] ------------------------------------------------------------------------
$

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package --projects common-one
[INFO] Scanning for projects...
[INFO]
[INFO] -------------------< com.packt.cookbook:common-one >--------------------
[INFO] Building First Child Project 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ common-one ---
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ common-one ---
[INFO] Changes detected - recompiling the module! :source
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/classes
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ common-one ---
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ common-one ---
[INFO] Changes detected - recompiling the module! :dependency
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/test-classes
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ common-one ---
[INFO] Using auto detected provider org.apache.maven.surefire.junit.JUnit3Provider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.015 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- jar:3.3.0:jar (default-jar) @ common-one ---
[INFO] Building jar: /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/target/common-one-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.170 s
[INFO] Finished at: 2024-02-21T12:57:16Z
[INFO] ------------------------------------------------------------------------
$

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package --projects common-one -am
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] two-multi-module                                                   [pom]
[INFO] First Child Project                                                [jar]
[INFO]
[INFO] ----------------< com.packt.cookbook:two-multi-module >-----------------
[INFO] Building two-multi-module 1.0-SNAPSHOT                             [1/2]
[INFO]   from pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] -------------------< com.packt.cookbook:common-one >--------------------
[INFO] Building First Child Project 1.0-SNAPSHOT                          [2/2]
[INFO]   from common-one/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ common-one ---
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ common-one ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ common-one ---
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter09/04-two-multi-module/common-one/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ common-one ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ common-one ---
[INFO] Using auto detected provider org.apache.maven.surefire.junit.JUnit3Provider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.018 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- jar:3.3.0:jar (default-jar) @ common-one ---
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for two-multi-module 1.0-SNAPSHOT:
[INFO]
[INFO] two-multi-module ................................... SUCCESS [  0.002 s]
[INFO] First Child Project ................................ SUCCESS [  2.615 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.707 s
[INFO] Finished at: 2024-02-21T12:58:34Z
[INFO] ------------------------------------------------------------------------
$

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package --projects common-one -amd

###########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -P dev package -rf dev-two

###########################################################################################

```
