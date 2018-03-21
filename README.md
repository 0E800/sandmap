<h1 align="center">Sandmap</h1>

<h4 align="center">Sandmap is a tool supporting network and system reconnaissance using the massive Nmap engine.</h4>

<p align="center">
  <a href="https://img.shields.io/badge/Branch-master-green.svg">
    <img src="https://img.shields.io/badge/Branch-master-green.svg"
        alt="Master">
  </a>
  <a href="https://img.shields.io/badge/Version-v1.0.0-lightgrey.svg">
    <img src="https://img.shields.io/badge/Version-v1.0.0-lightgrey.svg"
        alt="v1.0.0">
  </a>
  <a href="https://travis-ci.org/profile/sandmap">
    <img src="https://travis-ci.org/profile/sandmap.svg?branch=master"
        alt="Master">
  <a href="http://www.gnu.org/licenses/">
    <img src="https://img.shields.io/badge/license-GNU-blue.svg"
        alt="GNU">
  </a>
</p>

<p align="center">
   <a href="#description">Description</a>
 • <a href="#how-to-use">How To Use</a>
 • <a href="#configuration-file">Configuration File</a>
 • <a href="#requirements">Requirements</a>
 • <a href="#logging">Logging</a>
 • <a href="#contributing">Contributing</a>
 • <a href="#project-architecture">Project Architecture</a>
 • <a href="#license">License</a>
</p>

<div align="center">
  <sub>Created by
  <a href="https://twitter.com/trimstray">trimstray</a> and
  <a href="https://github.com/trimstray/sandmap/graphs/contributors">
    contributors
  </a>
</div>

<br>

<p align="center">
    <img src="https://i.imgur.com/4tyDmK9.gif"
        alt="Master">
</p>

## Description

**Sandmap** is a tool supporting network and system reconnaissance using the massive Nmap engine. It provides a user-friendly interface, automates and speeds up scanning and allows you to easily use many advanced scanning techniques.

### Key Features

- simple CLI with the ability to run pure Nmap engine
- predefined scans included in the modules
- TOR support (with proxychains)
- multiple scans at one time

## How To Use

It's simple:

```bash
# Clone this repository
git clone https://github.com/trimstray/sandmap

# Go into the repository
cd sandmap

# Install
./setup.sh install

# Run the app
sandmap
```

> * symlink to `bin/sandmap` is placed in `/usr/local/bin`
> * man page is placed in `/usr/local/man/man8`

## Configuration file

The `etc/main.cfg` configuration file has the following structure:

```bash
# shellcheck shell=bash

# Specifies the default destination.
# Examples:
#   - dst="127.0.0.1,8.8.8.8"
dst="127.0.0.1"

# Specifies the default port number.
# Examples:
#   - port="80"
port="80"

# Specifies the default MAC address.
# Examples:
#   - iface="eth0"
iface="eth0"

# Specifies the default network interface.
# Examples:
#   - hwaddr="00:01:02:03:04:05"
hwaddr=""

# Specifies the default output type and path.
# Examples:
#   - report="xml"
report=""

# Specifies the TOR connection.
# Examples:
#   - tor="true"
tor=""

# Specifies the terminal type.
# Examples:
#   - terminal="internal"
terminal="internal"
```

## Requirements

**<u>Sandmap</u>** uses external utilities to be installed before running:

- [nmap](https://nmap.org/)
- [xterm](https://invisible-island.net/xterm/)
- [proxychains](http://proxychains.sourceforge.net/)

## Logging

After running the script, the `log/` directory is created and in it the following files with logs:

* `<script_name>.<date>.log` - all `_logger()` function calls are saved in it
* `stdout.log` - a standard output and errors from the `_init_cmd()` function are written in it. If you want to redirect the output from command, use the following structure: `your_command >>"$_log_stdout" 2>&1 &`

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Project architecture

    |-- LICENSE.md                 # GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
    |-- README.md                  # this simple documentation
    |-- CONTRIBUTING.md            # principles of project support
    |-- .gitignore                 # ignore untracked files
    |-- .travis.yml                # continuous integration with Travis CI
    |-- setup.sh                   # install sandmap on the system
    |-- bin
        |-- sandmap                # main script (init)
    |-- doc                        # includes documentation, images and manuals
        |-- man8
            |-- sandmap.8          # man page for sandmap
        |-- img                    # images (eg. gif)
    |-- etc                        # contains configuration files
    |-- lib                        # libraries, external functions
    |-- log                        # contains logs, created after init
    |-- modules                    # contains modules
    |-- src                        # includes external project files
        |-- helpers                # contains core functions
        |-- import                 # appends the contents of the lib directory
        |-- __init__               # contains the __main__ function
        |-- settings               # contains sandmap settings
    |-- templates                  # contains examples and template files
    |-- tmp                        # contains temporary files (mktemp)

## License

GPLv3 : <http://www.gnu.org/licenses/>

**Free software, Yeah!**
