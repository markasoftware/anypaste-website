---
title: "Command-line options"
date: 2018-06-10T13:04:06-07:00
anchor: "cli"
weight: 200
---

All command-line options are documented in `anypaste -h` as well as here.

* `-p`: Specify part of a plugin name to use.
* `-f`: Skip compatibility checks (force).
* `-i`: Interactive mode. Check it out, super cool!
* `-n`: Specify a custom name for the file (displayed only on certain sites).
* `-c`: Specify a path to a custom configuration file.
* `-C`: Create a default configuration file. Everything will be commented out by default. See [Configuration](#configuration) for more info.
* `-l`, `--list`: List all currently installed plugins in human-readable form. Can be combined with other options, if so it will list the plugins that would otherwise be attempted for upload.
* `--list-machine`: Same as `-l`, but for use inside of other scripts. It prints the raw `get_static_info` output from each plugin, with a blank line between plugins and trailing.
* `-x`, `--copy`, `--notify`: See [Post-Upload Hooks](#hooks).
* `-v`, `--version`: Print version.
* `-h`, `--help`: Print help text.
