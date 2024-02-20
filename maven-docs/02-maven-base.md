# maven 内置的三个生命周期

maven 内置了三个生命周期，分别是 default, clean 和 site

每个生命周期包括不同阶段（phase），

每个阶段（phase）都由插件目标（plugin goals）组成。
也就是执行相应阶段（phase）的时候本质就是调用相应的插件的相关目标。

Lifecycle default -> [
    validate,
    initialize,
    generate-sources,
    process-sources,
    generate-resources,
    process-resources,
    compile,
    process-classes,
    generate-test-sources,
    process-test-sources,
    generate-test-resources,
    process-test-resources,
    test-compile,
    process-test-classes,
    test,
    prepare-package,
    package,
    pre-integration-test,
    integration-test,
    post-integration-test,
    verify,
    install,
    deploy
]

Lifecycle clean -> [
    pre-clean,
    clean,
    post-clean
]

Lifecycle site -> [
    pre-site,
    site,
    post-site,
    site-deploy
]

| Phase             | Plugin                                                            | Goal                                    |
| ----------------- | ----------------------------------------------------------------- | --------------------------------------- |
| clean             | Maven Clean plugin                                                | clean                                   |
| site              | Maven Site plugin                                                 | site                                    |
| process-resources | Maven Resources plugin                                            | resource                                |
| compile           | Maven Compiler plugin                                             | compile                                 |
| test              | Maven Surefire plugin                                             | test                                    |
| package           | Varies based on the packaging; for instance, the Maven JAR plugin | jar (in the case of a Maven JAR plugin) |
| install           | Maven Install plugin                                              | install                                 |
| deploy            | Maven Deploy plugin                                               | deploy                                  |

## 查看每个 phase 实现的插件

查看每个 phase 实现的插件需要在带有 pom.xml 文件的目录中执行，mvn 会扫描 pom.xml 配置，也就是查看每个 phase 实现的插件还是需要用户自己决定。

```bash
################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe -Dcmd=pre-clean
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------< org.apache.maven:standalone-pom >-------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ standalone-pom ---
[INFO] 'pre-clean' is a phase within the 'clean' lifecycle, which has the following phases:
* pre-clean: Not defined
  说明没有插件的目标实现这个 pre-clean 阶段
* clean: org.apache.maven.plugins:maven-clean-plugin:3.2.0:clean
  说明 clean 阶段是由 org.apache.maven.plugins:maven-clean-plugin 插件的 clean 目标实现
* post-clean: Not defined
  说明没有插件的目标实现这个 post-clean 阶段

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.546 s
[INFO] Finished at: 2024-02-20T09:21:57Z
[INFO] ------------------------------------------------------------------------
$

################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe -Dcmd=compile
[INFO] Scanning for projects...
[INFO]
[INFO] --------< com.packt.cookbook:project-with-additional-resources >--------
[INFO] Building Project with additional resources 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ project-with-additional-resources ---
[INFO] 'compile' is a phase corresponding to this plugin:
org.apache.maven.plugins:maven-compiler-plugin:3.11.0:compile

It is a part of the lifecycle for the POM packaging 'jar'. This lifecycle includes the following phases:
* validate: Not defined
* initialize: Not defined
* generate-sources: Not defined
* process-sources: Not defined
* generate-resources: Not defined
* process-resources: org.apache.maven.plugins:maven-resources-plugin:3.3.1:resources
* compile: org.apache.maven.plugins:maven-compiler-plugin:3.11.0:compile
* process-classes: Not defined
* generate-test-sources: Not defined
* process-test-sources: Not defined
* generate-test-resources: Not defined
* process-test-resources: org.apache.maven.plugins:maven-resources-plugin:3.3.1:testResources
* test-compile: org.apache.maven.plugins:maven-compiler-plugin:3.11.0:testCompile
* process-test-classes: Not defined
* test: org.apache.maven.plugins:maven-surefire-plugin:3.2.2:test
* prepare-package: Not defined
* package: org.apache.maven.plugins:maven-jar-plugin:3.3.0:jar
* pre-integration-test: Not defined
* integration-test: Not defined
* post-integration-test: Not defined
* verify: Not defined
* install: org.apache.maven.plugins:maven-install-plugin:3.1.1:install
* deploy: org.apache.maven.plugins:maven-deploy-plugin:3.1.1:deploy

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.653 s
[INFO] Finished at: 2024-02-20T09:26:24Z
[INFO] ------------------------------------------------------------------------
$

```

# maven 全部可用插件

* http://maven.apache.org/plugins
* 查找插件的 groupId 和 artifactId
* groupId 一般是 org.apache.maven.plugins
* 插件中有目标，每个目标中有相应的参数

## 查看特定插件的包含的目标和目标对应的参数

```bash
################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-jar-plugin \
-Ddetail
[INFO] Scanning for projects...
[INFO]
[INFO] --------< com.packt.cookbook:project-with-additional-resources >--------
[INFO] Building Project with additional resources 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ project-with-additional-resources ---
[INFO] org.apache.maven.plugins:maven-jar-plugin:3.3.0

Name: Apache Maven JAR Plugin
Description: Builds a Java Archive (JAR) file from the compiled project
  classes and resources.
Group Id: org.apache.maven.plugins
Artifact Id: maven-jar-plugin
Version: 3.3.0
Goal Prefix: jar

This plugin has 3 goals:

jar:help
  Description: Display help information on maven-jar-plugin.
    Call mvn jar:help -Ddetail=true -Dgoal=<goal-name> to display parameter
    details.
  Implementation: org.apache.maven.plugins.jar.HelpMojo
  Language: java

  Available parameters:

    detail (Default: false)
      User property: detail
      If true, display all settable properties for each goal.

    goal
      User property: goal
      The name of the goal for which to show help. If unspecified, all goals
      will be displayed.

    indentSize (Default: 2)
      User property: indentSize
      The number of spaces per indentation level, should be positive.

    lineLength (Default: 80)
      User property: lineLength
      The maximum length of a display line, should be positive.

jar:jar
  Description: Build a JAR from the current project.
  Implementation: org.apache.maven.plugins.jar.JarMojo
  Language: java
  Bound to phase: package

  Available parameters:

    archive
      The archive configuration to use. See Maven Archiver Reference
      <http://maven.apache.org/shared/maven-archiver/index.html>.

    classesDirectory (Default: ${project.build.outputDirectory})
      Required: true
      Directory containing the classes and resource files that should be
      packaged into the JAR.

    classifier
      Classifier to add to the artifact generated. If given, the artifact will
      be attached as a supplemental artifact. If not given this will create the
      main artifact which is the default behavior. If you try to do that a
      second time without using a classifier the build will fail.

    excludes
      List of files to exclude. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    forceCreation (Default: false)
      User property: maven.jar.forceCreation
      Require the jar plugin to build a new JAR even if none of the contents
      appear to have changed. By default, this plugin looks to see if the
      output jar exists and inputs have not changed. If these conditions are
      true, the plugin skips creation of the jar. This does not work when other
      plugins, like the maven-shade-plugin, are configured to post-process the
      jar. This plugin can not detect the post-processing, and so leaves the
      post-processed jar in place. This can lead to failures when those plugins
      do not expect to find their own output as an input. Set this parameter to
      true to avoid these problems by forcing this plugin to recreate the jar
      every time.
      Starting with 3.0.0 the property has been renamed from jar.forceCreation
      to maven.jar.forceCreation.

    includes
      List of files to include. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    outputDirectory (Default: ${project.build.directory})
      Required: true
      Directory containing the generated JAR.

    outputTimestamp (Default: ${project.build.outputTimestamp})
      Timestamp for reproducible output archive entries, either formatted as
      ISO 8601 extended offset date-time (e.g. in UTC such as
      '2011-12-03T10:15:30Z' or with an offset '2019-10-05T20:37:42+06:00'), or
      as an int representing seconds since the epoch (like SOURCE_DATE_EPOCH
      <https://reproducible-builds.org/docs/source-date-epoch/>).

    skipIfEmpty (Default: false)
      Skip creating empty archives.

    useDefaultManifestFile (Default: false)
      User property: jar.useDefaultManifestFile
      Using this property will fail your build cause it has been removed from
      the plugin configuration. See the Major Version Upgrade to version 3.0.0
      <https://maven.apache.org/plugins/maven-jar-plugin/> for the plugin.
      Deprecated. For version 3.0.0 this parameter is only defined here
      to break the build if you use it!

jar:test-jar
  Description: Build a JAR of the test classes for the current project.
  Implementation: org.apache.maven.plugins.jar.TestJarMojo
  Language: java
  Bound to phase: package

  Available parameters:

    archive
      The archive configuration to use. See Maven Archiver Reference
      <http://maven.apache.org/shared/maven-archiver/index.html>.

    classifier (Default: tests)
      Classifier to use for {@code test-jar}.

    excludes
      List of files to exclude. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    forceCreation (Default: false)
      User property: maven.jar.forceCreation
      Require the jar plugin to build a new JAR even if none of the contents
      appear to have changed. By default, this plugin looks to see if the
      output jar exists and inputs have not changed. If these conditions are
      true, the plugin skips creation of the jar. This does not work when other
      plugins, like the maven-shade-plugin, are configured to post-process the
      jar. This plugin can not detect the post-processing, and so leaves the
      post-processed jar in place. This can lead to failures when those plugins
      do not expect to find their own output as an input. Set this parameter to
      true to avoid these problems by forcing this plugin to recreate the jar
      every time.
      Starting with 3.0.0 the property has been renamed from jar.forceCreation
      to maven.jar.forceCreation.

    includes
      List of files to include. Specified as fileset patterns which are
      relative to the input directory whose contents is being packaged into the
      JAR.

    outputDirectory (Default: ${project.build.directory})
      Required: true
      Directory containing the generated JAR.

    outputTimestamp (Default: ${project.build.outputTimestamp})
      Timestamp for reproducible output archive entries, either formatted as
      ISO 8601 extended offset date-time (e.g. in UTC such as
      '2011-12-03T10:15:30Z' or with an offset '2019-10-05T20:37:42+06:00'), or
      as an int representing seconds since the epoch (like SOURCE_DATE_EPOCH
      <https://reproducible-builds.org/docs/source-date-epoch/>).

    skip
      User property: maven.test.skip
      Set this to true to bypass test-jar generation. Its use is NOT
      RECOMMENDED, but quite convenient on occasion.

    skipIfEmpty (Default: false)
      Skip creating empty archives.

    testClassesDirectory (Default:
    ${project.build.testOutputDirectory})
      Required: true
      Directory containing the test classes and resource files that should be
      packaged into the JAR.

    useDefaultManifestFile (Default: false)
      User property: jar.useDefaultManifestFile
      Using this property will fail your build cause it has been removed from
      the plugin configuration. See the Major Version Upgrade to version 3.0.0
      <https://maven.apache.org/plugins/maven-jar-plugin/> for the plugin.
      Deprecated. For version 3.0.0 this parameter is only defined here
      to break the build if you use it!


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.270 s
[INFO] Finished at: 2024-02-20T09:32:57Z
[INFO] ------------------------------------------------------------------------
$

################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-help-plugin \
-Ddetail
[INFO] Scanning for projects...
[INFO]
[INFO] --------< com.packt.cookbook:project-with-additional-resources >--------
[INFO] Building Project with additional resources 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ project-with-additional-resources ---
[INFO] org.apache.maven.plugins:maven-help-plugin:3.4.0

Name: Apache Maven Help Plugin
Description: The Maven Help plugin provides goals aimed at helping to make
  sense out of the build environment. It includes the ability to view the
  effective POM and settings files, after inheritance and active profiles have
  been applied, as well as a describe a particular plugin goal to give usage
  information.
Group Id: org.apache.maven.plugins
Artifact Id: maven-help-plugin
Version: 3.4.0
Goal Prefix: help

This plugin has 8 goals:

help:active-profiles
  Description: Displays a list of the profiles which are currently active for
    this build.
  Implementation: org.apache.maven.plugins.help.ActiveProfilesMojo
  Language: java

  Available parameters:

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.

help:all-profiles
  Description: Displays a list of available profiles under the current
    project. Note: it will list all profiles for a project. If a profile comes
    up with a status inactive then there might be a need to set profile
    activation switches/property.
  Implementation: org.apache.maven.plugins.help.AllProfilesMojo
  Language: java

  Available parameters:

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.

help:describe
  Description: Displays a list of the attributes for a Maven Plugin and/or
    goals (aka Mojo - Maven plain Old Java Object). See also: What is a Mojo?
  Implementation: org.apache.maven.plugins.help.DescribeMojo
  Language: java

  Available parameters:

    artifactId
      User property: artifactId
      The Maven Plugin artifactId to describe. Note: Should be used with
      groupId parameter.

    cmd
      User property: cmd
      A Maven command like a single goal or a single phase following the Maven
      command line: mvn [options] [] []

    detail (Default: false)
      User property: detail
      This flag specifies that a detailed (verbose) list of goal (Mojo)
      information should be given.

    goal
      User property: goal
      The goal name of a Mojo to describe within the specified Maven Plugin. If
      this parameter is specified, only the corresponding goal (Mojo) will be
      described, rather than the whole Plugin.

    groupId
      User property: groupId
      The Maven Plugin groupId to describe. Note: Should be used with
      artifactId parameter.

    minimal (Default: false)
      User property: minimal
      This flag specifies that a minimal list of goal (Mojo) information should
      be given.

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.

    plugin
      Alias: prefix
      User property: plugin
      The Maven Plugin to describe. This must be specified in one of three
      ways: * plugin-prefix, i.e. 'help' * groupId:artifactId, i.e.
      'org.apache.maven.plugins:maven-help-plugin' *
      groupId:artifactId:version, i.e.
      'org.apache.maven.plugins:maven-help-plugin:2.0'

    version
      User property: version
      The Maven Plugin version to describe. Note: Should be used with
      groupId/artifactId parameters.

help:effective-pom
  Description: Displays the effective POM as an XML for this build, with the
    active profiles factored in, or a specified artifact. If verbose, a comment
    is added to each XML element describing the origin of the line.
  Implementation: org.apache.maven.plugins.help.EffectivePomMojo
  Language: java

  Available parameters:

    artifact
      User property: artifact
      The artifact for which to display the effective POM. Note: Should respect
      the Maven format, i.e. groupId:artifactId[:version]. The latest version
      of the artifact will be used when no version is specified.

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.

    verbose (Default: false)
      User property: verbose
      Output POM input location as comments.

help:effective-settings
  Description: Displays the calculated settings as XML for this project,
    given any profile enhancement and the inheritance of the global settings
    into the user-level settings.
  Implementation: org.apache.maven.plugins.help.EffectiveSettingsMojo
  Language: java

  Available parameters:

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.

    showPasswords (Default: false)
      User property: showPasswords
      For security reasons, all passwords are hidden by default. Set this to
      true to show all passwords.

help:evaluate
  Description: Evaluates Maven expressions given by the user in an
    interactive mode.
  Implementation: org.apache.maven.plugins.help.EvaluateMojo
  Language: java

  Available parameters:

    artifact
      User property: artifact
      An artifact for evaluating Maven expressions. Note: Should respect the
      Maven format, i.e. groupId:artifactId[:version]. The latest version of
      the artifact will be used when no version is specified.

    expression
      User property: expression
      An expression to evaluate instead of prompting. Note that this must not
      include the surrounding ${...}.

    forceStdout (Default: false)
      User property: forceStdout
      This options gives the option to output information in cases where the
      output has been suppressed by using -q (quiet option) in Maven. This is
      useful if you like to use maven-help-plugin:evaluate in a script call
      (for example in bash) like this: RESULT=$(mvn help:evaluate
      -Dexpression=project.version -q -DforceStdout) echo $RESULT This will
      only printout the information which has been requested by expression to
      stdout.

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. This parameter will be ignored if no
      expression is specified. Note: Could be a relative path.

help:help
  Description: Display help information on maven-help-plugin. Call mvn
    help:help -Ddetail=true -Dgoal= to display parameter details.
  Implementation: org.apache.maven.plugins.help.HelpMojo
  Language: java

  Available parameters:

    detail (Default: false)
      User property: detail
      If true, display all settable properties for each goal.

    goal
      User property: goal
      The name of the goal for which to show help. If unspecified, all goals
      will be displayed.

    indentSize (Default: 2)
      User property: indentSize
      The number of spaces per indentation level, should be positive.

    lineLength (Default: 80)
      User property: lineLength
      The maximum length of a display line, should be positive.

help:system
  Description: Displays a list of the platform details like system properties
    and environment variables.
  Implementation: org.apache.maven.plugins.help.SystemMojo
  Language: java

  Available parameters:

    output
      User property: output
      Optional parameter to write the output of this help in a given file,
      instead of writing to the console. Note: Could be a relative path.


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.652 s
[INFO] Finished at: 2024-02-20T09:35:56Z
[INFO] ------------------------------------------------------------------------
$

################################################################################

# 查看插件中中目标的具体信息

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-Ddetail \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-jar-plugin \
-Dcmd=jar:jar


################################################################################

# 指定插件版本
$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-dependency-plugin \
-Dversion=3.3.0

################################################################################

```

# 生成项目骨架

mvn archetype:generate

# 生成最终的 pom

mvn help:effective-pom

#
$ mvn help:describe -Dplugin=org.apache.maven.plugins:maven-release-plugin -Ddetail=true

$ mvn clean release:clean
$ mvn clean release:clean -Dmaven.test.skip=true -Dmaven.verify.skip=true

$ mvn release:prepare -Psigned_release -Darguments="-DskipTests"

$ mvn release:perform -Psigned_release -Darguments="-DskipTests" -DdryRun=true

mvn clean
mvn install -Prelease-all -DskipTests -U
mvn install -Prelease-all -DskipTests -Dgpg.skip -U

