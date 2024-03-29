```bash
########################################################################################

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

########################################################################################

$ javac
Usage: javac <options> <source files>
where possible options include:
  -g                         Generate all debugging info
  -g:none                    Generate no debugging info
  -g:{lines,vars,source}     Generate only some debugging info
  -nowarn                    Generate no warnings
  -verbose                   Output messages about what the compiler is doing
  -deprecation               Output source locations where deprecated APIs are used
  -classpath <path>          Specify where to find user class files and annotation processors
  -cp <path>                 Specify where to find user class files and annotation processors
  -sourcepath <path>         Specify where to find input source files
  -bootclasspath <path>      Override location of bootstrap class files
  -extdirs <dirs>            Override location of installed extensions
  -endorseddirs <dirs>       Override location of endorsed standards path
  -proc:{none,only}          Control whether annotation processing and/or compilation is done.
  -processor <class1>[,<class2>,<class3>...] Names of the annotation processors to run; bypasses default discovery process
  -processorpath <path>      Specify where to find annotation processors
  -parameters                Generate metadata for reflection on method parameters
  -d <directory>             Specify where to place generated class files
  -s <directory>             Specify where to place generated source files
  -h <directory>             Specify where to place generated native header files
  -implicit:{none,class}     Specify whether or not to generate class files for implicitly referenced files
  -encoding <encoding>       Specify character encoding used by source files
  -source <release>          Provide source compatibility with specified release
  -target <release>          Generate class files for specific VM version
  -profile <profile>         Check that API used is available in the specified profile
  -version                   Version information
  -help                      Print a synopsis of standard options
  -Akey[=value]              Options to pass to annotation processors
  -X                         Print a synopsis of nonstandard options
  -J<flag>                   Pass <flag> directly to the runtime system
  -Werror                    Terminate compilation if warnings occur
  @<filename>                Read options and filenames from file

########################################################################################

$ javac -X
  -Xlint                     Enable recommended warnings
  -Xlint:{all,auxiliaryclass,cast,classfile,deprecation,dep-ann,divzero,empty,fallthrough,finally,options,overloads,overrides,path,processing,rawtypes,serial,static,try,unchecked,varargs,-auxiliaryclass,-cast,-classfile,-deprecation,-dep-ann,-divzero,-empty,-fallthrough,-finally,-options,-overloads,-overrides,-path,-processing,-rawtypes,-serial,-static,-try,-unchecked,-varargs,none} Enable or disable specific warnings
  -Xdoclint                  Enable recommended checks for problems in javadoc comments
  -Xdoclint:(all|none|[-]<group>)[/<access>]
        Enable or disable specific checks for problems in javadoc comments,
        where <group> is one of accessibility, html, missing, reference, or syntax,
        and <access> is one of public, protected, package, or private.
  -Xbootclasspath/p:<path>   Prepend to the bootstrap class path
  -Xbootclasspath/a:<path>   Append to the bootstrap class path
  -Xbootclasspath:<path>     Override location of bootstrap class files
  -Djava.ext.dirs=<dirs>     Override location of installed extensions
  -Djava.endorsed.dirs=<dirs> Override location of endorsed standards path
  -Xmaxerrs <number>         Set the maximum number of errors to print
  -Xmaxwarns <number>        Set the maximum number of warnings to print
  -Xstdout <filename>        Redirect standard output
  -Xprint                    Print out a textual representation of specified types
  -XprintRounds              Print information about rounds of annotation processing
  -XprintProcessorInfo       Print information about which annotations a processor is asked to process
  -Xprefer:{source,newer}    Specify which file to read when both a source file and class file are found for an implicitly compiled class
  -Xpkginfo:{always,legacy,nonempty} Specify handling of package-info files
  -Xplugin:"name args"       Name and optional arguments for a plug-in to be run
  -Xdiags:{compact,verbose}  Select a diagnostic mode

These options are non-standard and subject to change without notice.

########################################################################################

$ mvn -s /usr/src/Apache-Maven-Cookbook/settings.xml -X compile

[DEBUG] Command line options:
[DEBUG] -d /usr/src/Apache-Maven-Cookbook/Chapter03/10-project-with-deprecation/target/classes -classpath /usr/src/Apache-Maven-Cookbook/Chapter03/10-project-with-deprecation/target/classes: -sourcepath /usr/src/Apache-Maven-Cookbook/Chapter03/10-project-with-deprecation/src/main/java:/usr/src/Apache-Maven-Cookbook/Chapter03/10-project-with-deprecation/target/generated-sources/annotations: -g -nowarn -target 1.5 -source 1.5 -Xlint:deprecation

########################################################################################

```
