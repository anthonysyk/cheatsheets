
### Show Volumes Names
```bash
root@scw-8838b4:~# lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
vda     252:0    0 46.6G  0 disk
|-vda1  252:1    0 46.5G  0 part /
|-vda15 252:15   0  100M  0 part /boot/efi
vdb     252:16   0 46.6G  0 disk
```

### Format the volume

```bash
root@c1-X-Y-Z-T:~# mkfs -t ext4 /dev/nbd1
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
610800 inodes, 2441406 blocks
122070 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2503999488
75 block groups
32768 blocks per group, 32768 fragments per group
8144 inodes per group
Superblock backups stored on blocks:
  32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
```

### Manually mounting an additional volume

```bash
root@c1-X-Y-Z-T:~# mkdir -p /mnt/data
root@c1-X-Y-Z-T:~# mount /dev/nbd1 /mnt/data
root@c1-X-Y-Z-T:~# ls -la /mnt/data/
total 24
drwxr-xr-x 3 root root  4096 Jan  1 00:07 .
drwxr-xr-x 3 root root  4096 Jan  1 00:07 ..
drwx------ 2 root root 16384 Jan  1 00:07 lost+found
```

