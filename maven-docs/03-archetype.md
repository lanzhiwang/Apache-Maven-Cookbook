# 生成项目骨架 archetype

```bash
$ mvn help:describe -Dplugin=org.apache.maven.plugins:maven-archetype-plugin -Ddetail=true
Name: Maven Archetype Plugin
Description: Maven Archetype is a set of tools to deal with archetypes, i.e.
  an abstract representation of a kind of project that can be instantiated into
  a concrete customized Maven project. An archetype knows which files will be
  part of the instantiated project and which properties to fill to properly
  customize the project.
Group Id: org.apache.maven.plugins
Artifact Id: maven-archetype-plugin
Version: 3.2.1
Goal Prefix: archetype

This plugin has 7 goals:

archetype:crawl
archetype:create-from-project
archetype:generate
archetype:integration-test
archetype:jar
archetype:update-local-catalog

################################################################################

# 查看有哪些模板
$ mvn archetype:generate | more
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------< org.apache.maven:standalone-pom >-------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] >>> maven-archetype-plugin:3.2.0:generate (default-cli) > generate-sources @ standalone-pom >>>
[INFO]
[INFO] <<< maven-archetype-plugin:3.2.0:generate (default-cli) < generate-sources @ standalone-pom <<<
[INFO]
[INFO]
[INFO] --- maven-archetype-plugin:3.2.0:generate (default-cli) @ standalone-pom ---
[INFO] Generating project in Interactive mode
[INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0)
Choose archetype:
1: remote -> am.ik.archetype:elm-spring-boot-blank-archetype (Blank multi project for Spring Boot + Elm)
2: remote -> am.ik.archetype:graalvm-blank-archetype (Blank project for GraalVM)
3: remote -> am.ik.archetype:graalvm-springmvc-blank-archetype (Blank project for GraalVM + Spring MVC)

################################################################################

# 使用一个具体的模板生成项目骨架
$ mvn archetype:generate -DarchetypeGroupId=am.ik.archetype -DarchetypeArtifactId=elm-spring-boot-blank-archetype

################################################################################

org.apache.maven.archetypes:maven-archetype-archetype
org.apache.maven.archetypes:maven-archetype-j2ee-simple
org.apache.maven.archetypes:maven-archetype-marmalade-mojo
org.apache.maven.archetypes:maven-archetype-mojo
org.apache.maven.archetypes:maven-archetype-plugin
org.apache.maven.archetypes:maven-archetype-plugin-site
org.apache.maven.archetypes:maven-archetype-portlet
org.apache.maven.archetypes:maven-archetype-profiles
org.apache.maven.archetypes:maven-archetype-quickstart
org.apache.maven.archetypes:maven-archetype-simple
org.apache.maven.archetypes:maven-archetype-site
org.apache.maven.archetypes:maven-archetype-site-simple
org.apache.maven.archetypes:maven-archetype-site-skin
org.apache.maven.archetypes:maven-archetype-webapp

################################################################################

$ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.0

$ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-webapp

################################################################################

org.appfuse:appfuse-basic-jsf
org.appfuse:appfuse-basic-spring
org.appfuse:appfuse-basic-struts
org.appfuse:appfuse-basic-tapestry
org.appfuse:appfuse-core
org.appfuse:appfuse-modular-jsf
org.appfuse:appfuse-modular-spring
org.appfuse:appfuse-modular-struts
org.appfuse:appfuse-modular-tapestry

################################################################################

$ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-archetype
$ tree -a .
.
└── mvn1
    ├── pom.xml
    └── src
        ├── main
        │   └── resources
        │       ├── META-INF
        │       │   └── maven
        │       │       └── archetype-metadata.xml
        │       └── archetype-resources
        │           ├── pom.xml
        │           └── src
        │               ├── main
        │               │   └── java
        │               │       └── App.java
        │               └── test
        │                   └── java
        │                       └── AppTest.java
        └── test
            └── resources
                └── projects
                    └── it-basic
                        ├── archetype.properties
                        └── goal.txt

16 directories, 7 files
$

################################################################################

$ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-j2ee-simple
$ tree -a .
.
└── mvn2
    ├── ear
    │   ├── pom.xml
    │   └── src
    │       ├── main
    │       │   └── java
    │       └── test
    │           └── java
    ├── ejbs
    │   ├── pom.xml
    │   └── src
    │       ├── main
    │       │   ├── java
    │       │   └── resources
    │       │       └── META-INF
    │       │           └── ejb-jar.xml
    │       └── test
    │           └── java
    ├── pom.xml
    ├── primary-source
    │   ├── pom.xml
    │   └── src
    │       ├── main
    │       │   └── java
    │       └── test
    │           └── java
    ├── projects
    │   ├── logging
    │   │   ├── pom.xml
    │   │   └── src
    │   │       ├── main
    │   │       │   └── java
    │   │       └── test
    │   │           └── java
    │   └── pom.xml
    └── servlets
        ├── pom.xml
        └── servlet
            ├── pom.xml
            └── src
                ├── main
                │   ├── java
                │   └── webapp
                │       ├── WEB-INF
                │       │   └── web.xml
                │       └── index.jsp
                └── test
                    └── java

37 directories, 11 files
$

################################################################################

$ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-marmalade-mojo
$ tree -a .
.
└── mvn3
    ├── pom.xml
    └── src
        └── main
            ├── java
            │   └── com
            │       └── lanzhiwang
            │           ├── CopyFileTag.java
            │           └── MyMojoTagLibrary.java
            └── resources
                ├── META-INF
                │   └── marmalade
                │       └── myMojo.def
                └── myMojo.mmld

9 directories, 5 files
$

################################################################################

$ mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-mojo -DgroupId=com.lanzhiwang -DartifactId=mvn4 -Dversion=1.0-SNAPSHOT -Dpackage=com.lanzhiwang
$ tree -a .
.
└── mvn4
    ├── pom.xml
    └── src
        └── main
            └── java
                └── com
                    └── lanzhiwang
                        └── MyMojo.java

6 directories, 2 files
$

################################################################################

$ mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-plugin -DgroupId=com.lanzhiwang -DartifactId=mvn5 -Dversion=1.0-SNAPSHOT -Dpackage=com.lanzhiwang
$ tree -a .
.
└── mvn5
    ├── pom.xml
    └── src
        ├── it
        │   ├── settings.xml
        │   └── simple-it
        │       ├── pom.xml
        │       └── verify.groovy
        ├── main
        │   └── java
        │       └── com
        │           └── lanzhiwang
        │               └── MyMojo.java
        └── test
            ├── java
            │   └── com
            │       └── lanzhiwang
            │           └── MyMojoTest.java
            └── resources
                └── project-to-test
                    └── pom.xml

14 directories, 7 files
$

################################################################################

$ mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.packt.cookbook -DartifactId=project-with-source-code -Dversion=1.0-SNAPSHOT -Dpackage=com.packt.cookbook

$ tree -a simple-project
simple-project
├── pom.xml
└── src
    ├── main
    │   ├── java
    │   │   └── com
    │   │       └── packt
    │   │           └── cookbook
    │   │               └── App.java
    │   └── resources
    │       ├── m
    │       │   └── p2.xml
    │       └── p.xml
    └── test
        ├── java
        │   └── com
        │       └── packt
        │           └── cookbook
        │               └── AppTest.java
        └── resources
            └── ptest.xml

14 directories, 6 files
$

$ tree -a target
target
├── classes
│   ├── com
│   │   └── packt
│   │       └── cookbook
│   │           └── App.class
│   ├── m
│   │   └── p2.xml
│   └── p.xml
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
├── simple-project-1.0-SNAPSHOT.jar
├── surefire-reports
│   ├── TEST-com.packt.cookbook.AppTest.xml
│   └── com.packt.cookbook.AppTest.txt
└── test-classes
    ├── com
    │   └── packt
    │       └── cookbook
    │           └── AppTest.class
    └── ptest.xml

21 directories, 13 files
$

$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── simple-project
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
├── m
│   └── p2.xml
├── p.xml
└── simple-project-1.0-SNAPSHOT.jar

8 directories, 7 files
$

################################################################################

$ mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-webapp -DgroupId=com.packt.cookbook -DartifactId=simple-webapp -Dversion=1.0-SNAPSHOT -Dpackage=com.packt.cookbook

$ tree -a simple-webapp
simple-webapp
├── pom.xml
└── src
    └── main
        └── webapp
            ├── WEB-INF
            │   └── web.xml
            └── index.jsp

4 directories, 3 files
$

################################################################################

$ mvn -B archetype:generate -DarchetypeGroupId=org.wildfly.archetype -DarchetypeArtifactId=wildfly-javaee7-webapp-ear-archetype -DgroupId=com.packt.cookbook -DartifactId=simple-ear -Dversion=1.0-SNAPSHOT -Dpackage=com.packt.cookbook

$ tree -a simple-ear
simple-ear
├── README.md
├── pom.xml
├── simple-ear-ear
│   ├── pom.xml
│   └── src
│       └── main
│           └── application
│               └── META-INF
│                   └── simple-ear-ds.xml
├── simple-ear-ejb
│   ├── pom.xml
│   └── src
│       ├── main
│       │   ├── java
│       │   │   └── com
│       │   │       └── packt
│       │   │           └── cookbook
│       │   │               ├── data
│       │   │               │   ├── MemberListProducer.java
│       │   │               │   └── MemberRepository.java
│       │   │               ├── model
│       │   │               │   └── Member.java
│       │   │               ├── service
│       │   │               │   └── MemberRegistration.java
│       │   │               └── util
│       │   │                   └── Resources.java
│       │   └── resources
│       │       ├── META-INF
│       │       │   ├── beans.xml
│       │       │   └── persistence.xml
│       │       └── import.sql
│       └── test
│           ├── java
│           │   └── com
│           │       └── packt
│           │           └── cookbook
│           │               └── test
│           │                   └── MemberRegistrationTest.java
│           └── resources
│               ├── META-INF
│               │   └── test-persistence.xml
│               ├── arquillian.xml
│               └── test-ds.xml
└── simple-ear-web
    ├── pom.xml
    └── src
        ├── main
        │   ├── java
        │   │   └── com
        │   │       └── packt
        │   │           └── cookbook
        │   │               ├── controller
        │   │               │   └── MemberController.java
        │   │               ├── rest
        │   │               │   ├── JaxRsActivator.java
        │   │               │   └── MemberResourceRESTService.java
        │   │               └── util
        │   │                   └── WebResources.java
        │   └── webapp
        │       ├── WEB-INF
        │       │   ├── beans.xml
        │       │   ├── faces-config.xml
        │       │   └── templates
        │       │       └── default.xhtml
        │       ├── index.html
        │       ├── index.xhtml
        │       └── resources
        │           ├── css
        │           │   └── screen.css
        │           └── gfx
        │               ├── asidebkg.png
        │               ├── bkg-blkheader.png
        │               ├── dualbrand_logo.png
        │               ├── headerbkg.png
        │               └── wildfly_400x130.jpg
        └── test
            └── java

44 directories, 33 files
$

################################################################################

mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.packt.cookbook -DartifactId=project-with-exec -Dversion=1.0-SNAPSHOT -Dpackage=com.packt.cookbook

################################################################################

mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.lanzhiwang.producer -DartifactId=kafka-producer -Dversion=1.0-SNAPSHOT -Dpackage=com.lanzhiwang.producer

################################################################################

mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.lanzhiwang.consumer -DartifactId=kafka-consumer -Dversion=1.0-SNAPSHOT -Dpackage=com.lanzhiwang.consumer



```

