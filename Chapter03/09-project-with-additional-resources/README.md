```bash
#################################################################################

$ tree -a .
.
├── pom.xml
├── README.md
└── src
    ├── main
    │   ├── additional
    │   │   └── additional.properties
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

13 directories, 6 files
$

#################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X package

#################################################################################

$ tree -a target
target
├── classes
│   ├── additional.properties
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
├── project-with-additional-resources-1.0-SNAPSHOT.jar
├── surefire
│   ├── surefire_0-20240220095834142_2tmp
│   ├── surefire_0-20240220095840846_2tmp
│   ├── surefire_0-20240220095909478_2tmp
│   ├── surefire-20240220095834142_1tmp
│   ├── surefire-20240220095840846_1tmp
│   ├── surefire-20240220095909478_1tmp
│   ├── surefirebooter-20240220095834142_3.jar
│   ├── surefirebooter-20240220095840846_3.jar
│   └── surefirebooter-20240220095909478_3.jar
├── surefire-reports
│   ├── 2024-02-20T09-58-34_030-jvmRun1-commands.bin
│   ├── 2024-02-20T09-58-34_030-jvmRun1-events.bin
│   ├── 2024-02-20T09-58-40_735-jvmRun1-commands.bin
│   ├── 2024-02-20T09-58-40_735-jvmRun1-events.bin
│   ├── 2024-02-20T09-59-09_373-jvmRun1-commands.bin
│   ├── 2024-02-20T09-59-09_373-jvmRun1-events.bin
│   ├── com.packt.cookbook.AppTest.txt
│   └── TEST-com.packt.cookbook.AppTest.xml
└── test-classes
    └── com
        └── packt
            └── cookbook
                └── AppTest.class

21 directories, 27 files
$

#################################################################################

$ jar -xvf project-with-additional-resources-1.0-SNAPSHOT.jar
  created: META-INF/
 inflated: META-INF/MANIFEST.MF
  created: com/
  created: com/packt/
  created: com/packt/cookbook/
  created: META-INF/maven/
  created: META-INF/maven/com.packt.cookbook/
  created: META-INF/maven/com.packt.cookbook/project-with-additional-resources/
 inflated: additional.properties
 inflated: app.properties
 inflated: com/packt/cookbook/App.class
 inflated: META-INF/maven/com.packt.cookbook/project-with-additional-resources/pom.xml
 inflated: META-INF/maven/com.packt.cookbook/project-with-additional-resources/pom.properties

#################################################################################

$ ll
total 12
drwxr-xr-x 7 root root  224 Feb 20 10:03 ./
drwxr-xr-x 7 root root  224 Feb 20 10:01 ../
-rw-r--r-- 1 root root   32 Feb 20 09:58 additional.properties
-rw-r--r-- 1 root root   25 Feb 20 09:58 app.properties
drwxr-xr-x 3 root root   96 Feb 20 09:58 com/
drwxr-xr-x 4 root root  128 Feb 20 09:58 META-INF/
-rw-r--r-- 1 root root 2777 Feb 20 10:02 project-with-additional-resources-1.0-SNAPSHOT.jar

#################################################################################

$ tree -a .
.
├── additional.properties
├── app.properties
├── com
│   └── packt
│       └── cookbook
│           └── App.class
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── project-with-additional-resources
│               ├── pom.properties
│               └── pom.xml
└── project-with-additional-resources-1.0-SNAPSHOT.jar

7 directories, 7 files
$

#################################################################################

```
