---
title: "Introduction"
date: 2018-08-10T22:05:40-07:00
anchor: "introduction"
weight: 1
---

Anypaste is a tool for uploading files to public-facing websites. Ideally, you can run `anypaste /path/to/file` and several things will happen:

1. Anypaste will use `file` and other utilities to determine the type of the file.
1. Anypaste will filter the list of plugins (supported hosting sites) to the ones which report they are compatible with the file.
1. Anypaste will pass control to the "best" supported plugin, which will upload the file to the site and send the link to your terminal.

Anypaste is written in Bash, and was designed to support Linux and macOS. It should also work on other *nix-y systems, like FreeBSD or the Windows Subsystem for Linux, but some desktop integration features (namely the `--copy` and `--notify` command line parameters) will probably have issues.
