# Flashing OT-One .img onto Micro SD Card on a Mac using Terminal


## 1. Find your micro SD card

In Terminal

> $ diskutil list

You should see something like:

```
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *251.0 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:          Apple_CoreStorage Macintosh HD            250.1 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1 (internal, virtual):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                  Apple_HFS Macintosh HD           +249.8 GB   disk1
                                 Logical Volume on disk0s2
                                 A606F389-312C-3039-9351-CF180683GA19
                                 Unencrypted
/dev/disk3 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *15.9 GB     disk3
   1:                 DOS_FAT_32 SD Card                 15.9 GB     disk3s1
```

Find the partition for your card and take note of the disk number. In the example above, the disk number is 3.


## 2. Format your micro SD card

> $ sudo diskutil eraseDisk FAT32 *NAME* MBRFormat /dev/disk3

*NAME* is whatever you set it to, but do not use brackets.

## 3. Unmount Disk

> $ diskutil unmountDisk /dev/disk3

## 4. Burn your micro SD card

> $ sudo dd bs=1m of=/dev/rdisk3 if=/path/to/ot-one.img

The r in rdisk3 is not a typo. It prevents the utility from buffering data before writing. Buffering causes the
operation to take much longer. Bet patient. It will look like nothing is happening until dd finishes, at which time you should enter:

> $ sync

## 5. Eject your micro SD card

> $ diskutil eject /dev/disk3

You're done!


Links:
- http://elinux.org/RPi_Easy_SD_Card_Setup#Flashing_the_SD_card_using_Mac_OS_X
- https://github.com/hypriot/flash
- http://odroid.com/dokuwiki/doku.php?id=en:odroid_flashing_tools


