# File System

[TOC]

## Anatomy of a Disk

### Partition Table
Every disk will have a partition table, this table tells the system how the disk is partitioned. This table tells you where partitions begin and end, which partitions are bootable, what sectors of the disk are allocated to what partition, etc. There are two main partition table schemes used, Master Boot Record (MBR) and GUID Partition Table (GPT).

### Partition
Disks are comprised of partitions that help us organize our data. You can have multiple partitions on a disk and they can't overlap each other. If there is space that is not allocated to a partition, then it is known as free space. The types of partitions depend on your partition table. Inside a partition, you can have a filesystem or dedicate a partition to other things like swap (we'll get to that soon).

#### MBR
+ Traditional partition table, was used as the standard
+ Can have primary, extended, and logical partitions
+ MBR has a limit of four primary partitions
+ Additional partitions can be made by making a primary partition into an extended partition (there can only be one extended partition on a disk). Then inside the extended partition you add logical partitions. The logical partitions are used just like any other partition.
+ Supports disks up to 2 terabytes

#### GPT
+ GUID Partition Table (GPT) is becoming the new standard for disk partitioning
+ Has only one type of partition and you can make many of them
+ Each partition has a globally unique ID (GUID)
+ Used mostly in conjunction with UEFI based booting

### Filesystem Structure
A filesystem is an organized collection of files and directories. In its simplest form, it is comprised of a database to manage files and the actual files themselves.

+ Boot block - This is located in the first few sectors of the filesystem, and it's not really used the by the filesystem. Rather, it contains information used to boot the operating system. Only one boot block is needed by the operating system. If you have multiple partitions, they will have boot blocks, but many of them are unused.
+ Super block - This is a single block that comes after the boot block, and it contains information about the filesystem, such as the size of the inode table, size of the logical blocks and the size of the filesystem.
+ Inode table - Think of this as the database that manages our files. Each file or directory has a unique entry in the inode table and it has various information about the file.
+ Data blocks - This is the actual data for the files and directories.





## File System Types

### ext2 (second extended file system)
+ ext2 was the default file system in several major Linux distributions until supplanted by ext3.
+ Almost fully compatible with ext2, ext3 also supports journaling (see below).
ext2 is still the file system of choice for flash-based storage media because its lack of a journal increases performance and minimizes the number of writes.
+ Because flash memory devices have a limited number of write operations, minimizing write operations increases the device’s lifetime.
+ However, contemporary Linux kernels also support ext4, an even more modern file system, with better performance and which can also operate in a journal-less mode.

### ext3 (third extended file system)
+ ext3 is a journaled file system designed to improve the existing ext2 file system.
+ A journal, the main feature added to ext3, is a technique used to minimize the risk of file system corruption in the event of sudden power loss.
+ The file systems keeps a log (or journal) of all the file system changes about to be made.
+ If the computer crashes before the change is complete, the journal can be used to restore or correct any eventual issues created by the crash.
+ The maximum file size in ext3 file systems is 32 TB.

### ext4 (fourth extended file system)
+ Designed as a successor of ext3, ext4 was created based on a series of extensions to ext3.
+ While the extensions improve the performance of ext3 and increase supported file sizes, Linux kernel developers were concerned about stability issues and were opposed to adding the extensions to the stable ext3.
+ The ext3 project was split in two; one kept as ext3 and its normal development and the other, named ext4, incorporated the mentioned extensions.
+ This is the most current version of the native Linux filesystems. It is compatible with the older ext2 and ext3 versions. It supports disk volumes up to 1 exabyte and file sizes up to 16 terabytes and much more. It is the standard choice for Linux filesystems

### Swap File System
+ The swap file system is used by Linux when it runs out of RAM.
+ Technically, it is a swap partition that does not have a specific file system, but it is relevant to the file system discussion.
+ When this happens, the kernel moves inactive RAM content to the swap partition on the disk.
+ While swap partitions (also known as swap space) can be useful to Linux computers with a limited amount of memory, they should not be considered as a primary solution.
+ Swap partition is stored on disk which has much lower access speeds than RAM.

### NFS (Network File System)
+ NFS is a network-based file system, allowing file access over the network.
+ From the user standpoint, there is no difference between accessing a file stored locally or on another computer on the network.
+ NFS is an open standard which allows anyone to implement it

### Btrfs
"Better or Butter FS" it is a new filesystem for Linux that comes with snapshots, incremental backups, performance increase and much more. It is widely available, but not quite stable and compatible yet.

### XFS
High performance journaling file system, great for a system with large files such as a media server.

### HFS Plus or HFS+ (Hierarchical File System Plus)
+ A file system used by Apple in its Macintosh computers.
+ The Linux kernel includes a module for mounting HFS+ for read-write operations.

### APFS (Apple File System)
An updated file system that is used by Apple devices. It provides strong encryption and is optimized for flash and solid-state drives.

### CDFS (Compact Disc File System)
CDFS was created specifically for optical disk media.





## File System Hierarchy

+ **/** - The root directory of the entire filesystem hierarchy, everything is nestled under this directory.
+ **/bin** - Essential ready-to-run programs (binaries), includes the most basic commands such as ls and cp.
+ **/boot** - Contains kernel boot loader files.
+ **/dev** - Device files.
+ **/etc** - Core system configuration directory, should hold only configuration files and not any binaries.
+ **/home** - Personal directories for users, holds your documents, files, settings, etc.
+ **/lib** - Holds library files that binaries can use.
+ **/media** - Used as an attachment point for removable media like USB drives.
+ **/mnt** - Temporarily mounted filesystems.
+ **/opt** - Optional application software packages.
+ **/proc** - Information about currently running processes.
+ **/root** - The root user's home directory.
+ **/run** - Information about the running system since the last boot.
+ **/sbin** - Contains essential system binaries, usually can only be ran by root.
+ **/srv** - Site-specific data which are served by the system.
+ **/tmp** - Storage for temporary files
+ **/usr** - This is unfortunately named, most often it does not contain user files in the sense of a home folder. This is meant for user installed software and utilities, however that is not to say you can't add personal directories in there. Inside this directory are sub-directories for usr/bin, /usr/local, etc.
+ **/var** - Variable directory, it's used for system logging, user tracking, caches, etc. Basically anything that is subject to change all the time

Conventionally, /dev/sdX is used by Linux to represent hard drives, with the trailing number representing the partition number inside that device.



## mount and umount

```bash
# Display all block devices
lsblk

#View files are being shared (need to install package nfs-common)
showmount -e <ip>    (The -e or --exports show the server’s export list)

# Display more detailed information on the mounted filesystems
mount

# Create the mount point
sudo mount -t ext4 <other_drive> </local/file/path>

# Mount the Shares on file system (requires sudo permissions)
sudo mount <ip:/file/path> </local/file/path>

# Unmount Share (requires sudo permissions)
umount </local/file/path>

# Remember that the kernel names devices in the order it finds them. What if our device name changes for some reason after we mount it? Well fortunately, you can use a device's universally unique ID (UUID) instead of a name
# View the UUIDS on your system for block devices
sudo blkid

# Mount with UUIDs
sudo mount UUID=<uuid> </local/file/path>
```

## Hard Links and Symbolic Links
**Hard link** creates another file that points to the same location as the original file (same inode). 

So if I modified the contents of myfile2 or myhardlink, the change would be seen on both, but if I deleted myfile2, the file would still be accessible through myhardlink. Here is where our link count in the ls command comes into play. The link count is the number of hardlinks that an inode has, when you remove a file, it will decrease that link count. The inode only gets deleted when all hardlinks to the inode have been deleted. When you create a file, it's link count is 1 because it is the only file that is pointing to that inode

**Symbolic link**, also called a symlink or soft link, is similar to a hard link in that applying changes to the symbolic link will also change the original file. Symbolic links are denoted by ->. Notice how I got a new inode number though, symlinks are just files that point to filenames. When you modify a symlink, the file also gets modified. Inode numbers are unique to filesystems, you can't have two of the same inode number in a single filesystem, meaning you can't reference a file in a different filesystem by its inode number. However, if you use symlinks they do not use inode numbers, they use filenames, so they can be referenced across different filesystems.
Although symbolic links have a single point of failure (the underlying file), symbolic links have several benefits over hard links:

+ Locating hard links is more difficult. Symbolic links show the location of the original file in the ls -l command.
+ Hard links are limited to the file system in which they are created. Symbolic links can link to a file in another file system.
+ Hard links cannot link to a directory because the system itself uses hard links to define the hierarchy of the directory structure. However, symbolic links can link to directories

```bash
# Creating a hardlink
ln <somefile> <somelink>

# Creating a symlink
ln -s myfile mylink

# Show symlinks and inode's number
ls -li
```



## Disk Usage

```bash
# System disk space usage and other details about your disk
df -T
df -h

# Another similar command
du -h
```

