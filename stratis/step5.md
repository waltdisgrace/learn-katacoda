# Add a block device to a pool

All pools contain a data tier, which contains one or more block devices used to store data. The block devices used to create the pool belongs to the pool's data tier.

You can add additional block devices to a pool as data devices, thereby increasing the disk space provided to Stratis devices. This is helpful when you have exhaused the available space initially allocated to the pool.

Add /dev/loop2 as a data device to my_pool.

`stratis pool add-data my_pool /dev/loop2`{{execute}}

Now list pools.

`stratis pool list`{{execute}}

<pre class="file">
Name                     Total Physical
my_pool  20 GiB / 41.64 MiB / 19.96 GiB
</pre>

You should see that my_pool has a size of 20GiB.

# List block devices

Now that the pool consists of multiple block devices, it may be useful to find out which block devices belong to which pools.

`stratis blockdev list`{{execute}}
