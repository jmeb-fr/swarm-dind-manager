# Swarm-DinD

[![Release](https://img.shields.io/badge/release-v1.0.0-orange)](https://gitlab.com/jmeb-prj/swarm-dind-manager/-/releases/v1.0.1)
[![Software License](https://img.shields.io/badge/license-GPL--3.0--or--later-blue.svg)](https://gitlab.com/jmeb-prj/swarm-dind-manager/-/blob/master/COPYING)

## Goals

Help you to deploy and manage multiple Swarm clusters using DinD as nodes.

It's not a production-grade solution, DinD has some limitations and potential security issues (which can be mitigated with [rootless container](https://rootlesscontaine.rs/) or [Sysbox](https://github.com/nestybox/sysbox)). You should only use it to run cluster for local development.

You can manage clusters on a remote docker daemon but be aware that files on client host are used to keep track of some states. Especially, the lock system preventing concurrent modification on dind instances of a cluster won't work for users on a different host. 

## Requirements

* docker >=17.03
* bash >=4.3
* packages `coreutils` and depending on your distro `util-linux` or `bsdmainutils`<sup>1</sup>
* GNU version of common utilities (like `sed` or `grep`)<sup>1</sup>

<sup>1</sup> Try to limit dependencies to minimum in order to be easely installed on any environment, however a busybox-based one is not suitable.

## Manual installation

Download `swarm-dind` from the latest [release](https://gitlab.com/jmeb-prj/swarm-dind-manager/-/releases)

To install for all users
```
$ sudo install /path/to/downloaded/swarm-dind /usr/local/bin/swarm-dind
```

To install for current user only
```
$ install -D /path/to/downloaded/swarm-dind ~/.local/bin/swarm-dind
```

## Usage

Typical usage for creating a cluster will be:

Bootstrap the cluster
```
$ swarm-dind init
```

Set managers and workers to the cluster
```
$ swarm-dind apply 3 7
```

Remove all dind-nodes and configs when finished
```
$ swarm-dind destroy
```

For a complete list of commands and options run `swarm-dind -h` for generic docs or <code>swarm-dind <i>command</i> -h</code> for a specific command.

## License
The GNU General Public License v3.0 or later (GPL-3.0-or-later). Please see [license file](https://gitlab.com/jmeb-prj/swarm-dind-manager/-/blob/master/COPYING) for more information.
