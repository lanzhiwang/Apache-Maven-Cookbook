```bash

$ tree -a .
.
├── README.md
├── pom.xml
└── src
    └── main
        └── webapp
            ├── WEB-INF
            │   └── web.xml
            └── index.jsp

4 directories, 4 files
$

$ mvn clean package

$ tree -a .
.
├── README.md
├── pom.xml
├── src
│   └── main
│       └── webapp
│           ├── WEB-INF
│           │   └── web.xml
│           └── index.jsp
└── target
    ├── maven-archiver
    │   └── pom.properties
    ├── simple-webapp
    │   ├── META-INF
    │   ├── WEB-INF
    │   │   ├── classes
    │   │   └── web.xml
    │   └── index.jsp
    └── simple-webapp.war

10 directories, 8 files
$

$ mvn help:describe -Dcmd=war:exploded -Ddetail

$ mvn war:exploded
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------< com.packt.cookbook:simple-webapp >------------------
[INFO] Building simple-webapp Maven Webapp 1.0-SNAPSHOT
[INFO] --------------------------------[ war ]---------------------------------
[INFO]
[INFO] --- maven-war-plugin:3.2.2:exploded (default-cli) @ simple-webapp ---
[INFO] Exploding webapp
[INFO] Assembling webapp [simple-webapp] in [/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-webapp/target/simple-webapp]
[INFO] Processing war project
[INFO] Copying webapp resources [/Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-webapp/src/main/webapp]
[INFO] Webapp assembled in [18 msecs]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.543 s
[INFO] Finished at: 2021-10-05T15:00:06+08:00
[INFO] ------------------------------------------------------------------------

$ tree -a .
.
├── README.md
├── pom.xml
├── src
│   └── main
│       └── webapp
│           ├── WEB-INF
│           │   └── web.xml
│           └── index.jsp
└── target
    └── simple-webapp
        ├── META-INF
        ├── WEB-INF
        │   ├── classes
        │   └── web.xml
        └── index.jsp

9 directories, 6 files
$ mvn help:describe -Dcmd=package -Ddetail

```
