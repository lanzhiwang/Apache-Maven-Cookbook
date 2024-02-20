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
display.name=Hello ${project.name}
db.host=${host}
$

##################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X process-resources

##################################################################################

$ cat target/classes/app.properties
display.name=Hello Project with resource filtering
db.host=${host}

##################################################################################

$ mvn -Dhost="192.168.1.1" -Dproject.name="resource filtering" process-resources

##################################################################################

$ cat target/classes/app.properties
display.name=Hello resource filtering
db.host=192.168.1.1

##################################################################################

```
