# Mount the filesystem

Mounting a filesystem means making the particular filesystem accessible at a certain point in the Linux directory tree. Your filesystem, by default is unmounted and thus cannot be used to store, read from, or write to files.

Choose a mount point, the directory in which the filesystem will be mounted. Note that if you do not choose an empty directory, the directory's previous contents will become hidden until the filesystem is unmounted. We'll mount our filesystem, my_fs, in the directory /mnt.

`mount /stratis/my_pool/my_fs /mnt`{{execute}}

# Add the mount point to /etc/fstab using the filesystem UUID

If you'd like, you could add the mount point to /etc/fstab, a table of descriptions of filesystems that can be quickly mounted with the short command mount /cdrom or configured to mount automatically when the system boots.

For this, you could add `/stratis/<pool name>/<file system name>`, but if you were to rename a pool or file system, you would also need to update `/etc/fstab`. Therefore, using file system UUID is recommended.

`blkid -p /stratis/my_pool/my_fs /stratis/my_pool/my_fs: UUID="a38780e5-04e3-49da-8b95-2575d77e947c" TYPE="xfs" USAGE="filesystem"`{{execute}}

`echo "UUID=a38780e5-04e3-49da-8b95-2575d77e947c /mnt xfs defaults 0 0" >> /etc/fstab`{{execute}}