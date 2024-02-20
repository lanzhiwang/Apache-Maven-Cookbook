```bash
#####################################################################

$ tree -a .
.
├── pom.xml
├── README.md
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── packt
    │               └── cookbook
    │                   └── App.java
    └── test
        └── java
            └── com
                └── packt
                    └── cookbook
                        └── AppTest.java

11 directories, 4 files
$

#####################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml test
[INFO] Scanning for projects...
[INFO]
[INFO] -----------< com.packt.cookbook:project-with-tests-skipped >------------
[INFO] Building Project with tests skipped 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ project-with-tests-skipped ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/06-project-with-tests-skipped/src/main/resources
[INFO]
[INFO] --- compiler:3.11.0:compile (default-compile) @ project-with-tests-skipped ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ project-with-tests-skipped ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /usr/src/Apache-Maven-Cookbook/Chapter03/06-project-with-tests-skipped/src/test/resources
[INFO]
[INFO] --- compiler:3.11.0:testCompile (default-testCompile) @ project-with-tests-skipped ---
[INFO] Nothing to compile - all classes are up to date
[INFO]
[INFO] --- surefire:2.17:test (default-test) @ project-with-tests-skipped ---
[INFO] Tests are skipped.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.858 s
[INFO] Finished at: 2024-02-20T11:50:25Z
[INFO] ------------------------------------------------------------------------
$

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml help:describe \
-Ddetail \
-DgroupId=org.apache.maven.plugins \
-DartifactId=maven-surefire-plugin \
-Dversion=2.17 \
-Dcmd=surefire:test
[INFO] Scanning for projects...
[INFO]
[INFO] -----------< com.packt.cookbook:project-with-tests-skipped >------------
[INFO] Building Project with tests skipped 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- help:3.4.0:describe (default-cli) @ project-with-tests-skipped ---
[INFO] 'surefire:test' is a plugin goal (aka mojo).
Mojo: 'surefire:test'
surefire:test
  Description: Run tests using Surefire.
  Implementation: org.apache.maven.plugin.surefire.SurefirePlugin
  Language: java
  Bound to phase: test

  Available parameters:

    additionalClasspathElements
      User property: maven.test.additionalClasspath
      Additional elements to be appended to the classpath.

    argLine
      User property: argLine
      Arbitrary JVM options to set on the command line.

    basedir (Default: ${basedir})
      The base directory of the project being tested. This can be obtained in
      your integration test via System.getProperty("basedir").

    childDelegation (Default: false)
      User property: childDelegation
      When false it makes tests run using the standard classloader delegation
      instead of the default Maven isolated classloader. Only used when forking
      (forkMode is not "none").
      Setting it to false helps with some problems caused by conflicts between
      xml parsers in the classpath and the Java 5 provider parser.

    classesDirectory (Default: ${project.build.outputDirectory})
      The directory containing generated classes of the project being tested.
      This will be included after the test classes in the test classpath.

    classpathDependencyExcludes
      User property: maven.test.dependency.excludes
      List of dependencies to exclude from the test classpath. Each dependency
      string must follow the format groupId:artifactId. For example:
      org.acme:project-a

    classpathDependencyScopeExclude
      A dependency scope to exclude from the test classpath. The scope should
      be one of the scopes defined by org.apache.maven.artifact.Artifact. This
      includes the following:


      * compile - system, provided, compile
      * runtime - compile, runtime
      * compile+runtime - system, provided, compile, runtime
      * runtime+system - system, compile, runtime
      * test - system, provided, compile, runtime, test

    debugForkedProcess
      User property: maven.surefire.debug
      Attach a debugger to the forked JVM. If set to "true", the process will
      suspend and wait for a debugger to attach on port 5005. If set to some
      other string, that string will be appended to the argLine, allowing you
      to configure arbitrary debuggability options (without overwriting the
      other options specified through the argLine parameter).

    dependenciesToScan
      User property: dependenciesToScan
      List of dependencies to scan for test classes to include in the test run.
      The child elements of this element must be <dependency> elements, and the
      contents of each of these elements must be a string which follows the
      format: groupId:artifactId. For example: org.acme:project-a.

    disableXmlReport (Default: false)
      User property: disableXmlReport
      Flag to disable the generation of report files in xml format.

    enableAssertions (Default: true)
      User property: enableAssertions
      By default, Surefire enables JVM assertions for the execution of your
      test cases. To disable the assertions, set this flag to "false".

    environmentVariables
      Additional environment variables to set on the command line.

    excludedGroups
      User property: excludedGroups
      (TestNG/JUnit47 provider with JUnit4.8+ only) Excluded groups. Any
      methods/classes/etc with one of the groups specified in this list will
      specifically not be run.
      For JUnit, this parameter forces the use of the 4.7 provider
      This parameter is ignored if the suiteXmlFiles parameter is specified.

    excludes
      A list of <exclude> elements specifying the tests (by pattern) that
      should be excluded in testing. When not specified and when the test
      parameter is not specified, the default excludes will be
      <excludes>
      <exclude>**/*$*</exclude>
      </excludes>
      (which excludes all inner classes).
      This parameter is ignored if the TestNG suiteXmlFiles parameter is
      specified.

      Each exclude item may also contain a comma-separated sublist of items,
      which will be treated as multiple <exclude> entries.

    excludesFile
      A file containing exclude patterns. Blank lines, or lines starting with #
      are ignored. If {@code excludes} are also specified these patterns are
      appended.

    failIfNoSpecifiedTests
      User property: surefire.failIfNoSpecifiedTests
      Set this to "true" to cause a failure if the none of the tests specified
      in -Dtest=... are run. Defaults to "true".

    failIfNoTests
      User property: failIfNoTests
      Set this to "true" to cause a failure if there are no tests to run.
      Defaults to "false".

    forkCount (Default: 1)
      User property: forkCount
      Option to specify the number of VMs to fork in parallel in order to
      execute the tests. When terminated with "C", the number part is
      multiplied with the number of CPU cores. Floating point value are only
      accepted together with "C". If set to "0", no VM is forked and all tests
      are executed within the main process.

      Example values: "1.5C", "4"

      The system properties and the argLine of the forked processes may contain
      the place holder string ${surefire.forkNumber}, which is replaced with a
      fixed number for each of the parallel forks, ranging from 1 to the
      effective value of forkCount times the maximum number of parallel
      Surefire executions in maven parallel builds, i.e. the effective value of
      the -T command line argument of maven core.

    forkedProcessTimeoutInSeconds
      User property: surefire.timeout
      Kill the forked test process after a certain number of seconds. If set to
      0, wait forever for the process, never timing out.

    forkMode (Default: once)
      User property: forkMode
      DEPRECATED since version 2.14. Use forkCount and reuseForks instead.

      Option to specify the forking mode. Can be "never", "once", "always",
      "perthread". "none" and "pertest" are also accepted for backwards
      compatibility. "always" forks for each test-class. "perthread" will
      create threadCount parallel forks, each executing one test-class. See
      also parameter reuseForks.

    groups
      User property: groups
      (TestNG/JUnit47 provider with JUnit4.8+ only) Groups for this test. Only
      classes/methods/etc decorated with one of the groups specified here will
      be included in test run, if specified.
      For JUnit, this parameter forces the use of the 4.7 provider
      This parameter is ignored if the suiteXmlFiles parameter is specified.

    includes
      A list of <include> elements specifying the tests (by pattern) that
      should be included in testing. When not specified and when the test
      parameter is not specified, the default includes will be
      <includes>
      <include>**/Test*.java</include>
      <include>**/*Test.java</include>
      <include>**/*TestCase.java</include>
      </includes>


      Each include item may also contain a comma-separated sublist of items,
      which will be treated as multiple <include> entries.


      This parameter is ignored if the TestNG suiteXmlFiles parameter is
      specified.

    includesFile
      A file containing include patterns. Blank lines, or lines starting with #
      are ignored. If {@code includes} are also specified these patterns are
      appended.

    junitArtifactName (Default: junit:junit)
      User property: junitArtifactName
      Allows you to specify the name of the JUnit artifact. If not set,
      junit:junit will be used.

    jvm
      User property: jvm
      Option to specify the jvm (or path to the java executable) to use with
      the forking options. For the default, the jvm will be a new instance of
      the same VM as the one used to run Maven. JVM settings are not inherited
      from MAVEN_OPTS.

    objectFactory
      User property: objectFactory
      (TestNG only) Define the factory class used to create all test instances.

    parallel
      User property: parallel
      (TestNG only) When you use the parallel attribute, TestNG will try to run
      all your test methods in separate threads, except for methods that depend
      on each other, which will be run in the same thread in order to respect
      their order of execution.

      (JUnit 4.7 provider) Supports values "classes"/"methods"/"both" to run in
      separate threads, as controlled by threadCount.

      Since version 2.16 (JUnit 4.7 provider), the value "both" is DEPRECATED.
      Use "classesAndMethods" instead.

      Since version 2.16 (JUnit 4.7 provider), additional vales are available
      "suites"/"suitesAndClasses"/"suitesAndMethods"/"classesAndMethods"/"all".

    parallelOptimized (Default: true)
      User property: parallelOptimized
      (JUnit 4.7 / provider only) The thread counts do not exceed the number of
      parallel suite, class runners and average number of methods per class if
      set to true.

      True by default.

    parallelTestsTimeoutForcedInSeconds
      User property: surefire.parallel.forcedTimeout
      Stop executing queued parallel JUnit tests and interrupt currently
      running tests after a certain number of seconds.
      Example values: "3.5", "4"

      If set to 0, wait forever, never timing out. Makes sense with specified
      parallel different from "none".

    parallelTestsTimeoutInSeconds
      User property: surefire.parallel.timeout
      Stop executing queued parallel JUnit tests after a certain number of
      seconds.
      Example values: "3.5", "4"

      If set to 0, wait forever, never timing out. Makes sense with specified
      parallel different from "none".

    perCoreThreadCount (Default: true)
      User property: perCoreThreadCount
      (JUnit 4.7 provider) Indicates that threadCount, threadCountSuites,
      threadCountClasses, threadCountMethods are per cpu core.

    printSummary (Default: true)
      User property: surefire.printSummary
      Option to print summary of test suites or just print the test cases that
      have errors.

    properties
      List of properties for configuring all TestNG related configurations.
      This is the new preferred method of configuring TestNG.

    redirectTestOutputToFile (Default: false)
      User property: maven.test.redirectTestOutputToFile
      Set this to "true" to redirect the unit test standard output to a file
      (found in reportsDirectory/testName-output.txt).

    remoteRepositories (Default:
    ${project.pluginArtifactRepositories})
      The remote plugin repositories declared in the POM.

    reportFormat (Default: brief)
      User property: surefire.reportFormat
      Selects the formatting for the test report to be generated. Can be set as
      "brief" or "plain". Only applies to the output format of the output files
      (target/surefire-reports/testName.txt)

    reportNameSuffix
      User property: surefire.reportNameSuffix
      Add custom text into report filename:
      TEST-testClassName-reportNameSuffix.xml,
      testClassName-reportNameSuffix.txt and
      testClassName-reportNameSuffix-output.txt. File
      TEST-testClassName-reportNameSuffix.xml has changed attributes
      'testsuite'--'name' and 'testcase'--'classname' - reportNameSuffix is
      added to the attribute value.

    reportsDirectory (Default:
    ${project.build.directory}/surefire-reports)
      Base directory where all reports are written to.

    reuseForks (Default: true)
      User property: reuseForks
      Indicates if forked VMs can be reused. If set to "false", a new VM is
      forked for each test class to be executed. If set to "true", up to
      forkCount VMs will be forked and then reused to execute all tests.

    runOrder (Default: filesystem)
      Defines the order the tests will be run in. Supported values are
      "alphabetical", "reversealphabetical", "random", "hourly" (alphabetical
      on even hours, reverse alphabetical on odd hours), "failedfirst",
      "balanced" and "filesystem".



      Odd/Even for hourly is determined at the time the of scanning the
      classpath, meaning it could change during a multi-module build.

      Failed first will run tests that failed on previous run first, as well as
      new tests for this run.

      Balanced is only relevant with parallel=classes, and will try to optimize
      the run-order of the tests to make all tests complete at the same time,
      reducing the overall execution time.

      Note that the statistics are stored in a file named .surefire-XXXXXXXXX
      beside pom.xml, and should not be checked into version control. The
      "XXXXX" is the SHA1 checksum of the entire surefire configuration, so
      different configurations will have different statistics files, meaning if
      you change any config settings you will re-run once before new statistics
      data can be established.

    skip (Default: false)
      User property: maven.test.skip
      Set this to "true" to bypass unit tests entirely. Its use is NOT
      RECOMMENDED, especially if you enable it using the "maven.test.skip"
      property, because maven.test.skip disables both running the tests and
      compiling the tests. Consider using the skipTests parameter instead.

    skipExec
      User property: maven.test.skip.exec
      This old parameter is just like skipTests, but bound to the old property
      "maven.test.skip.exec".
      Deprecated. Use skipTests instead.

    skipTests (Default: false)
      User property: skipTests
      Set this to "true" to skip running tests, but still compile them. Its use
      is NOT RECOMMENDED, but quite convenient on occasion.

    suiteXmlFiles
      (TestNG) List of <suiteXmlFile> elements specifying TestNG suite xml file
      locations. Note that suiteXmlFiles is incompatible with several other
      parameters of this plugin, like includes/excludes.
      This parameter is ignored if the test parameter is specified (allowing
      you to run a single test instead of an entire suite).

    systemProperties
      List of System properties to pass to the JUnit tests.
      Deprecated. Use systemPropertyVariables instead.

    systemPropertiesFile
      List of System properties, loaded from a file, to pass to the JUnit
      tests.

    systemPropertyVariables
      List of System properties to pass to the JUnit tests.

    test
      User property: test
      Specify this parameter to run individual tests by file name, overriding
      the includes/excludes parameters. Each pattern you specify here will be
      used to create an include pattern formatted like **/${test}.java, so you
      can just type "-Dtest=MyTest" to run a single test called
      "foo/MyTest.java". The test patterns prefixed with a ! will be excluded.
      This parameter overrides the includes/excludes parameters, and the TestNG
      suiteXmlFiles parameter.

      Since 2.7.3, you can execute a limited number of methods in the test by
      adding #myMethod or #my*ethod. For example, "-Dtest=MyTest#myMethod".
      This is supported for junit 4.x and testNg.

    testClassesDirectory (Default:
    ${project.build.testOutputDirectory})
      The directory containing generated test classes of the project being
      tested. This will be included at the beginning of the test classpath. *

    testFailureIgnore (Default: false)
      User property: maven.test.failure.ignore
      Set this to "true" to ignore a failure during testing. Its use is NOT
      RECOMMENDED, but quite convenient on occasion.

    testNGArtifactName (Default: org.testng:testng)
      User property: testNGArtifactName
      Allows you to specify the name of the TestNG artifact. If not set,
      org.testng:testng will be used.

    testSourceDirectory (Default:
    ${project.build.testSourceDirectory})
      Required: true
      The test source directory containing test class sources.

    threadCount
      User property: threadCount
      (TestNG/JUnit 4.7 provider) The attribute thread-count allows you to
      specify how many threads should be allocated for this execution. Only
      makes sense to use in conjunction with the parallel parameter.

    threadCountClasses (Default: 0)
      User property: threadCountClasses
      (JUnit 4.7 provider) This attribute allows you to specify the concurrency
      in test classes, i.e.:
      * number of concurrent classes if threadCount is 0 or unspecified
      * limited classes concurrency if useUnlimitedThreads is set to true
      * if threadCount and certain thread-count parameters are > 0 for
      parallel, the concurrency is computed from ratio. For instance
      parallel=all and the ratio between
      threadCountSuites:threadCountClasses:threadCountMethods is 2:3:5, there
      is 30% of threadCount in concurrent classes.
      * as in the previous case but without this leaf thread-count. Example:
      parallel=suitesAndClasses, threadCount=16, threadCountSuites=5,
      threadCountClasses is unspecified leaf, the number of concurrent classes
      is varying from >= 11 to 14 or 15. The threadCountSuites become number of
      threads. Only makes sense to use in conjunction with the parallel
      parameter. The default value 0 behaves same as unspecified one.

    threadCountMethods (Default: 0)
      User property: threadCountMethods
      (JUnit 4.7 provider) This attribute allows you to specify the concurrency
      in test methods, i.e.:
      * number of concurrent methods if threadCount is 0 or unspecified
      * limited concurrency of methods if useUnlimitedThreads is set to true
      * if threadCount and certain thread-count parameters are > 0 for
      parallel, the concurrency is computed from ratio. For instance
      parallel=all and the ratio between
      threadCountSuites:threadCountClasses:threadCountMethods is 2:3:5, there
      is 50% of threadCount in concurrent methods.
      * as in the previous case but without this leaf thread-count. Example:
      parallel=all, threadCount=16, threadCountSuites=2, threadCountClasses=3,
      but threadCountMethods is unspecified leaf, the number of concurrent
      methods is varying from >= 11 to 14 or 15. The threadCountSuites and
      threadCountClasses become number of threads. Only makes sense to use in
      conjunction with the parallel parameter. The default value 0 behaves same
      as unspecified one.

    threadCountSuites (Default: 0)
      User property: threadCountSuites
      (JUnit 4.7 provider) This attribute allows you to specify the concurrency
      in test suites, i.e.:
      * number of concurrent suites if threadCount is 0 or unspecified
      * limited suites concurrency if useUnlimitedThreads is set to true
      * if threadCount and certain thread-count parameters are > 0 for
      parallel, the concurrency is computed from ratio. For instance
      parallel=all and the ratio between
      threadCountSuites:threadCountClasses:threadCountMethods is 2:3:5, there
      is 20% of threadCount in concurrent suites. Only makes sense to use in
      conjunction with the parallel parameter. The default value 0 behaves same
      as unspecified one.

    trimStackTrace (Default: true)
      User property: trimStackTrace
      Whether to trim the stack trace in the reports to just the lines within
      the test, or show the full trace.

    useFile (Default: true)
      User property: surefire.useFile
      Option to generate a file test report or just output the test report to
      the console.

    useManifestOnlyJar (Default: true)
      User property: surefire.useManifestOnlyJar
      By default, Surefire forks your tests using a manifest-only JAR; set this
      parameter to "false" to force it to launch your tests with a plain old
      Java classpath. (See
      http://maven.apache.org/plugins/maven-surefire-plugin/examples/class-loading.html
      for a more detailed explanation of manifest-only JARs and their
      benefits.)

      Beware, setting this to "false" may cause your tests to fail on Windows
      if your classpath is too long.

    useSystemClassLoader (Default: true)
      User property: surefire.useSystemClassLoader
      Option to pass dependencies to the system's classloader instead of using
      an isolated class loader when forking. Prevents problems with JDKs which
      implement the service provider lookup mechanism by using the system's
      classloader.

    useUnlimitedThreads (Default: false)
      User property: useUnlimitedThreads
      (JUnit 4.7 provider) Indicates that the thread pool will be unlimited.
      The parallel parameter and the actual number of classes/methods will
      decide. Setting this to "true" effectively disables perCoreThreadCount
      and threadCount. Defaults to "false".

    workingDirectory
      User property: basedir
      Command line working directory.


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.952 s
[INFO] Finished at: 2024-02-20T11:55:26Z
[INFO] ------------------------------------------------------------------------
$

```