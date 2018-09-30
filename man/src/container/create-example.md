
### Specify isolation technology for container (--isolation)/指定容器的隔离技术

This option is useful in situations where you are running Docker containers on
Windows. The `--isolation=<value>` option sets a container's isolation
technology. On Linux, the only supported is the `default` option which uses
**Linux namespaces**. On Microsoft Windows, you can specify these values:

* `default`: Use the value specified by the Docker daemon's `--exec-opt` .
  If the `daemon` does not specify an isolation technology, Microsoft Windows uses `process` as its default value.
* `process`: Namespace isolation only/仅限命名空间隔离.
* `hyperv`: Hyper-V hypervisor partition-based isolation.

Specifying the `--isolation` flag without a value is the same as setting `--isolation="default"`.

### Dealing with dynamically created devices (--device-cgroup-rule)/处理动态创建的设备

Devices available to a container are assigned at creation time. The
assigned devices will both be added to the `cgroup.allow` file and
created into the container once it is run. `This poses a problem when
a new device needs to be added to running container.`

当需要将新设备添加到正在运行的容器时，这会产生问题。

**One of the solution is to add a more permissive rule to a container
allowing it access to a wider range of devices.** For example, supposing
our container needs access to a character device with major `42` and
any number of minor number (added as new devices appear), the
following rule would be added:

```
docker create --device-cgroup-rule='c 42:* rmw' -name my-container my-image
```

其中一个解决方案是向容器添加更宽松的规则，允许它访问更广泛的设备。

Then, a user could ask `udev` to execute a script that would `docker exec my-container mknod newDevX c 42 <minor>`
the required device when it is added.

NOTE: initially present devices still need to be explicitly added to
the `create/run` command
