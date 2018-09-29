
**Returns information about one or more volumes.** By default, this command renders
all results in a JSON array. You can specify an alternate format to execute a
given template is executed for each result. Go's https://golang.org/pkg/text/template/
package describes all the details of the format.

返回若干个磁盘存储卷的信息。

    $ docker volume inspect docker
    [
        {
            "CreatedAt": "2018-09-28T17:53:53Z",
            "Driver": "local",
            "Labels": {},
            "Mountpoint": "/var/lib/docker/volumes/docker/_data",
            "Name": "docker",
            "Options": {},
            "Scope": "local"
        }
    ]
