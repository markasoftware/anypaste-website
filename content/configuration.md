---
title: "Configuration"
date: 2018-06-11T11:10:09-07:00
anchor: "configuration"
weight: 400
---

Anypaste's configuration file is a small shell script which sets environment variables. As such, if you know how to write Bash, you know how to write Anypaste config. Here's a cheat sheet:

* Set variable (string): `export var_name='I am a string'`.
* Set variable (number): `export var_name=647`.
* Set array: `export arr_name=('I am a string' 42 'This is the third element')`.
* Comment: `# don't unset this or everything will break! Not sure why...`.

The `export` preceding variable names tells Bash to pass these variables to subprocesses. The `export` is only necessary when configuring external plugins, i.e plugins that aren't built-in to Anypaste.

To create your configuration file, run `anypaste -C`. It will tell you where the config file was put. It will typically be `~/.config/anypaste.conf` on Linux and `~/.anypaste.conf` on Mac. Everything is commented out by default.

Option | Description | Default
---|---|---
`ap_plugins` | List of enabled plugins, in order of precedence | See config file
`ap_hooks` | List of [hooks](#hooks) that are enabled by default | Empty
`ap_hook_policy` | If set to "greedy", hooks will be run after every file uploaded. If set to "lazy", they will only be run just before Anypaste exits. | `lazy`
`ap_unicode` | Whether to prettify things with unicode characters. Mainly used in `anypaste -l`. | `true`
`ap_color` | Whether to colorize the output. | `true`
`ap_copy_regex` | The regular expression to determine which line to copy from when `--copy` is used. | `.` (matches first line)
`ap_ua` | User-agent to use | `Anypaste 1.15` (or other version)
