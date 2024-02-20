```bash

$ tree -a .
.
├── README.md
├── pom.xml
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

$ mvn clean package

$ tree -a .
.
├── README.md
├── pom.xml
├── src
│   ├── main
│   │   └── java
│   │       └── com
│   │           └── packt
│   │               └── cookbook
│   │                   └── App.java
│   └── test
│       └── java
│           └── com
│               └── packt
│                   └── cookbook
│                       └── AppTest.java
└── target
    ├── classes
    │   └── com
    │       └── packt
    │           └── cookbook
    │               └── App.class
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
    ├── project-with-assembly-1.0-SNAPSHOT.jar
    ├── surefire-reports
    │   ├── TEST-com.packt.cookbook.AppTest.xml
    │   └── com.packt.cookbook.AppTest.txt
    └── test-classes
        └── com
            └── packt
                └── cookbook
                    └── AppTest.class

32 directories, 14 files
$

#############################################################################

$ mvn help:describe -DgroupId=org.apache.maven.plugins -DartifactId=maven-assembly-plugin -Dversion=3.3.0

$ mvn help:describe -Dcmd=assembly:help



$ mvn help:describe -Dcmd=assembly:single -Ddetail
[INFO] Scanning for projects...
[INFO]
[INFO] --< com.packt.cookbook:simple-project-executable-jar-dependencies-assembly >--
[INFO] Building simple-project-executable-jar-dependencies-assembly 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-help-plugin:3.2.0:describe (default-cli) @ simple-project-executable-jar-dependencies-assembly ---
[INFO] 'assembly:single' is a plugin goal (aka mojo).
Mojo: 'assembly:single'
assembly:single
  Description: Assemble an application bundle or distribution from an
    assembly descriptor. This goal is suitable either for binding to the
    lifecycle or calling directly from the command line (provided all required
    files are available before the build starts, or are produced by another
    goal specified before this one on the command line).
    Note that the parameters descriptors, descriptorRefs, and
    descriptorSourceDirectory are disjoint, i.e., they are not combined during
    descriptor location calculation.
  Implementation: org.apache.maven.plugins.assembly.mojos.SingleAssemblyMojo
  Language: java

  Available parameters:

    additionalProperties
      A set of additional properties to use for filtering

    appendAssemblyId (Default: true)
      User property: assembly.appendAssemblyId
      Set to false to exclude the assembly id from the assembly final name, and
      to create the resultant assembly artifacts without classifier. As such,
      an assembly artifact having the same format as the packaging of the
      current Maven project will replace the file for this main project
      artifact.

    archive
      This is a set of instructions to the archive builder, especially for
      building .jar files. It enables you to specify a Manifest file for the
      jar, in addition to other options. See Maven Archiver Reference.

    archiveBaseDirectory
      This is the base directory from which archive files are created. This
      base directory pre-pended to any <directory> specifications in the
      assembly descriptor. This is an optional parameter.

    archiverConfig
      Allows additional configuration options that are specific to a particular
      type of archive format. This is intended to capture an XML configuration
      that will be used to reflectively setup the options on the archiver
      instance.
      To see the possible options for archiver configuration visit the Plexus
      Archiver Documentation
      For instance, to direct an assembly with the 'ear' format to use a
      particular deployment descriptor, you should specify the following for
      the archiverConfig value in your plugin configuration:

      <appxml>${project.basedir}/somepath/app.xml</appxml>

    attach (Default: true)
      User property: assembly.attach
      Controls whether the assembly plugin tries to attach the resulting
      assembly to the project.

    delimiters
      Set of delimiters for expressions to filter within the resources. These
      delimiters are specified in the form 'beginToken*endToken'. If no '*' is
      given, the delimiter is assumed to be the same for start and end.

      So, the default filtering delimiters might be specified as:

      <delimiters>
       <delimiter>${*}</delimiter>
       <delimiter>@</delimiter>
      </delimiters>

      Since the '@' delimiter is the same on both ends, we don't need to
      specify '@*@' (though we can).

    descriptorRefs
      A list of references to assembly descriptors available on the plugin's
      classpath. The default classpath includes these built-in descriptors:
      bin, jar-with-dependencies, src, and project. You can add others by
      adding dependencies to the plugin.

    descriptors
      A list of descriptor files to generate from.

    descriptorSourceDirectory
      Directory to scan for descriptor files in. NOTE: This may not work
      correctly with assembly components.

    dryRun (Default: false)
      User property: assembly.dryRun
      If this flag is set, everything up to the call to
      Archiver.createArchive() will be executed.

    encoding (Default: ${project.build.sourceEncoding})
      User property: encoding
      The character encoding scheme to be applied when filtering resources.

    escapeString
      User property: assembly.escapeString
      Expressions preceded with this String won't be interpolated. If you use
      '\' as the escape string then \${foo} will be replaced with ${foo}.

    filters
      The list of extra filter properties files to be used along with System
      properties, project properties, and filter properties files specified in
      the POM build/filters section, which should be used for the filtering
      during the current mojo execution.
      Normally, these will be configured from a plugin's execution section, to
      provide a different set of filters for a particular execution.

    formats
      Specifies the formats of the assembly. Multiple formats can be supplied
      and the Assembly Plugin will generate an archive for each desired
      formats. When deploying your project, all file formats specified will
      also be deployed. A format is specified by supplying one of the following
      values in a <format> subelement:
      - dir - Creates a directory
      - zip - Creates a ZIP file format
      - tar - Creates a TAR format
      - tar.gz or tgz - Creates a gzip'd TAR format
      - tar.bz2 or tbz2 - Creates a bzip'd TAR format
      - tar.snappy - Creates a snappy'd TAR format
      - tar.xz or txz - Creates a xz'd TAR format

    ignoreDirFormatExtensions (Default: true)
      If this flag is set, the '.dir' suffix will be suppressed in the output
      directory name when using assembly/format == 'dir' and other formats that
      begin with 'dir'.
      NOTE: Since 2.2-beta-3, the default-value for this is true, NOT false as
      it used to be.

    ignoreMissingDescriptor (Default: false)
      User property: assembly.ignoreMissingDescriptor
      Set to true in order to not fail when a descriptor is missing.

    ignorePermissions (Default: false)
      User property: assembly.ignorePermissions
      Set to true in order to avoid all chmod calls.

      NOTE: This will cause the assembly plugin to DISREGARD all
      fileMode/directoryMode settings in the assembly descriptor, and all file
      permissions in unpacked dependencies!

    includeProjectBuildFilters (Default: true)
      User property: assembly.includeProjectBuildFilters
      If True (default) then the ${project.build.filters} are also used in
      addition to any further filters defined for the Assembly.

    mergeManifestMode
      sets the merge manifest mode in the JarArchiver

    outputDirectory (Default: ${project.build.directory})
      Required: true
      The output directory of the assembled distribution file.

    outputTimestamp (Default: ${project.build.outputTimestamp})
      Timestamp for reproducible output archive entries, either formatted as
      ISO 8601 yyyy-MM-dd'T'HH:mm:ssXXX or as an int representing seconds since
      the epoch (like SOURCE_DATE_EPOCH).

    overrideGid
      Override of group ID in archive type which can store it.

    overrideGroupName
      Override of group name in archive type which can store it.

    overrideUid
      Override of user ID in archive type which can store it.

    overrideUserName
      Override of user name in archive type which can store it.

    recompressZippedFiles (Default: true)
      Indicates if zip archives (jar,zip etc) being added to the assembly
      should be compressed again. Compressing again can result in smaller
      archive size, but gives noticeably longer execution time.

    runOnlyAtExecutionRoot (Default: false)
      User property: assembly.runOnlyAtExecutionRoot
      This will cause the assembly to run only at the top of a given module
      tree. That is, run in the project contained in the same folder where the
      mvn execution was launched.

    skipAssembly (Default: false)
      User property: assembly.skipAssembly
      Flag allowing one or more executions of the assembly plugin to be
      configured as skipped for a particular build. This makes the assembly
      plugin more controllable from profiles.

    tarLongFileMode (Default: warn)
      User property: assembly.tarLongFileMode
      Sets the TarArchiver behavior on file paths with more than 100 characters
      length. Valid values are: 'warn' (default), 'fail', 'truncate', 'gnu',
      'posix', 'posix_warn' or 'omit'.

    updateOnly (Default: false)
      User property: assembly.updateOnly
      This will cause the assembly to only update an existing archive, if it
      exists.
      Note: The property that can be used on the command line was misspelled as
      'assembly.updatOnly' in versions prior to version 2.4.

    useJvmChmod (Default: false)
      User property: assembly.useJvmChmod
      (no description available)
      Deprecated. Not used anymore and will be removed in future
      version

    workDirectory (Default:
    ${project.build.directory}/assembly/work)
      Required: true
      Directory to unpack JARs into if needed


[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.914 s
[INFO] Finished at: 2021-10-05T10:11:28+08:00
[INFO] ------------------------------------------------------------------------
$

$ mvn clean package
maven-clean-plugin:3.1.0:clean
maven-resources-plugin:3.0.2:resources
maven-compiler-plugin:3.8.0:compile
maven-resources-plugin:3.0.2:testResources
maven-compiler-plugin:3.8.0:testCompile
maven-surefire-plugin:2.22.1:test

maven-jar-plugin:3.0.2:jar
Building jar: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter11/project-with-assembly/target/project-with-assembly-1.0-SNAPSHOT.jar

maven-assembly-plugin:3.3.0:single
Building jar: /Users/huzhi/work/code/java_code/maven/Apache-Maven-Cookbook/Chapter11/project-with-assembly/target/project-with-assembly-1.0-SNAPSHOT-jar-with-dependencies.jar
$


$ tree -a target
target
├── archive-tmp
├── classes
│   └── com
│       └── packt
│           └── cookbook
│               └── App.class
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
├── project-with-assembly-1.0-SNAPSHOT-jar-with-dependencies.jar
├── project-with-assembly-1.0-SNAPSHOT.jar
├── surefire-reports
│   ├── TEST-com.packt.cookbook.AppTest.xml
│   └── com.packt.cookbook.AppTest.txt
└── test-classes
    └── com
        └── packt
            └── cookbook
                └── AppTest.class

21 directories, 11 files
$

$ java -jar target/project-with-assembly-1.0-SNAPSHOT-jar-with-dependencies.jar
[main] INFO com.packt.cookbook.App - Hello World

$ java -jar target/project-with-assembly-1.0-SNAPSHOT.jar
target/project-with-assembly-1.0-SNAPSHOT.jar中没有主清单属性


$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       └── com.packt.cookbook
│           └── project-with-assembly
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
└── project-with-assembly-1.0-SNAPSHOT.jar

7 directories, 5 files

$ cat jar/META-INF/MANIFEST.MF
Manifest-Version: 1.0
Built-By: huzhi
Created-By: Apache Maven 3.6.3
Build-Jdk: 1.8.0_275




$ tree -a jar
jar
├── META-INF
│   ├── MANIFEST.MF
│   └── maven
│       ├── com.packt.cookbook
│       │   └── project-with-assembly
│       │       ├── pom.properties
│       │       └── pom.xml
│       └── org.slf4j
│           ├── slf4j-api
│           │   ├── pom.properties
│           │   └── pom.xml
│           └── slf4j-simple
│               ├── pom.properties
│               └── pom.xml
├── com
│   └── packt
│       └── cookbook
│           └── App.class
├── org
│   └── slf4j
│       ├── ILoggerFactory.class
│       ├── IMarkerFactory.class
│       ├── Logger.class
│       ├── LoggerFactory.class
│       ├── MDC$1.class
│       ├── MDC$MDCCloseable.class
│       ├── MDC.class
│       ├── Marker.class
│       ├── MarkerFactory.class
│       ├── helpers
│       │   ├── BasicMDCAdapter.class
│       │   ├── BasicMarker.class
│       │   ├── BasicMarkerFactory.class
│       │   ├── FormattingTuple.class
│       │   ├── MarkerIgnoringBase.class
│       │   ├── MessageFormatter.class
│       │   ├── NOPLogger.class
│       │   ├── NOPLoggerFactory.class
│       │   ├── NOPMDCAdapter.class
│       │   ├── NamedLoggerBase.class
│       │   ├── SubstituteLogger.class
│       │   ├── SubstituteLoggerFactory.class
│       │   ├── Util$1.class
│       │   ├── Util$ClassContextSecurityManager.class
│       │   └── Util.class
│       ├── impl
│       │   ├── SimpleLogger$1.class
│       │   ├── SimpleLogger.class
│       │   ├── SimpleLoggerFactory.class
│       │   ├── StaticLoggerBinder.class
│       │   ├── StaticMDCBinder.class
│       │   └── StaticMarkerBinder.class
│       └── spi
│           ├── LocationAwareLogger.class
│           ├── LoggerFactoryBinder.class
│           ├── MDCAdapter.class
│           └── MarkerFactoryBinder.class
└── project-with-assembly-1.0-SNAPSHOT-jar-with-dependencies.jar

15 directories, 43 files

$ cat jar/META-INF/MANIFEST.MF
Manifest-Version: 1.0
Build-Jdk-Spec: 1.8
Created-By: Maven Archiver 3.5.0
Main-Class: com.packt.cookbook.App

$



















```




