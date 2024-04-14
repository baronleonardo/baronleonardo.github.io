---
layout: post
title: Migrate nextcloud turnkey on proxmox
tags: linux
---

## How to
- there are two important pathes that need to be mounted from outside to the nextcloud container
    - /var/www/nextcloud
    - /var/www/nextcloud-data
    - NOTE: check [this](https://pve.proxmox.com/wiki/Linux_Container#_bind_mount_points) for how to
    - NOTE: don't forget to change the permission of these pathes from outside [explanation](https://pve.proxmox.com/wiki/Unprivileged_LXC_containers)
- do local backup
    - NOTE: [how to](https://www.turnkeylinux.org/faq/how-do-i-backup-local-storage-instead-s3)
- poweroff the old container
- create a new nextcloud container and do the usual installation (with the same configuration as the old container)
- mount the above passes as the old container
- power on the new container
- restore the backup
    - NOTE: [how to](https://www.turnkeylinux.org/faq/how-do-i-backup-local-storage-instead-s3)
- restart the container and that's it.
