```bash

################################################################################

$ tree -a /usr/local/Cellar/maven/3.6.3_1/libexec/
/usr/local/Cellar/maven/3.6.3_1/libexec/
├── bin
│   ├── m2.conf
│   ├── mvn
│   ├── mvnDebug
│   └── mvnyjp
├── boot
│   ├── plexus-classworlds-2.6.0.jar
│   └── plexus-classworlds.license
├── conf
│   ├── logging
│   │   └── simplelogger.properties
│   ├── settings.xml
│   └── toolchains.xml
└── lib
    ├── cdi-api-1.0.jar
    ├── cdi-api.license
14 directories, 79 files
$

################################################################################

$ tree -L 1  ~/.m2/
/Users/huzhi/.m2/
├── repository
└── settings.xml

1 directory, 1 file
$

################################################################################

$ mvn -h

usage: mvn [options] [<goal(s)>] [<phase(s)>]

Options:

-am,--also-make
If project list is specified, also build projects required by the list
如果指定了项目列表，还要构建列表所需的项目

-amd,--also-make-dependents
If project list is specified, also build projects that depend on projects on the list
如果指定了项目列表，还要构建依赖列表中项目的项目

-B,--batch-mode
Run in non-interactive (batch) mode (disables output color)
在非交互式（批处理）模式下运行（禁用输出颜色）

-b,--builder <arg>
The id of the build strategy to use
要使用的构建策略的 ID

-C,--strict-checksums
Fail the build if checksums don't match
如果校验和不匹配，则构建失败

-c,--lax-checksums
Warn if checksums don't match

-cpu,--check-plugin-updates
Ineffective, only kept for backward compatibility
无效，只保留向后兼容

-D,--define <arg>
Define a system property

-e,--errors
Produce execution error messages

-emp,--encrypt-master-password <arg>
Encrypt master security password

-ep,--encrypt-password <arg>
Encrypt server password

-f,--file <arg>
Force the use of an alternate POM file (or directory with pom.xml)
强制使用备用 POM 文件（或带有 pom.xml 的目录）

-fae,--fail-at-end
Only fail the build afterwards; allow all non-impacted builds to continue
仅在之后构建失败； 允许所有未受影响的构建继续

-ff,--fail-fast
Stop at first failure in reactorized builds
在反应式构建中的第一次失败时停止

-fn,--fail-never
NEVER fail the build, regardless of project result
永远不要让构建失败，无论项目结果如何

-gs,--global-settings <arg>
Alternate path for the global settings file
全局设置文件的备用路径

-gt,--global-toolchains <arg>
Alternate path for the global toolchains file

-h,--help
Display help information

-l,--log-file <arg>
Log file where all build output will go (disables output color)

-llr,--legacy-local-repository
Use Maven 2 Legacy Local Repository behaviour, ie no use of _remote.repositories. Can also be activated by using -Dmaven.legacyLocalRepo=true

-N,--non-recursive
Do not recurse into sub-projects

-npr,--no-plugin-registry
Ineffective, only kept for backward compatibility

-npu,--no-plugin-updates
Ineffective, only kept for backward compatibility

-nsu,--no-snapshot-updates
Suppress SNAPSHOT updates

-ntp,--no-transfer-progress
Do not display transfer progress when downloading or uploading

-o,--offline
Work offline

-P,--activate-profiles <arg>
Comma-delimited list of profiles to activate
选择使用的 profile

-pl,--projects <arg>
Comma-delimited list of specified reactor projects to build instead of all projects. A project can be specified by [groupId]:artifactId or by its relative path
要构建的指定反应堆项目的逗号分隔列表，而不是所有项目。 一个项目可以通过 [groupId]:artifactId 或者它的相对路径来指定

-q,--quiet
Quiet output - only show errors

-rf,--resume-from <arg>
Resume reactor from specified project

-s,--settings <arg>
Alternate path for the user settings file
选择 settings.xml 文件

-t,--toolchains <arg>
Alternate path for the user toolchains file

-T,--threads <arg>
Thread count, for instance 2.0C where C is core multiplied

-U,--update-snapshots
Forces a check for missing releases and updated snapshots on remote repositories
强制检查远程存储库上丢失的版本和更新的快照

-up,--update-plugins
Ineffective, only kept for backward compatibility

-v,--version
Display version information

-V,--show-version
Display version information WITHOUT stopping build

-X,--debug
Produce execution debug output
mvn 输出详细信息

$

################################################################################


```

