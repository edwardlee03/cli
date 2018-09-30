
This command **displays system wide information regarding the Docker installation.**
Information displayed includes the kernel version, number of containers and images.
The number of images shown is the number of unique images. The same image tagged
under different names is counted only once.

**显示有关Docker安装的系统范围信息。**
显示的信息包括内核版本，容器和镜像的数量。
显示的镜像数量是唯一镜像的数量，标记在不同名称下的相同镜像仅计算一次。

If a format is specified, the given template will be executed instead of the
default format. Go's **text/template** package
describes all the details of the format.

Depending on the storage driver in use, additional information can be shown, such
as pool name, data file, metadata file, data space used, total data space, metadata
space used, and total metadata space.

取决于使用的存储驱动程序，可以显示其他信息，例如池名称，数据文件，元数据文件，
使用的数据空间，总的数据空间，使用的元数据空间以及总的元数据空间。

The data file is where the images are stored and the metadata file is where the
meta data regarding those images are stored. When run for the first time Docker
allocates a certain amount of data space and meta data space from the space
available on the volume where `/var/lib/docker` is mounted.

**数据文件**是**存储`镜像`的位置**，**元数据文件**是**存储**关于这些**`镜像的元数据`的位置**。

# EXAMPLES/示例

## Display Docker system information/显示Docker系统信息

Here is a sample output for a daemon running on Ubuntu, using the overlay2
storage driver:

    $ docker -D info
    Containers: 14
     Running: 3
     Paused: 1
     Stopped: 10
    Images: 52
    Server Version: 1.13.0
    Storage Driver: overlay2
     Backing Filesystem: extfs
     Supports d_type: true
     Native Overlay Diff: false
    Logging Driver: json-file
    Cgroup Driver: cgroupfs
    Plugins:
     Volume: local
     Network: bridge host macvlan null overlay
    Swarm: active
     NodeID: rdjq45w1op418waxlairloqbm
     Is Manager: true
     ClusterID: te8kdyw33n36fqiz74bfjeixd
     Managers: 1
     Nodes: 2
     Orchestration:
      Task History Retention Limit: 5
     Raft:
      Snapshot Interval: 10000
      Number of Old Snapshots to Retain: 0
      Heartbeat Tick: 1
      Election Tick: 3
     Dispatcher:
      Heartbeat Period: 5 seconds
     CA Configuration:
      Expiry Duration: 3 months
     // 节点地址
     Node Address: 172.16.66.128 172.16.66.129
     // 管理者地址
     Manager Addresses:
      172.16.66.128:2477
    Runtimes: runc
    Default Runtime: runc
    Init Binary: docker-init
    containerd version: 8517738ba4b82aff5662c97ca4627e7e4d03b531
    runc version: ac031b5bf1cc92239461125f4c1ffb760522bbf2
    init version: N/A (expected: v0.13.0)
    Security Options:
     apparmor
     seccomp
      Profile: default
    Kernel Version: 4.4.0-31-generic
    Operating System: Ubuntu 16.04.1 LTS
    OSType: linux
    Architecture: x86_64
    CPUs: 2
    Total Memory: 1.937 GiB
    Name: ubuntu
    ID: H52R:7ZR6:EIIA:76JG:ORIY:BVKF:GSFU:HNPG:B5MK:APSC:SZ3Q:N326
    Docker Root Dir: /var/lib/docker
    Debug Mode (client): true
    Debug Mode (server): true
     File Descriptors: 30
     Goroutines: 123
     System Time: 2016-11-12T17:24:37.955404361-08:00
     EventsListeners: 0
    Http Proxy: http://test:test@proxy.example.com:8080
    Https Proxy: https://test:test@proxy.example.com:8080
    No Proxy: localhost,127.0.0.1,docker-registry.somecorporation.com
    Registry: https://index.docker.io/v1/
    WARNING: No swap limit support
    Labels:
     storage=ssd
     staging=true
    Experimental: false
    Insecure Registries:
     127.0.0.0/8
    Registry Mirrors:
      http://192.168.1.2/
      http://registry-mirror.example.com:5000/
    Live Restore Enabled: false

Mac:

    $ docker system info
      // 容器统计数据
      Containers: 38
       Running: 0
       Paused: 0
       Stopped: 38
      // 镜像的数量
      Images: 3
      // Docker服务器版本
      Server Version: 18.03.1-ce
      // 存储驱动程序
      Storage Driver: overlay2
       Backing Filesystem: extfs
       Supports d_type: true
       Native Overlay Diff: true
      // 日志记录驱动程序
      Logging Driver: json-file
      // 进程控制分组管理
      // CGroup是Control Groups的缩写，是Linux内核提供的一种可以限制、记录、隔离进程组(process groups)所使用的物力资源(如cpu memory i/o 等等)的机制
      // CGroup 是将任意进程进行分组化管理的 Linux 内核功能
      // CGroup 介绍、应用实例及原理描述 - https://www.ibm.com/developerworks/cn/linux/1506_cgroup/index.html
      Cgroup Driver: cgroupfs
      // 插件列表
      Plugins:
       // 数据卷
       Volume: local
       // 网络
       Network: bridge host ipvlan macvlan null overlay
       // 日志
       Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
      Swarm: error
       NodeID:
       Error: error while loading TLS certificate in /var/lib/docker/swarm/certificates/swarm-node.crt: certificate (1 - ijj7mmh80669gkbvqrpticrlw) not valid after Fri, 02 Feb 2018 14:28:00 UTC, and it is currently Fri, 28 Sep 2018 14:21:11 UTC: x509: certificate has expired or is not yet valid
       Is Manager: false
       Node Address: 192.168.65.2
      // 运行时环境
      Runtimes: runc
      Default Runtime: runc
      // 初始化二进制程序
      Init Binary: docker-init
      // containerd版本
      containerd version: 773c489c9c1b21a6d78b5c538cd395416ec50f88
      // 运行代码版本
      runc version: 4fc53a81fb7c994640722ac585fa9ca548971871
      // 初始化程序版本
      init version: 949e6fa
      // 安全选项
      Security Options:
       seccomp
        Profile: default
      // 内核版本
      Kernel Version: 4.9.87-linuxkit-aufs
      // 操作系统
      Operating System: Docker for Mac
      // 操作系统类型
      OSType: linux
      // 操作系统体系结构
      Architecture: x86_64
      // 中央处理器的数量
      CPUs: 2
      // 总内存
      Total Memory: 1.952GiB
      // 名称
      Name: linuxkit-025000000001
      // 标识
      ID: 7PD6:UEPX:WB5W:A3LL:BWNV:GYAE:WSQS:5ZOG:NBGQ:OLYH:IP5B:U5DD
      // Docker根目录
      Docker Root Dir: /var/lib/docker
      // 客户端调试模式
      Debug Mode (client): false
      // 服务端调试模式
      Debug Mode (server): true
       // 文件描述符的数量
       File Descriptors: 21
       // 协程的数量
       Goroutines: 40
       // 系统时间
       System Time: 2018-09-28T17:55:53.655733387Z
       // 事件监听器的数量
       EventsListeners: 2
      // HTTP代理
      HTTP Proxy: docker.for.mac.http.internal:3128
      // HTTPS代理
      HTTPS Proxy: docker.for.mac.http.internal:3129
      // Docker分发注册中心
      Registry: https://index.docker.io/v1/
      // 标签列表
      Labels:
      // 试验
      Experimental: true
      Insecure Registries:
       127.0.0.0/8
      // 实时还原已启用
      Live Restore Enabled: false

The global `-D` option tells all `docker` commands to output debug information.

The example below shows the output for a daemon running on Red Hat Enterprise Linux,
using the devicemapper storage driver. As can be seen in the output, additional
information about the devicemapper storage driver is shown:

    $ docker info
    Containers: 14
     Running: 3
     Paused: 1
     Stopped: 10
    Untagged Images: 52
    Server Version: 1.10.3
    Storage Driver: devicemapper
     Pool Name: docker-202:2-25583803-pool
     Pool Blocksize: 65.54 kB
     Base Device Size: 10.74 GB
     Backing Filesystem: xfs
     Data file: /dev/loop0
     Metadata file: /dev/loop1
     Data Space Used: 1.68 GB
     Data Space Total: 107.4 GB
     Data Space Available: 7.548 GB
     Metadata Space Used: 2.322 MB
     Metadata Space Total: 2.147 GB
     Metadata Space Available: 2.145 GB
     Udev Sync Supported: true
     Deferred Removal Enabled: false
     Deferred Deletion Enabled: false
     Deferred Deleted Device Count: 0
     Data loop file: /var/lib/docker/devicemapper/devicemapper/data
     Metadata loop file: /var/lib/docker/devicemapper/devicemapper/metadata
     Library Version: 1.02.107-RHEL7 (2015-12-01)
    Execution Driver: native-0.2
    Logging Driver: json-file
    Plugins:
     Volume: local
     Network: null host bridge
    Kernel Version: 3.10.0-327.el7.x86_64
    Operating System: Red Hat Enterprise Linux Server 7.2 (Maipo)
    OSType: linux
    Architecture: x86_64
    CPUs: 1
    Total Memory: 991.7 MiB
    Name: ip-172-30-0-91.ec2.internal
    ID: I54V:OLXT:HVMM:TPKO:JPHQ:CQCD:JNLC:O3BZ:4ZVJ:43XJ:PFHZ:6N2S
    Docker Root Dir: /var/lib/docker
    Debug mode (client): false
    Debug mode (server): false
    Username: gordontheturtle
    Registry: https://index.docker.io/v1/
    Insecure registries:
     myinsecurehost:5000
     127.0.0.0/8

You can also specify the output format:

    $ docker info --format '{{json .}}'
	{"ID":"I54V:OLXT:HVMM:TPKO:JPHQ:CQCD:JNLC:O3BZ:4ZVJ:43XJ:PFHZ:6N2S","Containers":14, ...}
