# partitioning using fdesk

1. connect ur sd card or usb 

2. lsblk and figure out the name of usb or sd card

3. sudo fdisk /dev/(name of ur device as showed on lsblk)

 **tldr fdisk**
 - List partitions:
   sudo fdisk -l

 - Start the partition manipulator:
   sudo fdisk {{/dev/sdX}}

## Inside fdisk:
```bash
1. TL;DR fdisk Commands:
2. - List partitions: sudo fdisk -l
3. - Start fdisk: sudo fdisk /dev/sdX
4. - Create a new partition: n
5. - Delete a partition: d
6. - Print partition table: p
7. - Write changes: w
8. - Quit without saving: q
9. - Display help: m
```
4. start partitioniing and then manipulate as u need


## DIFF BETWEEN EXTENDED AND PRIMARY PARTITIONS

**Primary Partition:**

Definition: Used directly for file systems or storage.
Limit: Up to four per disk with MBR.
Bootability: Can be marked as active for booting.
Usage: Typically for OS and essential data, supports various file systems like NTFS, FAT32, ext4.

**Extended Partition:**

Definition: Acts as a container for other partitions (logical partitions).
Limit: Only one per disk.
Logical Partitions: Allows creation of multiple partitions within it, bypassing the four-partition limit of MBR.
Bootability: Logical partitions are generally not bootable.
Usage: Organizes data and creates multiple storage areas when exceeding four partitions on a disk. 


5. make the first sector Default (entry point of the first partition)

6. if i want it 4 GB   -> make last sector +4G


7. then try to write the file system on it 

```bash
sudo mkfs.ext3 /dev/sdb1

sudo mkfs.ext4 /dev/sdb2
```

8. lsblk -f

to get UUID of a partition


9. mount -a 
to mount all on fstab 


