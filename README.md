# Apache-Maven-Cookbook
Apache Maven Cookbook, published by Packt

```bash
docker run -it --rm --name my-maven-project \
-v /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook:/usr/src/Apache-Maven-Cookbook \
-v /Users/huzhi/.m2:/root/.m2 \
-w /usr/src/Apache-Maven-Cookbook \
--network host \
maven:3.9.6-eclipse-temurin-8-focal bash

find . -name .gitignore -exec mv {} {}-bak \;

find Chapter03 -name "*.java" -exec /usr/local/opt/openjdk@11/bin/java -jar format/google-java-format-1.20.0-all-deps.jar -a -i {} \;

```
