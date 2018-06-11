---
title: "Installation"
date: 2018-06-10T11:09:11-07:00
anchor: "installation"
weight: 100
---

Anypaste is a shell script, and as such exists simply as a single executable file. You can download it directly from [GitLab](https://gitlab.com/markasoftware/anypaste/), mark it as an executable file, then drop it somewhere in your `$PATH`, for example `/usr/local/bin/`. If you're not one for following instructions, just run these commands:

```bash
sudo curl -o /usr/local/bin/anypaste https://gitlab.com/markasoftware/anypaste
sudo chmod +x /usr/local/bin/anypaste
```

Anypaste's dependencies are available out-of-the-box on most systems it supports. All it needs are recent versions of Bash, curl, and POSIX-compliant core utilities.
