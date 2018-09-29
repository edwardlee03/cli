
**Connects a container to a network.** You can connect a container by name
or by ID. Once connected, the container can communicate with other containers in
the same network.

**将容器连接到网络。**
您可以按名称或ID连接容器。连接后，容器可以与同一网络中的其他容器通信。

```bash
$ docker network connect multi-host-network container1
```

You can also use the `docker run --network=<network-name>` option to start a container and immediately connect it to a network.

```bash
$ docker run -itd --network=multi-host-network --ip 172.20.88.22 --ip6 2001:db8::8822 busybox
```

You can pause, restart, and stop containers that are connected to a network.
A container connects to its configured networks when it runs.

If specified, `the container's IP address(es) is reapplied when a stopped
container is restarted.` If the IP address is no longer available, the container
fails to start. One way to guarantee that the IP address is available is
to specify an `--ip-range` when creating the network, and choose the static IP
address(es) from outside that range. This ensures that the IP address is not
given to another container while this container is not on the network.

如果指定，则在重新启动已停止的容器时重新应用容器的IP地址。
如果IP地址不再可用，则容器无法启动。

```bash
$ docker network create --subnet 172.20.0.0/16 --ip-range 172.20.240.0/20 multi-host-network
```

```bash
$ docker network connect --ip 172.20.128.2 multi-host-network container2
```

To verify the container is connected, use the `docker network inspect` command.
Use `docker network disconnect` to remove a container from the network.

使用`docker network inspect`验证容器是否已连接。

Once connected in network, containers can communicate using only another
container's IP address or name. For `overlay` networks or custom plugins that
support multi-host connectivity, containers connected to the same multi-host
network but launched from different Engines can also communicate in this way.

You can connect a container to one or more networks.
The networks need not be the same type.
For example, you can connect a single container bridge and overlay networks.

您可以将容器连接到一个或多个网络。网络不必是同一类型。
