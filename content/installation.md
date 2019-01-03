---
title: "Installation"
date: 2018-06-10T11:09:11-07:00
anchor: "installation"
weight: 100
---

Anypaste is just a single, cross-platform executable! That's because it's a shell script. You can download it from [https://anypaste.xyz/sh](https://anypaste.xyz/sh), which will just redirect you to the raw file hosted on GitHub. 

```bash
sudo mkdir -p /usr/local/bin # only needed on macOS
sudo curl -Lo /usr/local/bin/anypaste https://anypaste.xyz/sh
sudo chmod +x /usr/local/bin/anypaste
```

### Dependencies

Bash, curl, and POSIX core utils are all you need. `ffprobe` is optional but can provide more accurate compatibility checking for media file types; typically it comes inside of an `ffmpeg` package.
