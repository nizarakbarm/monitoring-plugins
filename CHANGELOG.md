# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project does NOT adhere to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## [Unreleased]

### Added

New features:

* Add hidden `.windows` files as indication for automatic compilation on/for Windows systems
* Add lib/distro3.py
* Add sudoers file for Fedora 35
* Icinga: duplicity Service Set
* New check infomaniak-swiss-backup-devices
* New check infomaniak-swiss-backup-products
* New check mysql-aria
* New check mysql-system
* New check mysql-traffic
* New check mysql-logfile
* New check strongswan-connections


### Changed

Changes in existing functionality:

* apache-httpd-status: Add insecure parameter
* dhcp-scope-usage3: Parse PercentageInUse locale-aware ([PR #551](https://github.com/Linuxfabrik/monitoring-plugins/pull/551))
* disk-io: Checks if psutil has a certain minimum version on systems with kernel 4.18+.
* disk-smart: Exclude zfs-volumes ([PR #539](https://github.com/Linuxfabrik/monitoring-plugins/pull/539))
* disk-smart: Properly handle Power_On_Hours_and_Msec attribute perfdata parsing ([PR #549](https://github.com/Linuxfabrik/monitoring-plugins/pull/549))
* disk-smart3: Now also runs on Windows ([PR #553](https://github.com/Linuxfabrik/monitoring-plugins/pull/553))
* file-age: Performance data aggregation on file_age check ([PR #544](https://github.com/Linuxfabrik/monitoring-plugins/pull/544))
* file-age: Improve perfdata labels
* file-age: shorten the message ([fix 559](https://github.com/Linuxfabrik/monitoring-plugins/issues/559))
* infomaniak-swiss-backup-devices: Increase default thresholds from 80/90% to 90/95%
* needs-restarting3: Debian Buster/bullseye command not found ([fix #572](https://github.com/Linuxfabrik/monitoring-plugins/issues/572))
* php-status: Change behavior when handling default values ([fix #540](https://github.com/Linuxfabrik/monitoring-plugins/issues/540))
* qts-\*: Increase default connect timeout from 3 to 6 seconds
* systemd-units-failed: Allow wildcards for the `--ignore` parameter ([fix #542](https://github.com/Linuxfabrik/monitoring-plugins/issues/542))
* lib/db_mysql3.py: Enhanced for new mysql-checks
* lib/disk3.py: Add file_exists() function
* Icinga: Adjust windows director definitions to the new folder structure
* Icinga: Increase windows service check intervals
* Revert Python 3.6+ `f`-strings to use `.format()` to be more conservative


### Fixed

Bug fixes:

* disk-io3: Fix python3 lib calls
* keycloak-version3: AttributeError: 'NoneType' object has no attribute 'group' ([fix #555](https://github.com/Linuxfabrik/monitoring-plugins/issues/))
* xca-cert3: Checks expiry date again


### Removed

For now removed features:

* Icinga: Remove gpsvc on windows



[Unreleased]: https://github.com/Linuxfabrik/monitoring-plugins/compare/2022030201...HEAD