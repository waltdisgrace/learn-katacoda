# Snapshot a filesystem

To create a snapshot of a filesystem, i.e. a read/writeable thinly provisioned point in time copy of the source filesystem, you'll need the name of the pool in which the filesystem is located, the name of the filesystem, and the name of the snapshot of the filesystem. We'll name the filesystem snapshot my_snapshot.

`stratis filesystem snapshot my_pool my_fs my_snapshot`{{execute}}