```bash
##################################################################################

$ tree -a .
.
├── pom.xml
├── README.md
└── src
    ├── main
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

12 directories, 5 files
$


##################################################################################

$ cat src/main/resources/app.properties
# POM
display.name=${project.name}
display.url=${project.url}

# System Properties
sun.boot.library.path=${sun.boot.library.path}

# Environment Variables
JAVA_HOME=${env.JAVA_HOME}

# 用户自定义
db.host=${host}
$

##################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X process-resources

##################################################################################

$ cat target/classes/app.properties
# POM
display.name=Project with resource filtering
display.url=http://maven.apache.org

# System Properties
sun.boot.library.path=/opt/java/openjdk/jre/lib/amd64

# Environment Variables
JAVA_HOME=/opt/java/openjdk

# 用户自定义
db.host=${host}
$

##################################################################################

$ mvn -Dhost="192.168.1.1" -s /usr/src/Apache-Maven-Cookbook/settings.xml -X process-resources

##################################################################################

$ cat target/classes/app.properties
# POM
display.name=Project with resource filtering
display.url=http://maven.apache.org

# System Properties
sun.boot.library.path=/opt/java/openjdk/jre/lib/amd64

# Environment Variables
JAVA_HOME=/opt/java/openjdk

# 用户自定义
db.host=192.168.1.1
$

##################################################################################

$ mvn -Dhost="192.168.1.1" -Dproject.name="resource filtering" -s /usr/src/Apache-Maven-Cookbook/settings.xml -X process-resources

##################################################################################

$ cat target/classes/app.properties
# POM
display.name=resource filtering
display.url=http://maven.apache.org

# System Properties
sun.boot.library.path=/opt/java/openjdk/jre/lib/amd64

# Environment Variables
JAVA_HOME=/opt/java/openjdk

# 用户自定义
db.host=192.168.1.1
$

##################################################################################

```
