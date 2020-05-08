# Create a snapshot

A snapshot of a filesystem is a read/writeable thinly provisioned point in time copy of the source filesystem. To create a snapshot, you will need the name of the pool in which the filesystem is located, the name of the filesystem, and the name of the snapshot of the filesystem.

Create a snapshot of the filesystem. This snapshot will be named my_snapshot.

`stratis filesystem snapshot my_pool my_fs my_snapshot`{{execute}}

Check that the snapshot was created successfully by listing the stratis filesystems.

`stratis fs`{{execute}}

<pre class="file">
 Pool Name  Name         Used     Created            Device                        UUID
 my_pool    my_fs        546 MiB  May 08 2020 12:19  /stratis/my_pool/my_fs        0f808d165a264b779cb9108f7176c098
 my_pool    my_snapshot  546 MiB  May 08 2020 12:29  /stratis/my_pool/my_snapshot  cf5ac541bb7440a9b1cf5b2ebe936f05
</pre>

You should see my_snapshot listed in the output.

# Access the snapshot to recover files

Here is an example of how a snapshot can be used to recover deleted files from a filesystem.

Delete the first file you created in Step 7.

`rm -f /mnt/test_mnt/my_first_file`{{execute}}

Check that my_first_file has been deleted.

`ls /mnt/test_mnt`{{execute}}

<pre class="file">
 my_second_file
</pre>

You can see that my_first_file has been removed from the directory, and only my_second_file remains.

You can now mount the snapshot and get access to both files, since the snapshot was created before the first file was deleted.
First, unmount the filesystem, my_fs, from the mount point, /mnt/test_mnt.

`umount /mnt/test_mnt`{{execute}}

Next, mount the snapshot, my_snapshot.

`mount /stratis/my_pool/my_snapshot /mnt/test_mnt`{{execute}}

Confirm that the snapshot was mounted successfully.

`mount`{{execute}}

<pre class="file">
 << OUTPUT ABRIDGED >>
 /dev/mapper/stratis-1-ab995c9fa31e43a281322465a744c911-thin-fs-cf5ac541bb7440a9b1cf5b2ebe936f05 on /mnt/test_mnt type xfs (rw,relatime,seclabel,attr2,inode64,sunit=2048,swidth=2048,noquota)
</pre>

You can now see the snapshot mounted on /mnt/test_mnt.

List the files in /mnt/test_mnt to see that my_first_file has been recovered.

`ls /mnt/test_mnt`{{execute}}

<pre class="file">
 my_first_file  my_second_file
</pre>

Both files are now listed!

# Copy the file back to the original filesystem

Now that you have access to the previously deleted file, my_first_file, you may want to copy it back into the original filesystem, my_fs.

To do this, copy the file, my_first_file into the home directory.

`cp /mnt/test_mnt/my_first_file ~`{{execute}}

Check that the file has been successfully copied. 

`ls ~`{{execute}}

<pre class="file">
 anaconda-ks.cfg  my_first_file  openscap_data  original-ks.cfg
</pre>

Unmount the snapshot and mount the original filesystem, similarly to the previous steps.

`umount /mnt/test_mnt`{{execute}}

`mount /stratis/my_pool/my_fs /mnt/test_mnt`{{execute}}

Copy the file, my_first_file to the filesystem, my_fs.

`cp ~/my_first_file /mnt/test_mnt`{{execute}} 

Lastly, confirm that my_first_file has been copied to /mnt/test_mnt.

`ls /mnt/test_mnt`{{execute}}

<pre class="file">
 my_first_file my_second_file
</pre>

The filesystem, my_fs, now contains the previously deleted file, my_first_file.
