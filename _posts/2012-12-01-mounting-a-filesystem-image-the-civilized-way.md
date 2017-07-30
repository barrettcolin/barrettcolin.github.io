---
layout: post
title: "Linux: mounting a filesystem image the civilized way"
categories: linux
---

You'll need kpartx:

```
sudo apt-get install kpartx
```
I'll be using 2012-10-28-wheezy-raspbian.img as an example

### List image partitions

```
sudo kpartx -l 2012-10-28-wheezy-raspbian.img
```
### Add partition mappings

```
sudo kpartx -a -v 2012-10-28-wheezy-raspbian.img
```

Mappings are created under /dev/mapper; the -v option additionally prints the list

### Mount partition (read-only)

Assuming you don't have anything under /mnt (make a new mount point and adjust the path accordingly if you do)

```
sudo mount /dev/mapper/loop0p2 /mnt -o ro
```

(using the mapping - /dev/mapper/loop0p2 - that was created (and printed) in the previous step)

### Unmount and remove mappings

```
sudo umount /mnt
sudo kpartx -d 2012-10-28-wheezy-raspbian.img
```

