# Overview:

Stratis provides a variety of storage management features by integrating layers of existing technologies:
* the device mapper framework and
* the XFS filesystem.

Stratis consists of two components.

First, the Stratis daemon, stratisd:
* manages collections of block devices and
* provides a D-Bus API.

Second, the Stratis command-line interface, stratis-cli:
* uses the D-Bus API to communicate with stratisd.

# Goal:

After completing this scenario, users will be able to manage local storage with the Stratis CLI.

# Concepts included in this scenario:

* Installing Stratis

* Querying stratisd version

* Starting and enabling Stratis

* Locating empty block devices

* Creating pools and filesystems

* Listing pools and filesystems

* Renaming pools and filesystems

* Mounting filesystems

* Adding block devices data/cache devices to an existing pool

* Listing block devices

* Snapshotting filesystems

* Destroying pools and filesystems