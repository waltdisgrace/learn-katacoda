# Add a block device as a data device to an existing pool

All pools contain a data tier, which contains one or more blockdevs used to store data. The blockdev used to create the pool belongs to the pool's data tier. We can additional blockdevs to a pool as a data device.

Let's add /dev/sdc as a data device to my_pool.

`stratis pool add-data my_pool /dev/sdc`{{execute}}