Lists all the plugins that are currently installed. You can install plugins
using the `docker plugin install` command.
You can also filter using the `-f` or `--filter` flag.

列出当前安装的所有插件。
您可以使用`docker plugin install`命令安装插件。

## Filters

Filter output based on these conditions:
   - enabled=(true|false) - plugins that are enabled or not
   - capability=<string> - filters plugins based on capabilities (currently `volumedriver`, `networkdriver`, `ipamdriver`, or `authz`)

## Format

   Pretty-print plugins using a Go template.
   Valid placeholders:
      .ID - Plugin ID.
      .Name - Plugin Name.
      .Description - Plugin description.
      .Enabled - Whether plugin is enabled or not.

# EXAMPLES/示例
## Display all plugins/显示所有插件

    $ docker plugin ls
    ID                  NAME                                    DESCRIPTION                         ENABLED
    869080b57404        tiborvass/sample-volume-plugin:latest   A sample volume plugin for Docker   true
    141bf6c02ddd        vieux/sshfs:latest                      sshFS plugin for Docker             false

## Display plugins with their ID and names

    $ docker plugin ls --format "{{.ID}}: {{.Name}}"
    869080b57404: tiborvass/sample-volume-plugin:latest

## Display enabled plugins

    $ docker plugin ls --filter enabled=true
    ID                  NAME                                    DESCRIPTION                         ENABLED
    869080b57404        tiborvass/sample-volume-plugin:latest   A sample volume plugin for Docker   true

## Display plugins with `volumedriver` capability

    $ docker plugin ls --filter capability=volumedriver --format "table {{.ID}}\t{{.Name}}"
    ID                  Name
    869080b57404        tiborvass/sample-volume-plugin:latest
