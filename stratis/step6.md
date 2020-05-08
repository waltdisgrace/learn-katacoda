# Create a filesystem

A filesystem is a hierarchy of directories that is used to organize files on a storage media. Multiple Stratis filesystems may be created from a pool. Like pools, all filesystems must have a name; you can name the filesystem my_first_fs.

Create my_first_fs from the pool that you created, my_pool.

`stratis filesystem create my_pool my_first_fs`{{execute}}

# List filesystems

At any point, you may list all existing Stratis filesystems.

`stratis filesystem list`{{execute}}

<pre class="file">
Pool Name  Name         Used     Created            Device                        UUID
my_pool    my_first_fs  546 MiB  May 07 2020 14:55  /stratis/my_pool/my_first_fs  e2688231488f40808507ede7502aad01
</pre>

You can see the new filesystem, my_first_fs, listed with the corresponding pool and additional information.

>**NOTE:** There's a shorter version of the filesystem listing command.

`stratis fs`{{execute}}

You should see the filesystem that you just created in the last step.

# Rename a filesystem

It is possible to rename a filesystem. This may be useful in a variety of cases, such as updating the name of a test filesystem to a production ready name.

You can rename filesystems with with the following command:

`stratis filesystem rename my_pool my_first_fs my_fs`{{execute}}

A filesystem list command will now yield the filesystem with its new name:

`stratis fs`{{execute}}

<pre class="file">
Pool Name  Name   Used     Created            Device                  UUID
my_pool    my_fs  546 MiB  May 07 2020 14:55  /stratis/my_pool/my_fs  e2688231488f40808507ede7502aad01
</pre>

The filesystem is now listed as my_fs under the Name column.
