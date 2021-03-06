# Linux Disk Utils

## Wipe, Partition, and Format Drives

### list block devices
Locate the drive and its partitions
* `lsblk`
* `-f`: show file system, or more details 

### mount device
* `mount`
* `/dev/<drive><partition label>`
* `<path to mount point>`

### unmount device
* `umount`
* `<path to mount point>`


or

* `umount`
* `/dev/<device>`

### remove drive signature
Remove boot or raid signatures so that the drive is recognizable by Mac or Windows
* `wipefs`
* `-a`: all signatures
* `/dev/<device>`

### erase data
Write zeros to the device
* `dd`
* `if=/dev/zero`
* `of=/dev/<device>`
* `bs=4k`
* `status=progress && sync`

### partition
Add partition to device
* `cfdisk`
* `/dev/<device>`
* Terminal interactive GUI

### format
Format devce to certain format
* `mkfs`
* `-t <file system types>`
  * `vfat`: FAT32
  * `ext4`
  * `ntfs`
  * `bfs`: boot fs
  * etc.
* `/dev/<device><partition label>` 

## NFS
### server
[nfs tutorial](https://www.raspberrypi.org/documentation/configuration/nfs.md)
### client
MacOS or Linux
* Install NFS client `sudo apt install nfs-common`
* Show sever `showmount -e <server hostname or ip>`
* Mount `sudo mount -t nfs -o resvport,nolocks,rw <server hostname or ip>:<path to nfs server folder> <path to client folder>`
