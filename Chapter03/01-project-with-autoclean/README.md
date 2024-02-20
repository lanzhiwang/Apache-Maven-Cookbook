```bash
#############################################################################################

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

#############################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml package
[INFO] Scanning for projects...
[INFO]
[INFO] -------------< com.packt.cookbook:project-with-autoclean >--------------
[INFO] Building Project with autoclean 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- clean:2.6:clean (auto-clean) @ project-with-autoclean ---
[INFO] Deleting /usr/src/Apache-Maven-Cookbook/Chapter03/01-project-with-autoclean/target
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ project-with-autoclean ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/01-project-with-autoclean/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ project-with-autoclean ---
[INFO] Changes detected - recompiling the module! :source
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/classes
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ project-with-autoclean ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/01-project-with-autoclean/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ project-with-autoclean ---
[INFO] Changes detected - recompiling the module! :dependency
[WARNING] File encoding has not been set, using platform encoding UTF-8, i.e. build is platform dependent!
[INFO] Compiling 1 source file with javac [debug target 1.8] to target/test-classes
[INFO]
[INFO] --- surefire:3.2.2:test (default-test) @ project-with-autoclean ---
[INFO] Using auto detected provider org.apache.maven.surefire.junit.JUnit3Provider
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.017 s -- in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- jar:3.3.0:jar (default-jar) @ project-with-autoclean ---
[INFO] Building jar: /usr/src/Apache-Maven-Cookbook/Chapter03/01-project-with-autoclean/target/project-with-autoclean-1.0-SNAPSHOT.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.280 s
[INFO] Finished at: 2024-02-20T10:56:26Z
[INFO] ------------------------------------------------------------------------
$

#############################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml initialize
[INFO] Scanning for projects...
[INFO]
[INFO] -------------< com.packt.cookbook:project-with-autoclean >--------------
[INFO] Building Project with autoclean 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- clean:2.6:clean (auto-clean) @ project-with-autoclean ---
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.245 s
[INFO] Finished at: 2024-02-20T10:58:18Z
[INFO] ------------------------------------------------------------------------
$

#############################################################################################

```
