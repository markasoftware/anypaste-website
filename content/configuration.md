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

The `export` preceding variable names tells Bash to pass these variables to subprocesses. The `export` is only necessary when configuring external plugins, i.e plugins that aren't included with Anypaste. This tells Bash to pass the variables on to subprocesses. All the properties listed below, and all properties for the built-in plugins, do not need `export`.

To create your configuration file, run `anypaste -C`. It will tell you where the config file was put, then you can edit it. It will typically be `~/.config/anypaste.conf` on Linux and `~/.anypaste.conf` on Mac. Everything is commented out by default.

| Option | Description | Default |
---|---|---
| `ap_plugins` | List of enabled plugins, in order of precedence | See config file |
| `ap_hook_policy` | If set to "greedy", [hooks](#hooks) will be run after every file uploaded. If set to "lazy", they will only be run just before Anypaste exits. | `lazy` |
