# Create a pool with the block device

A pool is quantity of storage set aside by an administrator. A Stratis pool is created from one or more blockdevs. All pools must have a name; we will name our pool my_first_pool.

Let's create my_first_pool from the blockdev that we just identified, /dev/sdb. 

`stratis pool create my_first_pool /dev/sdb`{{execute}}

# List pools

At any point, you may list all existing Stratis pools.

`stratis pool list`{{execute}}

You should see the pool that you just created in the last step.

# Rename a pool

You can rename pools with with the following command:

`stratis pool rename my_first_pool my_pool`{{execute}}

A pool list command will now yield the pool with its new name:

`stratis pool list`{{execute}}