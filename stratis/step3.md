# Locate an empty block device

A block storage device (blockdev) is a device that can read and write data in “blocks” of a given size.

We'll need to obtain empty blockdevs for this tutorial.

To do that, first use the lsblk utility to view a list of blockdevs on your machine.

`lsblk`{{execute}}

Within the list of of blockdevs, locate an empty blockdev. You can check whether or not a blockdev is empty using the blkid utility.

`blkid -p /dev/sdb`{{execute}}

If no partition table signature is displayed, then the blockdev is empty.