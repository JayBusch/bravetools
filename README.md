[![Gitter](https://badges.gitter.im/bravetools/community.svg)](https://gitter.im/bravetools/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge) [![Go Report Card](https://goreportcard.com/badge/github.com/bravetools/bravetools)](https://goreportcard.com/report/github.com/bravetools/bravetools)

# Bravetools
Bravetools is an end-to-end System Container management platform. Bravetools makes it easy to configure, build, and deploy reproducible and isolated environments either on single machines or large clusters.

## Quickstart

To get started using Bravetools, download a platform-specific binary, rename it to `brave`, and add it to your PATH variable:

| Operating System | Binary | Version |
|------------------|--------|---------|
| Ubuntu           | [download](https://github.com/bravetools/bravetools/releases/download/1.54/brave-release-1.54-ubuntu) | release-1.54 |
| macOS            | [download](https://github.com/bravetools/bravetools/releases/download/1.54/brave-release-1.54-darwin) | release-1.54 |
| Windows 8/10     | [download](https://github.com/bravetools/bravetools/releases/download/1.54/brave-release-1.54-win.exe)  | release-1.54 |

> **NOTE:** Bravetools can be built from source on any platform that supports Go.

## Using Bravetools

To learn more about using Bravetools, please refer to our [Bravetools Documentation](https://bravetools.github.io/bravetools/).

## Installation

Ensure that your user is part of the `lxd group`:
```bash
sudo usermod --append --groups lxd USER
```

You may also need to install `zfsutils`:
```bash
sudo apt install zfsutils-linux
```

### Ubuntu

**Minimum Requirements**
* Operating System
  * Ubuntu 18.04 (64-bit)
* Hardware
  * 4GB of Memory
* Software
  * [Go](https://golang.org/)
  * [LXD >3.0.3](https://linuxcontainers.org/lxd/getting-started-cli/)

```bash
git clone https://github.com/bravetools/bravetools
cd bravetools
make ubuntu
```

If this is your first time setting up Bravetools, run `brave init` to initialise the required profile, storage pool, and LXD bridge.

### Mac OS

**Minimum Requirements**
* Operating System
  * MacOS Mojave (64-bit)
* Hardware
  * 4GB of Memory
* Software
  * [Go](https://golang.org/)
  * [Multipass](https://multipass.run/)

```bash
git clone https://github.com/bravetools/bravetools
cd bravetools
make darwin
```

If this is your first time setting up Bravetools, run `brave init` to initialise the required profile, storage pool, and LXD bridge.


### Windows

**Minimum Requirements**
* Operating System
  * Windows 8 (64-bit)
* Hardware
  * 8GB of Memory
* Software
  * [Go](https://golang.org/)
  * [Multipass](https://multipass.run/)
  * BIOS-level hardware virtualization support must be enabled in the BIOS settings.

```bash
git clone https://github.com/beringresearch/bravetools
cd bravetools
go build -ldflags=“-s -X github.com/bravetools/bravetools/shared.braveVersion=VERSION” -o brave.exe
```

Where VERSION reflects the latest stable release of Bravetools e.g `shared.braveVersion=1.53`

### Vagrant

1. Start Vagrant VM:

```bash
cd vagrant
vagrant up
vagrant ssh

// execute inside Vagrant VM
cd $HOME/workspace/src/github.com/bravetools/bravetools
make ubuntu
brave init
```

### Update Bravetools

To update existing installation of Bravetools for your platform:

```bash
git clone https://github.com/bravetools/bravetools
cd bravetools
make [darwin][ubuntu]
```

## Build Documentation

Follow installation instructions for [Jekyll](https://jekyllrb.com/) on your platform.
To serve documentation locally run:

```bash
cd docs
bundle exec jekyll serve --trace
```

and point your browser to http://127.0.0.1:4000/bravetools/.


## Command Reference

```
Usage:
  brave [command]

Available Commands:
  base        Build a base unit
  build       Build an image from a Bravefile
  configure   Configure local host parameters such as storage
  deploy      Deploy Unit from image
  help        Help about any command
  images      List images
  import      Import a tarball into local Bravetools image repository
  info        Display workspace information
  init        Create a new Bravetools host
  mount       Mount a directory to a Unit
  remove      Remove a Unit or an Image
  start       Start Unit
  stop        Stop Unit
  umount      Unmount <disk> from UNIT
  units       List Units
  version     Show current bravetools version

Flags:
  -h, --help   help for brave
```