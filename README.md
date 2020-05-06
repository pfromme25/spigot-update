# spigot-update

## Description

This tool automates the installation and update process of a spigot minecraft server.

## Dependencies

* python3

## Configuration

Each installation directive (spigot and spigot2 in the example below) defines a spigot server instance to update/install. The name can be freely picked.

* path: the directory of the spigot server
* start: init start command
* stop: init stop command
* isactive: return whether the server is active (or inactive) as a return code
* version: corresponds to buildtools --rev
* cache(optional): file to cache the version information in

```
[DEFAULT]
rootu = root
user = mc
logDir = /var/log/

[spigot]
path = /opt/mc/spigot
start = systemctl start spigot.service
stop = systemctl stop spigot.service
isactive = systemctl is-active --quiet spigot.service
version = latest
cache = /opt/mc/spigot.cache

[spigot2]
path = /opt/mc/spigot2
start = systemctl start spigot2.service
stop = systemctl stop spigot2.service
isactive = systemctl is-active --quiet spigot2.service
version = 1.15.2
```

## Logging

spigot-update logs output depending on log level (default: WARNING). In order to log the complete update process, level=INFO should be used.

## Usage

Updating the Server with verbose output to the command line:
```
spigot-update -v
```

You can also change the log level to enable even more verbose output:
```
spigot-update -v -l INFO