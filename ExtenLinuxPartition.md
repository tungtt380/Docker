Ref link: https://networklessons.com/uncategorized/extend-lvm-partition

**Ref link:** https://networklessons.com/uncategorized/extend-lvm-partition

1. Create a new partition on hard disk.
`fdisk -l`
**`# fdisk /dev/sda`**

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): **n**
Command action
   e   extended
   p   primary partition (1-4)
**p**
Partition number (1-4): **3**
First cylinder (3917-7832, default 3917): 
Using default value 3917
Last cylinder, +cylinders or +size{K,M,G} (3917-7832, default 7832): 
Using default value 7832

Command (m for help): **w**
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks. 


2. Add the partition you just created as a physical volume.
`# fdisk -l`
3. Add the new physical volume to the volume group.
`# pvdisplay`
`# pvcreate /dev/sda3`
`# vgdisplay | grep Name`
  VG Name               vg_vmware
`# vgextend vg_vmware /dev/sda3`

4. Assign space from the volume group to the logical volume.
`# vgdisplay`
`# lvdisplay | grep Path`
  LV Path                /dev/centos/root
  LV Path                /dev/centos/home

5. Resize the filesystem.
`# lvextend -l +100%FREE /dev/vg_vmware/lv_root`
`# lvdisplay`
`xfs_growfs /dev/centos/home`
