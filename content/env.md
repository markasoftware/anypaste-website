---
title: "Environment Variables"
date: 2018-06-10T13:43:21-07:00
anchor: "env"
weight: 2000
---

[Plugins](#making-plugins) and [hooks](#hooks) have access to a number of environment variables. This is the primary way to get information about the currently uploading file.

Variable|Description
---|---
`ap_path`| The absolute path to the uploading file on-disk.
`ap_human_name`| The name specified using `-n` or inferred from the file name.
`ap_file_info`| Output of `file "$ap_path"`, contains lots of useful file metadata.
`ap_mime`| Mime type of the file (from `file --mime-type --brief "$ap_path"`).
`ap_ffprobe`| Output of `ffprobe -show_streams -show_format "$ap_path"`. Null if ffprobe is not installed. Often provides more accurate and reliable info that `file` can for audio and video.
`ap_size`| Size of the file, in bytes (from `wc -c`).
`ap_plugin`| The name of the plugin as it appears in `ap_plugins`.
`ap_version`| Current Anypaste version.
`ap_mac`| `true` if running on Mac, `false` otherwise.
<br>
There are many other variables set by Anypaste, but they are meant for internal use only and may change without warning.
