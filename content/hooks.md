---
title: "Post-Upload Hooks"
date: 2018-06-10T13:11:31-07:00
anchor: "hooks"
weight: 500
---

Hooks run after Anypaste finishes uploading a file. Anypaste has two built-in hooks:

* Copy: Copies the link to your clipboard. Activated by adding the `-x` or `--copy` command-line options. By default it copies the "main" link, i.e. the one that begins with `Link: `. If you wish to copy a different link, say the "direct" links, you can set the `ap_copy_regex` config option to the regex pattern which will match the line containing the link you want. For direct links, you can do `export ap_copy_regex=Direct`.
* Notify: Sends a desktop notification when an upload completes. Activated with `--notify`. It uses `notify-send` on Linux to achieve a cross-desktop-environment experience, but some distros may not ship with it. On Mac, it should "just work" out of the box.

You can change how hooks work when multiple files are uploaded using `ap_hook_policy`. If it is set to `lazy` (the default), hooks will only run after the last file in a batch. If set to `greedy`, they will be run after every file.

Custom hooks can be added to the `ap_hooks` array in the config file. They have access to the same [environment variables](#env) as plugins, but additionally can see the output of the last plugin in `ap_last_stdout`. Custom hooks are able to work in combination with built-in plugins; both will run. This example will fun the first link outputted during each upload to 

```
ap_hook_policy=greedy
ap_hooks=('echo -n "$ap_last_stdout" | grep ^Link: | head -n 1 >> ~/Other/anypaste-links.txt')
```
