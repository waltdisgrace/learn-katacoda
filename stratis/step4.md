# Create a pool

A pool is a quantity of storage set aside by an administrator. A Stratis pool is created from one or more block devices. All pools must have a name; you will name the pool my_pool.

Create my_pool from the block device that you just identified, /dev/loop1.

`stratis pool create my_pool /dev/loop1`{{execute}}

`blkid`{{execute}}

<pre class="file"><< OUTPUT ABRIDGED >>

/dev/loop1: UUID="e28d5230c62349ae954c73373ffaca50" POOL_UUID="f2dd9526bc2a4653a431f322ed85b0f5" BLOCKDEV_SECTORS="20971520" BLOCKDEV_INITTIME="1588558543" TYPE="stratis"
</pre>

If you run blkid, you can see that /dev/loop1 is now in use and that it's type is "stratis".
The other loopback device is not in use, and therefore is not listed.

`stratis pool list`{{execute}}

You should see my_pool listed.

> **NOTE:** `stratis pool list` will provide you a list of any storage pools created on the system using stratis.

