# Guide to Configuring Plug-ins

## Introduction

In Maven, there are two kinds of plugins, build and reporting:

- **Build plugins** are executed during the build and configured in the `<build/>` element.

- **Reporting plugins** are executed during the site generation and configured in the `<reporting/>` element.

All plugins should have minimal required [information](https://maven.apache.org/ref/current/maven-model/maven.html#class_plugin): `groupId`, `artifactId` and `version`.

**Important Note**: Always define each version of the plugins used by the build to guarantee the build reproducibility. A good practice is to specify them in the `<build><pluginManagement/></build>` elements for each build plugins. (Generally, you will define a `<pluginManagement/>` element in a parent POM.) For reporting plugins, specify each version in the `<reporting><plugins/></reporting>` elements (and surely in the `<build><pluginManagement/></build>` elements too).  重要说明：始终定义构建使用的插件的每个版本，以保证构建的可重现性。 一个好的做法是在每个构建插件的 `<build><pluginManagement/></build>` 元素中指定它们。 （通常，您将在父 POM 中定义一个 `<pluginManagement/>` 元素。）对于报告插件，在 `<reporting><plugins/></reporting>` 元素中指定每个版本（当然在 `<build><pluginManagement/></build>` 元素）。

## Generic Configuration

Maven plugins (build and reporting) are configured by specifying a `<configuration>` element where the child elements of the `<configuration>` element are mapped to fields, or setters, inside your Mojo. (**Remember that a plug-in consists of one or more Mojos where a Mojo maps to a goal**.) Say, for example, you have a Mojo that performs a query against a particular URL, with a specified timeout and list of options. The Mojo might look like the following:  Maven 插件（构建和报告）是通过指定一个 `<configuration>` 元素来配置的，其中 `<configuration>` 元素的子元素被映射到你的 Mojo 中的字段或设置器。 （请记住，插件由一个或多个 Mojo 组成，其中一个 Mojo 映射到一个目标。）例如，您有一个 Mojo，它对特定 URL 执行查询，具有指定的超时和选项列表。 Mojo 可能如下所示：


```java
/**
 * @goal query
 */
public class MyQueryMojo extends AbstractMojo {
    @Parameter(property = "query.url", required = true)
    private String url;

    @Parameter(property = "timeout", required = false, defaultValue = "50")
    private int timeout;

    @Parameter(property = "options")
    private String[] options;

    public void execute() throws MojoExecutionException {
        ...
    }
}
```

To configure the Mojo from your POM with the desired URL, timeout and options you might have something like the following:  要使用所需的 URL、超时和选项从您的 POM 配置 Mojo，您可能有以下内容：

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-myquery-plugin</artifactId>
        <version>1.0</version>
        <configuration>
          <url>http://www.foobar.com/query</url>
          <timeout>10</timeout>
          <options>
            <option>one</option>
            <option>two</option>
            <option>three</option>
          </options>
        </configuration>
      </plugin>
    </plugins>
  </build>
  ...
</project>

```

The elements in the configuration match the names of the fields in the Mojo. The mapping is straight forward, the `url` element maps to the `url` field, the `timeout` element maps to the `timeout` field and the `options` element maps to the `options` field. The mapping mechanism can deal with arrays by inspecting the type of the field and determining if a suitable mapping is possible.  配置中的元素与 Mojo 中的字段名称相匹配。 映射很简单，url 元素映射到 url 字段，timeout 元素映射到 timeout 字段，options 元素映射到 options 字段。 映射机制可以通过检查字段的类型并确定是否可能进行合适的映射来处理数组。

For Mojos that are intended to be executed directly from the CLI, their parameters usually provide a means to be configured via system properties instead of a `<configuration>` section in the POM. The plugin documentation for those parameters will list an *expression* that denotes the system properties for the configuration. In the Mojo above, the parameter `url` is associated with the expression `${query.url}`, meaning its value can be specified by the system property `query.url` as shown below:  对于打算直接从 CLI 执行的 Mojo，它们的参数通常提供一种通过系统属性而不是 POM 中的 `<configuration>` 部分进行配置的方法。 这些参数的插件文档将列出一个表示配置的系统属性的表达式。 在上面的 Mojo 中，参数 url 与表达式 ${query.url} 相关联，这意味着它的值可以由系统属性 query.url 指定，如下所示：

```bash
mvn myquery:query -Dquery.url=http://maven.apache.org
```

The name of the system property does not necessarily match the name of the mojo parameter. While this is a rather common practice, you will often notice plugins that employ some prefix for the system properties to avoid name clashes with other system properties. Though rarely, there are also plugin parameters that (e.g. for historical reasons) employ system properties which are completely unrelated to the parameter name. So be sure to have a close look at the plugin documentation.  系统属性的名称不一定与 mojo 参数的名称匹配。 虽然这是一种相当普遍的做法，但您经常会注意到插件为系统属性使用了一些前缀，以避免与其他系统属性的名称冲突。 虽然很少，但也有插件参数（例如出于历史原因）使用与参数名称完全无关的系统属性。 所以一定要仔细查看插件文档。

### Help Goal

Most Maven plugins have a `help` goal that prints a description of the plugin and its parameters and types. For instance, to see help for the javadoc goal, type:

```bash
mvn javadoc:help -Ddetail -Dgoal=javadoc
```

And you will see all parameters for the javadoc:javadoc goal, similar to this [page](https://maven.apache.org/plugins/maven-javadoc-plugin/javadoc-mojo.html).

#### Configuring Parameters

##### Mapping Simple Objects

Mapping simple types, like Boolean or Integer, is very simple. The `<configuration>` element might look like the following:

```xml
...
<configuration>
  <myString>a string</myString>
  <myBoolean>true</myBoolean>
  <myInteger>10</myInteger>
  <myDouble>1.0</myDouble>
  <myFile>c:\temp</myFile>
  <myURL>http://maven.apache.org</myURL>
</configuration>
...
```

##### Mapping Complex Objects

Mapping complex types is also fairly straight forward. Let's look at a simple example where we are trying to map a configuration for Person object. The `<configuration/>` element might look like the following:  映射复杂类型也相当简单。 让我们看一个简单的例子，我们试图为 Person 对象映射一个配置。 <configuration/> 元素可能如下所示：

```xml
...
<configuration>
  <person>
    <firstName>Jason</firstName>
    <lastName>van Zyl</lastName>
  </person>
</configuration>
...
```

The rules for mapping complex objects are as follows:  映射复杂对象的规则如下：

- There must be a private field that corresponds to name of the element being mapped. So in our case the `person` element must map to a `person` field in the mojo.  必须有一个与被映射元素的名称相对应的私有字段。 所以在我们的例子中，person 元素必须映射到 mojo 中的 person 字段。

- The object instantiated must be in the same package as the Mojo itself. So if your mojo is in `com.mycompany.mojo.query` then the mapping mechanism will look in that package for an object named `Person`. The mechanism capitalizes the first letter of the element name and uses that to search for the object to instantiate.  实例化的对象必须与 Mojo 本身在同一个包中。 因此，如果您的 mojo 在 com.mycompany.mojo.query 中，那么映射机制将在该包中查找名为 Person 的对象。 该机制将元素名称的第一个字母大写，并使用它来搜索要实例化的对象。

- If you wish to have the object to be instantiated live in a different package or have a more complicated name, specify this using an `implementation` attribute like the following:  如果您希望在不同的包中实例化对象或使用更复杂的名称，请使用如下实现属性指定：


```xml
...
<configuration>
  <person implementation="com.mycompany.mojo.query.SuperPerson">
    <firstName>Jason</firstName>
    <lastName>van Zyl</lastName>
  </person>
</configuration>
...
```


##### Mapping Collections

The configuration mapping mechanism can easily deal with most collections so let's go through a few examples to show you how it's done:

###### Mapping Lists

Mapping lists works in much the same way as mapping to arrays where you a list of elements will be mapped to the List. So if you have a mojo like the following:

```java
public class MyAnimalMojo extends AbstractMojo {
    @Parameter(property = "animals")
    private List animals;
 
    public void execute() throws MojoExecutionException {
        ...
    }
}
```

Where you have a field named `animals` then your configuration for the plug-in would look like the following:

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-myanimal-plugin</artifactId>
        <version>1.0</version>
        <configuration>
          <animals>
            <animal>cat</animal>
            <animal>dog</animal>
            <animal>aardvark</animal>
          </animals>
        </configuration>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

Where each of the animals listed would be entries in the `animals` field. Unlike arrays, collections have no specific component type. In order to derive the type of a list item, the following strategy is used:  列出的每只动物都是动物字段中的条目。 与数组不同，集合没有特定的组件类型。 为了导出列表项的类型，使用以下策略：

1. If the XML element contains an `implementation` hint attribute, that is used  如果 XML 元素包含实现提示属性，则使用

2. If the XML tag contains a `.`, try that as a fully qualified class name  如果 XML 标记包含 .，请尝试将其作为完全限定的类名

3. Try the XML tag (with capitalized first letter) as a class in the same package as the mojo/object being configured  尝试将 XML 标记（首字母大写）作为与正在配置的 mojo/object 相同的包中的类

4. If the element has no children, assume its type is `String`. Otherwise, the configuration will fail.  如果元素没有子元素，则假定其类型为 String。 否则，配置将失败。


###### Mapping Maps

In the same way, you could define maps like the following:

```java
...
    @Parameter(property = "myMap")
    private Map myMap;
...
```

```xml
...
  <configuration>
    <myMap>
      <key1>value1</key1>
      <key2>value2</key2>
    </myMap>
  </configuration>
...
```


###### Mapping Properties

Properties should be defined like the following:

```java
...
    @Parameter(property = "myProperties")
    private Properties myProperties;
...
```

```xml
...
  <configuration>
    <myProperties>
      <property>
        <name>propertyName1</name>
        <value>propertyValue1</value>
      </property>
      <property>
        <name>propertyName2</name>
        <value>propertyValue2</value>
      </property>
    </myProperties>
  </configuration>
...
```

## Configuring Build Plugins

The following is only to configure Build plugins in the `<build>` element.

### Using the `<executions>` Tag

You can also configure a mojo using the `<executions>` tag. This is most commonly used for mojos that are intended to participate in some phases of the [build lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html). Using `MyQueryMojo` as an example, you may have something that will look like:  您还可以使用 `<executions>` 标签配置 mojo。 这最常用于旨在参与构建生命周期某些阶段的 mojo。 以 MyQueryMojo 为例，您可能会看到如下所示的内容：


```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-myquery-plugin</artifactId>
        <version>1.0</version>
        <executions>
          <execution>
            <id>execution1</id>
            <phase>test</phase>
            <configuration>
              <url>http://www.foo.com/query</url>
              <timeout>10</timeout>
              <options>
                <option>one</option>
                <option>two</option>
                <option>three</option>
              </options>
            </configuration>
            <goals>
              <goal>query</goal>
            </goals>
          </execution>
          <execution>
            <id>execution2</id>
            <configuration>
              <url>http://www.bar.com/query</url>
              <timeout>15</timeout>
              <options>
                <option>four</option>
                <option>five</option>
                <option>six</option>
              </options>
            </configuration>
            <goals>
              <goal>query</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

The first execution with id "execution1" binds this configuration to the test phase. The second execution does not have a `<phase>` tag, how do you think will this execution behave? Well, goals can have a default phase binding as discussed further below. If the goal has a default phase binding then it will execute in that phase. But if the goal is not bound to any lifecycle phase then it simply won't be executed during the build lifecycle.  id 为“execution1”的第一次执行将此配置绑定到测试阶段。 第二次执行没有 `<phase>` 标签，您认为这次执行的表现如何？ 好吧，目标可以有一个默认的阶段绑定，如下文进一步讨论的。 如果目标具有默认阶段绑定，则它将在该阶段执行。 但是如果目标没有绑定到任何生命周期阶段，那么它就不会在构建生命周期中执行。

Note that while execution id's have to be unique among all executions of a single plugin within a POM, they don't have to be unique across an inheritance hierarchy of POMs. Executions of the same id from different POMs are merged. The same applies to executions that are defined by profiles.  请注意，虽然执行 id 在 POM 内单个插件的所有执行中必须是唯一的，但它们在 POM 的继承层次结构中不必是唯一的。 来自不同 POM 的相同 id 的执行被合并。 这同样适用于由配置文件定义的执行。

How about if we have a multiple executions with different phases bound to it? How do you think will it behave? Let us use the example POM above again, but this time we shall bind `execution2` to a phase.  如果我们有多个不同阶段绑定到它的执行怎么办？ 你认为它会如何表现？ 让我们再次使用上面的示例 POM，但这次我们将 execution2 绑定到一个阶段。

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        ...
        <executions>
          <execution>
            <id>execution1</id>
            <phase>test</phase>
            ...
          </execution>
          <execution>
            <id>execution2</id>
            <phase>install</phase>
            <configuration>
              <url>http://www.bar.com/query</url>
              <timeout>15</timeout>
              <options>
                <option>four</option>
                <option>five</option>
                <option>six</option>
              </options>
            </configuration>
            <goals>
              <goal>query</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

If there are multiple executions bound to different phases, then the mojo is executed once for each phase indicated. Meaning, `execution1` will be executed applying the configuration setup when the phase of the build is test, and `execution2` will be executed applying the configuration setup when the build phase is already in install.  如果有多个执行绑定到不同的阶段，那么针对每个指定的阶段执行一次 mojo。 这意味着，当构建阶段是测试时，将应用配置设置执行 execution1，当构建阶段已经安装时，将应用配置设置执行 execution2。

Now, let us have another mojo example which shows a default lifecycle phase binding.  现在，让我们有另一个 mojo 示例，它显示了默认的生命周期阶段绑定。

```java
/**
 * @goal query
 * @phase package
 */
public class MyBoundQueryMojo extends AbstractMojo {
    @Parameter(property = "query.url", required = true)
    private String url;
 
    @Parameter(property = "timeout", required = false, defaultValue = "50")
    private int timeout;
 
    @Parameter(property = "options")
    private String[] options;
 
    public void execute() throws MojoExecutionException {
        ...
    }
}
```

From the above mojo example, `MyBoundQueryMojo` is by default bound to the package phase (see the `@phase` notation). But if we want to execute this mojo during the install phase and not with package we can rebind this mojo into a new lifecycle phase using the `<phase>` tag under `<execution>`.  在上面的 mojo 示例中，默认情况下 MyBoundQueryMojo 绑定到包阶段（请参阅@phase 表示法）。 但是如果我们想在安装阶段执行这个 mojo 而不是包，我们可以使用 `<execution>` 下的 `<phase>` 标签将这个 mojo 重新绑定到新的生命周期阶段。

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-myquery-plugin</artifactId>
        <version>1.0</version>
        <executions>
          <execution>
            <id>execution1</id>
            <phase>install</phase>
            <configuration>
              <url>http://www.bar.com/query</url>
              <timeout>15</timeout>
              <options>
                <option>four</option>
                <option>five</option>
                <option>six</option>
              </options>
            </configuration>
            <goals>
              <goal>query</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

Now, `MyBoundQueryMojo` default phase which is package has been overridden by install phase.  现在，MyBoundQueryMojo 默认阶段是包已被安装阶段覆盖。

**Note:** Configurations inside the `<executions>` element used to differ from those that are outside `<executions>` in that they could not be used from a direct command line invocation because they were only applied when the lifecycle phase they were bound to was invoked. So you had to move a configuration section outside of the executions section to apply it globally to all invocations of the plugin. Since Maven 3.3.1 this is not the case anymore as you can specify on the command line the execution id for direct plugin goal invocation. Hence if you want to run the above plugin and it's specific execution1's configuration from the command-line, you can execute:  注意：`<executions>` 元素内的配置过去与 `<executions>` 外的配置不同，因为它们不能从直接命令行调用中使用，因为它们仅在它们绑定到的生命周期阶段被调用时应用。 因此，您必须将配置部分移到执行部分之外，以将其全局应用于插件的所有调用。 从 Maven 3.3.1 开始，情况不再如此，因为您可以在命令行上指定直接插件目标调用的执行 ID。 因此，如果您想从命令行运行上述插件并且它是特定 execution1 的配置，您可以执行：

```bash
mvn myqyeryplugin:queryMojo@execution1
```

### Using the `<dependencies>` Tag

You could configure the dependencies of the Build plugins, commonly to use a more recent dependency version.  您可以配置 Build 插件的依赖项，通常使用更新的依赖项版本。

For instance, the Maven Antrun Plugin version 1.2 uses Ant version 1.6.5, if you want to use the latest Ant version when running this plugin, you need to add `<dependencies>` element like the following:  例如，Maven Antrun Plugin 1.2版使用Ant 1.6.5版，如果你想在运行这个插件时使用最新的Ant版本，你需要添加`<dependencies>`元素，如下所示：

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-antrun-plugin</artifactId>
        <version>1.2</version>
        ...
        <dependencies>
          <dependency>
            <groupId>org.apache.ant</groupId>
            <artifactId>ant</artifactId>
            <version>1.7.1</version>
          </dependency>
          <dependency>
            <groupId>org.apache.ant</groupId>
            <artifactId>ant-launcher</artifactId>
            <version>1.7.1</version>
          </dependency>
         </dependencies>
      </plugin>
    </plugins>
  </build>
  ...
</project>
```

### Using the `<inherited>` Tag In Build Plugins

By default, plugin configuration should be propagated to child POMs, so to break the inheritance, you could use the `<inherited>` tag:  默认情况下，插件配置应该传播到子 POM，所以为了打破继承，你可以使用 `<inherited>` 标签：

```xml
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-antrun-plugin</artifactId>
        <version>1.2</version>
        <inherited>false</inherited>
        ...
      </plugin>
    </plugins>
  </build>
  ...
</project>
```


## Configuring Reporting Plugins

The following is only to configure Reporting plugins in the `<reporting>` element.

### Using the `<reporting>` Tag VS `<build>` Tag

Configuring a reporting plugin in the `<reporting>` or `<build>` elements in the pom does **NOT** have the same behavior!  在 pom 中的 `<reporting>` 或 `<build>` 元素中配置报告插件不会有相同的行为！

- **mvn site**

It uses **only** the parameters defined in the `<configuration>` element of each reporting Plugin specified in the `<reporting>` element, i.e. `site` always **ignores** the parameters defined in the `<configuration>` element of each plugin specified in `<build>`.  它仅使用在 `<reporting>` 元素中指定的每个报告插件的 `<configuration>` 元素中定义的参数，即站点始终忽略在 `<build>` 中指定的每个插件的 `<configuration>` 元素中定义的参数。

- **mvn aplugin:areportgoal**

It uses **firstly** the parameters defined in the `<configuration>` element of each reporting Plugin specified in the `<reporting>` element; if a parameter is not found, it will look up to a parameter defined in the `<configuration>` element of each plugin specified in `<build>`.  它首先使用在 `<reporting>` 元素中指定的每个报告插件的 `<configuration>` 元素中定义的参数； 如果未找到参数，它将查找在 `<build>` 中指定的每个插件的 `<configuration>` 元素中定义的参数。


### Using the `<reportSets>` Tag

You can configure a reporting plugin using the `<reportSets>` tag. This is most commonly used to generate reports selectively when running `mvn site`. The following will generate only the project team report.  您可以使用 `<reportSets>` 标签配置报告插件。 这最常用于在运行 mvn site 时有选择地生成报告。 以下将仅生成项目团队报告。

```xml
<project>
  ...
  <reporting>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-project-info-reports-plugin</artifactId>
        <version>2.1.2</version>
        <reportSets>
          <reportSet>
            <reports>
              <report>project-team</report>
            </reports>
          </reportSet>
        </reportSets>
      </plugin>
    </plugins>
  </reporting>
  ...
</project>
```

Notes:

To exclude all reports, you need to use:

```xml
  <reportSets>
    <reportSet>
      <reports/>
    </reportSet>
  </reportSets>
```

Refer to each Plugin Documentation (i.e. plugin-info.html) to know the available report goals.

### Using the `<inherited>` Tag In Reporting Plugins

Similar to the build plugins, to break the inheritance, you can use the `<inherited>` tag:

```xml
<project>
  ...
  <reporting>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-project-info-reports-plugin</artifactId>
        <version>2.1.2</version>
        <inherited>false</inherited>
      </plugin>
    </plugins>
  </reporting>
  ...
</project>
```

