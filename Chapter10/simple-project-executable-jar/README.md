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

$ java -jar target/simple-project-executable-jar-1.0-SNAPSHOT.jar
target/simple-project-executable-jar-1.0-SNAPSHOT.jar中没有主清单属性


$ mvn clean package

$ java -jar target/simple-project-executable-jar-1.0-SNAPSHOT.jar
Hello World!


$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── simple-project-executable-jar
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
└── simple-project-executable-jar-1.0-SNAPSHOT.jar

7 directories, 5 files

$ cat jar/META-INF/MANIFEST.MF
Manifest-Version: 1.0
Built-By: huzhi
Created-By: Apache Maven 3.6.3
Build-Jdk: 1.8.0_275
Main-Class: com.packt.cookbook.App

$

```
