```bash

$ mvn -B archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart -DgroupId=com.packt.cookbook -DartifactId=simple-pom-project -Dversion=1.0-SNAPSHOT -Dpackage=com.packt.cookbook

$ rm -rf simple-pom-project/src

$ tree -a simple-pom-project
simple-pom-project
└── pom.xml

0 directories, 1 file

$ mvn clean package
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------< com.packt.cookbook:simple-pom-project >----------------
[INFO] Building simple-pom-project 1.0-SNAPSHOT
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ simple-pom-project ---
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.219 s
[INFO] Finished at: 2021-10-05T15:21:16+08:00
[INFO] ------------------------------------------------------------------------

$ tree -a .
.
├── README.md
└── pom.xml

0 directories, 2 files






$ mvn clean install
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------< com.packt.cookbook:simple-pom-project >----------------
[INFO] Building simple-pom-project 1.0-SNAPSHOT
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ simple-pom-project ---
[INFO]
[INFO] --- maven-install-plugin:2.5.2:install (default-install) @ simple-pom-project ---
[INFO] Installing /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter10/simple-pom-project/pom.xml to /Users/huzhi/.m2/repository/com/packt/cookbook/simple-pom-project/1.0-SNAPSHOT/simple-pom-project-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.313 s
[INFO] Finished at: 2021-10-05T15:23:05+08:00
[INFO] ------------------------------------------------------------------------
$

$ mvn help:describe -Dcmd=deploy
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------< com.packt.cookbook:simple-pom-project >----------------
[INFO] Building simple-pom-project 1.0-SNAPSHOT
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-help-plugin:3.2.0:describe (default-cli) @ simple-pom-project ---
[INFO] 'deploy' is a phase corresponding to this plugin:
org.apache.maven.plugins:maven-deploy-plugin:2.7:deploy

It is a part of the lifecycle for the POM packaging 'pom'. This lifecycle includes the following phases:
* validate: Not defined
* initialize: Not defined
* generate-sources: Not defined
* process-sources: Not defined
* generate-resources: Not defined
* process-resources: Not defined
* compile: Not defined
* process-classes: Not defined
* generate-test-sources: Not defined
* process-test-sources: Not defined
* generate-test-resources: Not defined
* process-test-resources: Not defined
* test-compile: Not defined
* process-test-classes: Not defined
* test: Not defined
* prepare-package: Not defined
* package: Not defined
* pre-integration-test: Not defined
* integration-test: Not defined
* post-integration-test: Not defined
* verify: Not defined
* install: org.apache.maven.plugins:maven-install-plugin:2.4:install
* deploy: org.apache.maven.plugins:maven-deploy-plugin:2.7:deploy

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.512 s
[INFO] Finished at: 2021-10-05T15:26:13+08:00
[INFO] ------------------------------------------------------------------------
$



$ mvn clean compiler:compile compiler:testCompile surefire:test jar:jar

$ tree -a .
.
├── README.md
├── pom.xml
└── target
    ├── maven-archiver
    │   └── pom.properties
    └── simple-pom-project-1.0-SNAPSHOT.jar

2 directories, 4 files
$

```
