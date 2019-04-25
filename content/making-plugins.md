---
title: "Making Plugins"
date: 2018-07-25T10:59:38-07:00
anchor: "making-plugins"
weight: 1100
---

An Anypaste plugin is just an executable file (Bash will be used for all examples, but you can use any language you wish). This executable file is called with a single argument, which instructs the plugin on what to do. Additional data is not passed on the command line, but rather supplied through environment variables which the plugin can read at will. Here's a list of "commands" (the command line arguments) that can be passed to your plugin, and what your plugin should do in each situation:

## `check_eligibility`
The plugin  should determine whether the file being uploaded is compatible with this plugin. Typically, this involves checking that `$ap_mime` is a supported MIME type and that `$ap_size` is not over the site's size limit. The plugin should exit with an exit code of `0` if it's compatible, or non-zero if it is incompatible. This step should *not* involve any sort of network communications.

## `upload`
The plugin should perform the actual upload. Typically this involves using `curl` to upload the file at `$ap_path`, using whatever API the site provides. It might also use `$ap_human_name` to set the name of the file on the site being uploaded to, if the site supports that. Any warnings, errors, or progress bars should be outputted to stderr. If the upload completes successfully, the plugin should output a blank line to stdout, followed by the links, followed by another blank line. Each "link" should consist of some sort of label, followed by `:`, then followed by the actual link. Here's an example output:

```

Link: https://imgur.com/abcdef
Direct: https://i.imgur.com/abcdef.png
Edit: https://imgur.com/edit/abcdef/secret
Delete: https://imgur.com/delete/abcdef/secret

```

Your plugin should try to use "standard" names before the `:` whenever possible. This makes Anypaste's behavior more consistent, and makes it easier to use inside of other scripts. If there's something special about a link that a user should know, it's better to output it to stderr before the links rather than stdout with the links. When in doubt, look at the built-in plugins and try to act as similarly to them as possible.

Exit with a code of `0` if the upload was successful, or non-zero otherwise.

## `get_info`
The plugin should output "static" information about itself (metadata). Most of the [environment variables](#env) will *not* be available during this step. Your plugin should output its information in an ini-like format. Each "section" should start with `[section-name]`, then any lines after that until the next section are the contents. Blank lines are ignored. For example:

```
[description]
This is a cool plugin for uploading to imgur.com
[tags]
permanent
editable
deletable
[config]
required|imgur_api_public|Public API key
requied|imgur_api_secret|Private API secret
```

List of possible sections:

 - `name`: A human-readable name of the plugin. Often just a capitalized version of the machine-readable name.
 - `description`: A human-readable description of what this plugin does.
 - `tags`: The plugin's [tags](#cli), line-separated.
 - `config`: Has lines in the format `requiredness|name|description`. Each is an additional environment variable/configuration option that the user may supply via `anypaste.conf`. `requiredness` should be either `optional`, in which case it is purely cosmetic for display in `anypaste -l`, `recommended`, which will trigger a warning whenever the plugin is run without that option, and `required`, which will consider the plugin incompatible if that option is missing. `name` is the name of the environment variable for this option. `description` is cosmetic and human-readable.
 
### Aside: Config options
 
Config options are just environment variables which are set in the config file. You don't have to do anything special to get access to them. Keep in mind that they are in a "global" scope, so name them in a way that they don't interfere with other config options (e.g, don't name an option "api_key"; instead, use "imgur_api_key")

## Example plugins

The official [example plugin](https://github.com/markasoftware/anypaste-thinimg) for [ThinImg](http://thinimg.com) is a great learning resource. However, ThinImg is very simple, and we don't make use of some of the features plugins can have. If you want to see more fleshed-out plugins, look in the first several hundred lines of the main Anypaste source code -- that's where all the built-in plugins are.
