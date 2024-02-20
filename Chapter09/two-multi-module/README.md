```bash

$ tree -a .
.
├── README.md
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
└── pom.xml

30 directories, 16 files
$


$ mvn clean test
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] two-multi-module                                                   [pom]
[INFO] First Child Project                                                [jar]


$ mvn -P dev clean test
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] two-multi-module                                                   [pom]
[INFO] First Child Project                                                [jar]
[INFO] Second Child Project                                               [jar]

```