---
tags:
  - Linux
---
1. NOTE:

1. this doc assumes we are using the LVM file system and Volume Groups to extend storage and an Ubuntu image.
2. Depending on file system type, linux distro, and distro version – commands and options may vary slightly or not work at all.

3. Ensure you have a restore point
4. Ensure you've added the required storage to disk in vm solution (this doc is not including these steps)
5. Login via SSH as root to vm
6. Command: fdisk –l
7. Find the disk you are trying to extend, you should something like the following:

1. Disk </diskName/> 10GB, 8370192856123 Bytes, 948891471234 sectors
2. The above number should represent the total storage, including the added storage to the disk
3. If the total has not updated, you likely have to reboot the vm
4. Make note of the partition names

9. Command: fdisk </diskName/>
10. Command: n

1. All defaults should be fine
2. After all prompts, enter command: w, to save config

12. Command: fdisk –l

1. Find the disk and make note of the new partition name

14. Command: pvcreate </partitionName/>
15. Command: vgdisplay

1. Find and make note of the volume group you are trying to extend

17. Command: vgextend <vgName> </partitionName/>

1. if you run vgdisplay again, you should see the size of the partition matching the value of the Free PE/Size property for the Volume Group

19. Command: lvdisplay

1. Make note of the volume you are trying to extend and its LVPath property
2. If you are unsure which one to pick, the LVPatch value will likely patch the file system dir you are trying to increase

1. Df -h to determine the files system dir you are trying to update

21. Command: lvextend -L+5GB </LVPath/>

1. change the 5GB to the value you are trying to extend to
2. Reference: [lvextend(8): extend size of logidf -hcal volume - Linux man page (die.net)](https://linux.die.net/man/8/lvextend)

23. If you run lvdisplay again, you should see the logical volume size matching the total size after the extension
24. Command: df –h

1. Note that the filesystem dir is still not resized
2. Make note of the filesystem name/path
3. All we did was increase the volume size the file system dir references, but we have not told the file system to update and use the new space found in this resized volume

26. Command: resize2fs </filessystem/>

1. At this point you are done

28. Command: df –h

1. You should see the total size of the file system matching the final total after extension