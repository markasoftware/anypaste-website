---
title: "Plugins"
date: 2018-07-25T11:04:05-07:00
anchor: "plugins"
weight: 1000
---

Anypaste plugins are each single executable files (except for the built-in ones, which are bundled inside the main Anypaste executable). The recommended way to "install" a plugin is to download it from its author's website (hopefully a GitHub release), mark it as executable (`chmod +x plugin-file`), then put it in `~/.anypaste-plugins` (you may need to create this folder). Alternatively, you could put it anywhere in your `$PATH`. After that, you must enable the plugin by adding it to the `ap_plugins` array in your [config](#configuration) file. Remember that this array is in order of precedence -- if you put it at the end, it will almost never be used!

## Third party plugins

Want to see your plugin on this list? [Open an issue!](https://github.com/markasoftware/anypaste-website/issues/new)

Name | Description | Link
---|---|---
ThinImg | A simple plugin created mainly to serve as an example about how to make third-party plugins. See [Making Plugins](#making-plugins) for more information. | [GitHub](https://github.com/markasoftware/anypaste-thinimg)
