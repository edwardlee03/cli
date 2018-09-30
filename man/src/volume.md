
The `docker volume` command has **subcommands for managing data volumes.** A data
volume is a specially-designated directory that by-passes storage driver
management.

**用于管理数据卷的子命令。**
**数据卷**是一个特殊指定的目录，它绕过存储驱动程序管理。

**Data volumes persist data independent of a container's life cycle.** `When you
delete a container, the Docker daemon does not delete any data volumes.` You can
**share volumes across multiple containers.** Moreover, you can share data volumes
with other computing resources in your system.

**数据卷保持数据独立于容器的生命周期。**
删除容器时，Docker守护进程不会删除任何数据卷。您可以**跨多个容器共享数据卷**。
此外，您可以与系统中的其他计算资源共享数据卷。

To see help for a subcommand, use:

    docker volume COMMAND --help

For full details on using docker volume visit Docker's online documentation.
有关使用docker volume的完整详细信息，请访问Docker的在线文档。
