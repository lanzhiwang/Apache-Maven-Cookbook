## Apache Maven Assembly Plugin

### Introduction

The Assembly Plugin for Maven enables developers to combine project output into a single distributable archive that also contains dependencies, modules, site documentation, and other files.  Maven 的 Assembly 插件使开发人员能够将项目输出合并到一个单独的可分发存档中，该存档还包含依赖项、模块、站点文档和其他文件。

Your project can easily build distribution "assemblies" using one of the [prefabricated assembly descriptors](https://maven.apache.org/plugins/maven-assembly-plugin/descriptor-refs.html). These descriptors handle many common operations, such as packaging a project's artifact along with generated documentation into a [single zip archive](https://maven.apache.org/plugins/maven-assembly-plugin/descriptor-refs.html#bin). Alternatively, your project can provide its own [descriptor](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html) and assume a much higher level of control over how dependencies, modules, file-sets, and individual files are packaged in the assembly.  您的项目可以使用预制组件描述符之一轻松构建分发“组件”。 这些描述符处理许多常见的操作，例如将项目的工件与生成的文档一起打包到单个 zip 存档中。 或者，您的项目可以提供自己的描述符，并对依赖项、模块、文件集和单个文件在程序集中的打包方式承担更高级别的控制。

Currently it can create distributions in the following formats:  目前，它可以创建以下格式的发行版：

- zip
- tar
- tar.gz (or tgz)
- tar.bz2 (or tbz2)
- tar.snappy
- tar.xz (or txz)
- jar
- dir
- war
- and any other format that the ArchiveManager has been configured for

If your project wants to package your artifact in an uber-jar, the assembly plugin provides only basic support. For more control, use the [Maven Shade Plugin](http://maven.apache.org/plugins/maven-shade-plugin/).  如果您的项目想要将您的工件打包到 uber-jar 中，则程序集插件仅提供基本支持。 如需更多控制，请使用 Maven Shade Plugin。

To use the Assembly Plugin in Maven, you simply need to:  要在 Maven 中使用 Assembly Plugin，您只需：

- choose or write the assembly descriptor to use,  选择或编写要使用的程序集描述符，
- configure the Assembly Plugin in your project's `pom.xml`, and  在项目的 pom.xml 中配置 Assembly Plugin，以及
- run "mvn assembly:single" on your project.  在您的项目上运行“mvn assembly:single”。

To write your own custom assembly, you will need to refer to the [Assembly Descriptor Format](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html) reference.  要编写自己的自定义程序集，您需要参考程序集描述符格式参考。

### What is an Assembly?

An "assembly" is a group of files, directories, and dependencies that are assembled into an archive format and distributed. For example, assume that a Maven project defines a single JAR artifact that contains both a console application and a Swing application. Such a project could define two "assemblies" that bundle the application with a different set of supporting scripts and dependency sets. One assembly would be the assembly for the console application, and the other assembly could be a Swing application bundled with a slightly different set of dependencies.  “程序集”是一组文件、目录和依赖项，它们被组装成归档格式并分发。例如，假设一个 Maven 项目定义了一个包含控制台应用程序和 Swing 应用程序的 JAR 工件。这样的项目可以定义两个“程序集”，将应用程序与一组不同的支持脚本和依赖项集捆绑在一起。一个程序集是控制台应用程序的程序集，另一个程序集可能是捆绑了一组稍微不同的依赖项的 Swing 应用程序。

The Assembly Plugin provides a descriptor format which allows you to define an arbitrary assembly of files and directories from a project. For example, if your Maven project contains the directory "src/main/bin", you can instruct the Assembly Plugin to copy the contents of this directory to the "bin" directory of an assembly and to change the permissions of the files in the "bin" directory to UNIX mode 755. The parameters for configuring this behavior are supplied to the Assembly Plugin by way of the [assembly descriptor](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html).  程序集插件提供了一种描述符格式，允许您定义项目中文件和目录的任意程序集。例如，如果您的Maven项目包含目录“src/main/bin”，您可以指示Assembly Plugin将该目录的内容复制到程序集的“bin”目录中，并更改其中文件的权限“bin”目录到 UNIX 模式 755。用于配置此行为的参数通过程序集描述符提供给程序集插件。

### Goals

The main goal in the assembly plugin is the [single](https://maven.apache.org/plugins/maven-assembly-plugin/single-mojo.html) goal. It is used to create all assemblies.

For more information about the goals that are available in the Assembly Plugin, see [the plugin documentation page](https://maven.apache.org/plugins/maven-assembly-plugin/plugin-info.html).

### Assembly and Component Descriptor Schemas (XSD)

- http://maven.apache.org/xsd/assembly-2.0.0.xsd, http://maven.apache.org/xsd/assembly-component-2.0.0.xsd (for version 3.0 and higher)

- http://maven.apache.org/xsd/assembly-1.1.3.xsd, http://maven.apache.org/xsd/component-1.1.3.xsd (for version 2.5.4 and higher)

- http://maven.apache.org/xsd/assembly-1.1.2.xsd, http://maven.apache.org/xsd/component-1.1.2.xsd (for version 2.2 and higher)

- http://maven.apache.org/xsd/assembly-1.1.1.xsd, http://maven.apache.org/xsd/component-1.1.1.xsd (for version 2.2-beta-4 - 2.2-beta-5)

- http://maven.apache.org/xsd/assembly-1.1.0.xsd, http://maven.apache.org/xsd/component-1.1.0.xsd (for version 2.2-beta-1 - 2.2-beta-3)

- http://maven.apache.org/xsd/assembly-1.0.0.xsd, http://maven.apache.org/xsd/component-1.0.0.xsd (for version 2.1 and lower)

### Usage

General instructions on how to use the Assembly Plugin can be found on the [usage page](https://maven.apache.org/plugins/maven-assembly-plugin/usage.html). Some more specific use cases are described in the examples given below.

In case you still have questions regarding the plugin's usage, please have a look at the [FAQ](https://maven.apache.org/plugins/maven-assembly-plugin/faq.html) and feel free to contact the [user mailing list](https://maven.apache.org/plugins/maven-assembly-plugin/mailing-lists.html). The posts to the mailing list are archived and could already contain the answer to your question as part of an older thread. Hence, it is also worth browsing/searching the [mail archive](https://maven.apache.org/plugins/maven-assembly-plugin/mailing-lists.html).

If you feel like the plugin is missing a feature or has a defect, you can fill a feature request or bug report in our [issue tracker](https://maven.apache.org/plugins/maven-assembly-plugin/issue-management.html). When creating a new issue, please provide a comprehensive description of your concern. Especially for fixing bugs it is crucial that the developers can reproduce your problem. For this reason, entire debug logs, POMs or most preferably little demo projects attached to the issue are very much appreciated. Of course, patches are welcome, too. Contributors can check out the project from our [source repository](https://maven.apache.org/plugins/maven-assembly-plugin/scm.html) and will find supplementary information in the [guide to helping with Maven](http://maven.apache.org/guides/development/guide-helping.html).

### Examples

To provide you with better understanding on some usages of the Assembly Plugin, you can take a look into the examples which can be found [here](https://maven.apache.org/plugins/maven-assembly-plugin/examples/index.html).
