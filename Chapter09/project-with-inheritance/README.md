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
│       └── test
│           └── java
│               └── com
│                   └── packt
│                       └── cookbook
│                           └── AppTest.java
└── pom.xml

12 directories, 4 files
$




$ pwd
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-inheritance

$ mvn clean package

$ tree -a .
.
├── README.md
├── child
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

12 directories, 5 files
$


$ pwd
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-inheritance/child

$ mvn clean package

$ tree -a ~/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-inheritance
/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter09/project-with-inheritance
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
│   │   └── test
│   │       └── java
│   │           └── com
│   │               └── packt
│   │                   └── cookbook
│   │                       └── AppTest.java
│   └── target
│       ├── child-1.0-SNAPSHOT.jar
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


