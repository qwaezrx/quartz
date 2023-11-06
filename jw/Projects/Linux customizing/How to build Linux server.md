---
tags:
  - CS/OS/Linux
---


I will use my desktop as a Linux server.

Will use Ubuntu 22.04.3 LTS desktop version
- Download link: https://ubuntu.com/download/desktop

- Used rsync for backup
	- https://www.vinchin.com/en/blog/backup-and-restore-linux-server.html

- Need to repartition the disk space
	- https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/installation_guide/sect-disk-partitions-making-room
	- For Non-Destructive Repartitioning
		1. Compress and backup existing data
		2. Resize the existing partition
		3. Create new partition(s)
