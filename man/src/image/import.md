
**Create a new filesystem image** from the contents of a tarball (`.tar`,
`.tar.gz`, `.tgz`, `.bzip`, `.tar.xz`, `.txz`) into it, **then optionally tag it.**

**从包的内容中创建一个新的文件系统镜像，然后选择标记它。**

# EXAMPLES

## Import from a remote location/从远程位置导入

    # docker image import http://example.com/exampleimage.tgz example/imagerepo

## Import from a local file/从本地文件导入

Import to docker via pipe and stdin:

    # cat exampleimage.tgz | docker image import - example/imagelocal

Import with a commit message. 

    # cat exampleimage.tgz | docker image import --message "New image imported from tarball" - exampleimagelocal:new

Import to a Docker image from a local file.

    # docker image import /path/to/exampleimage.tgz 

## Import from a local file and tag

Import to docker via pipe and stdin:

    # cat exampleimageV2.tgz | docker image import - example/imagelocal:V-2.0

## Import from a local directory/从本地目录导入

    # tar -c . | docker image import - exampleimagedir

## Apply specified Dockerfile instructions while importing the image/导入镜像时应用指定的Dockerfile指令
This example sets the docker image ENV variable DEBUG to true by default.

    # tar -c . | docker image import -c="ENV DEBUG true" - exampleimagedir

## When the daemon supports multiple operating systems/当守护进程支持多个操作系统时
If the daemon supports multiple operating systems, and the image being imported
does not match the default operating system, it may be necessary to add
`--platform`. This would be necessary when importing a Linux image into a Windows
daemon.

    # docker image import --platform=linux .\linuximage.tar

# See also
**docker-export(1)** to export the contents of a filesystem as a tar archive to STDOUT.
将文件系统的内容作为tar存档导出到标准输出控制台。
