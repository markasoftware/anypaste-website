---
title: "Plugins"
date: 2018-07-25T11:04:05-07:00
anchor: "plugins"
weight: 1000
---

Anypaste plugins are each single executable files (except for the built-in ones, which are bundled inside the main Anypaste executable). The recommended way to "install" a plugin is to download it from its author's website (hopefully a GitHub release), mark it as executable (`chmod +x plugin-file`), then put it in `~/.anypaste-plugins` (you may need to create this folder). Alternatively, you could put it anywhere in your `$PATH`. After that, you must enable the plugin by adding it to the `ap_plugins` array in your [config](#configuration) file. Remember that this array is in order of precedence -- if you put it at the end, it will almost never be used!

## Built-In Plugins 

Name | File Types | Extra Notes | Anypaste version
---|---|---|---
[Sendvid](http://sendvid.com) | Videos | | 1.0
[Streamable](https://streamable.com) | Videos | Requires authentication. | 1.0
[Gfycat](https://gfycat.com) | Videos (Gifs) | Short videos only. | 1.0
[Tinyimg](https://tinyimg.io) | Images | | 1.0
[Imgur](https://tinyimg.io) | Images | Uses a hardcoded API key. | 1.1
[Clyp](https://clyp.it) | Audio | Pretty crappy. | 1.1
[Hastebin](https://hastebin.com) | Text | Has frequent downtimes. | 1.0
[ix.io](https://ix.io) | Text | | 1.0
[Docdroid](https://docdroid.net) | Documents | Requires authentication. | 1.0
[Filemail](https://filemail.com) | Generic | 50GB upload limit (no authentication). | 1.1.3
[Transfer.sh](https://transfer.sh) | Generic | 10GB upload limit (no authentication). | 1.1
[Dmca.gripe](https://dmca.gripe) | Generic | 1GB upload limit. | 1.1
[File.io](https://file.io) | Generic | Files deleted after first download. | 1.0

## Third party plugins

Want to see your plugin on this list? [Open an issue!](https://github.com/markasoftware/anypaste-website/issues/new)

Name | Description | Plugin Homepage
---|---|---
[ThigImg](https://thinimg.com) | A simple plugin created mainly to serve as an example about how to make third-party plugins. See [Making Plugins](#making-plugins) for more information. | [GitHub](https://github.com/markasoftware/anypaste-thinimg)
