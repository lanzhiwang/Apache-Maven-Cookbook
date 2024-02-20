$ mvn test
[INFO] Scanning for projects...
[INFO]
[INFO] ----------------< com.packt.cookbook:project-with-test >----------------
[INFO] Building project-with-test 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-resources-plugin:3.0.2:resources (default-resources) @ project-with-test ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter03/project-with-test/src/main/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.8.0:compile (default-compile) @ project-with-test ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter03/project-with-test/target/classes
[INFO]
[INFO] --- maven-resources-plugin:3.0.2:testResources (default-testResources) @ project-with-test ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter03/project-with-test/src/test/resources
[INFO]
[INFO] --- maven-compiler-plugin:3.8.0:testCompile (default-testCompile) @ project-with-test ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter03/project-with-test/target/test-classes
[INFO]
[INFO] --- maven-surefire-plugin:2.22.1:test (default-test) @ project-with-test ---
[INFO]
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.packt.cookbook.AppTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.019 s - in com.packt.cookbook.AppTest
[INFO]
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.555 s
[INFO] Finished at: 2021-10-04T19:43:11+08:00
[INFO] ------------------------------------------------------------------------
$


$ tree -a target
target
├── classes
│   └── com
│       └── packt
│           └── cookbook
│               └── App.class
├── generated-sources
│   └── annotations
├── generated-test-sources
│   └── test-annotations
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
├── surefire-reports
│   ├── TEST-com.packt.cookbook.AppTest.xml
│   └── com.packt.cookbook.AppTest.txt
└── test-classes
    └── com
        └── packt
            └── cookbook
                └── AppTest.class

19 directories, 8 files
$

