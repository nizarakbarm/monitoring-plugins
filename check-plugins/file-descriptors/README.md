# Check "file-descriptors" - Overview

Checks the number of allocated file handles in percent. Depending on the file and user (e.g. running as 'icinga') sudo (sudoers) is needed.

We recommend to run this check every minute.


# Installation and Usage

Requirements:
* `sysctl`

```bash
./file-descriptors --warning 90 --critical 95
./file-descriptors --help
```


# States

* WARN or CRIT if usage of file descriptors in % is above a given threshold.


# Perfdata

* File descriptors (%)


# Credits, License

* Authors: [Linuxfabrik GmbH, Zurich](https://www.linuxfabrik.ch)
* License: The Unlicense, see LICENSE file.