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
    ├── project-with-one-jar-1.0-SNAPSHOT.jar
    ├── project-with-one-jar-1.0-SNAPSHOT.one-jar.jar
    ├── surefire-reports
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   └── com.packt.cookbook.AppTest.txt
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

32 directories, 15 files

$ java -jar target/project-with-one-jar-1.0-SNAPSHOT.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/slf4j/LoggerFactory
	at com.packt.cookbook.App.main(App.java:13)
Caused by: java.lang.ClassNotFoundException: org.slf4j.LoggerFactory
	at java.net.URLClassLoader.findClass(URLClassLoader.java:382)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:352)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
	... 1 more

$ java -jar target/project-with-one-jar-1.0-SNAPSHOT.one-jar.jar
[main] INFO com.packt.cookbook.App - Hello World


$ tree -a jar
jar
├── .version
├── META-INF
│   └── MANIFEST.MF
├── OneJar.class
├── com
│   └── simontuffs
│       └── onejar
│           ├── Boot$1.class
│           ├── Boot$2.class
│           ├── Boot$3.class
│           ├── Boot.class
│           ├── Handler$1.class
│           ├── Handler.class
│           ├── IProperties.class
│           ├── JarClassLoader$1.class
│           ├── JarClassLoader$2.class
│           ├── JarClassLoader$ByteCode.class
│           ├── JarClassLoader$FileURLFactory$1.class
│           ├── JarClassLoader$FileURLFactory.class
│           ├── JarClassLoader$IURLFactory.class
│           ├── JarClassLoader$OneJarURLFactory.class
│           ├── JarClassLoader.class
│           ├── OneJarFile$1.class
│           ├── OneJarFile$2.class
│           ├── OneJarFile.class
│           └── OneJarURLConnection.class
├── doc
│   └── one-jar-license.txt
├── lib
│   ├── slf4j-api-1.7.9.jar
│   └── slf4j-simple-1.7.9.jar
├── main
│   └── project-with-one-jar-1.0-SNAPSHOT.jar
├── project-with-one-jar-1.0-SNAPSHOT.one-jar.jar
└── src
    ├── OneJar.java
    └── com
        └── simontuffs
            └── onejar
                ├── Boot.java
                ├── Handler.java
                ├── IProperties.java
                ├── JarClassLoader.java
                ├── OneJarFile.java
                └── OneJarURLConnection.java

11 directories, 34 files

```
