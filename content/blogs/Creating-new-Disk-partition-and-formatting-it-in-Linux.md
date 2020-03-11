+++
date = "2013-11-05"
title = "Creating a new Disk partition and formatting it in Linux"
tags = ["Disk Partition","Linux"]
categories = ["technical blogs"]
+++

__Disk utility__ can also be used to create new partitions and prepare them for use. Once a partition has been created, it must be formatted with a file system before it can be used. The standard file system used in Red Hat Enterprise Linux is ext4,the _Fourth Extended File system_.

In order to use the file system, we need to associate it with a _mount point_, and _empty directory_ on a file system that is already available. Then the contents of that file system can be browsed as if they are the contents of the mount point directory. This is called as _mounting the file system on the mount point_.

A file which only root can edit, `/etc/fstab`, list what partitions should have their file systems mounted on what mount points with which options, one partition per line, A typical line may look like this:

`/dev/sda6 /data ext4 defaults 1 2`

This indicates that the ext4 file system on the `/dev/sda6` partition should be mounted on the directory /data automatically using default options at _boot time_, and it should be backed up and checked for errors normally.

Once this is set, root can run `mount /data` to mount the file system above and `umount /data` to un-mount it.

![fstab](/images/fstab.jpeg)

/etc/fstab

**High- level steps for creating persistent storage**

1. Log into GNOME as a regular user.

2. Use __Disk Utility__ to create a partition. Enter the root password when prompted by the _Authenticaion is required to create a partition_ dialog.

3. Format the file system and assign it a label.

4. Test the file system by mounting it with __Disk Utility__ (It will be mounted on the directoy `/media/your-label`.)

5. Open a shell prompt with _Application_ —> _System Tools_ —> _Terminal_.

6. At the shell prompt, type `su` – to switch to a root shell.

7. As root, type the shell command `mkdir /data` to make an empty directory, `/data`, for the file system.

8. Use _gedit_ to add a line to `/etc/fstab` which will mount the ext4 file system in your new partition on your mount point (/data in this example), using default options as in the example above. Save `/etc/fstab`.

9. As root, run `umount /media/your-label`, then mount /data. verify that your partition is mounted on /data by highlighting the partition in **Disk Utility**.

10. Reboot to confirm that the file system mounts automatically on the desired mount point.