# Protected and Persistent RAM Filesystem   


## Summary   
Many embedded systems have a block of non-volatile RAM seperate from normal system memory, i.e. of which the kernel maintains no memory page descriptors. 
For such systems it would be beneficial to mount a read/write filesystem over this "I/O memory", for storing frequently accessed data that must survive system reboots and power cycles or volatile data avoiding to write on a disk or flash. 
An example usage might be system logs under /var/log or debug information of a flight-recorder.   

Currently Linux has no support for a persistent, non-volatile RAM-based filesystem, persistent meaning the filesystem survives a system reboot or power cycle intact. 
The existing RAM-based filesystems such as tmpfs and ramfs have no actual backing store but exist entirely in the page and buffer caches, hence the filesystem disappears after a system reboot or power cycle.   

A relatively straight-forward solution is to write a simple block driver for the non-volatile RAM, and mount over it any disk-based filesystem such as ext2, ext3, ext4, etc.


## Reference  
- [pramfs](http://pramfs.sourceforge.net)   
