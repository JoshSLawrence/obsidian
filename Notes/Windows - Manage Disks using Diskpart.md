---
tags:
  - Microsoft/WindowsServer
---
## Diskpart

| Command                 | Description                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| `diskpart`              | run the diskpart utility. Works in both cmd and PowerShell         |
| `list disk`             | lists connected disks                                              |
| `select/sel disk <num>` | make the selected disk the active disk                             |
| `list partition/part`   | list the partitions that exist in the active disk                  |
| `list volume/vol`       | list the volumes that exist in the active disk                     |
| `sel part <num>`        | make the selected partition the active partition                   |
| `sel vol <num>`         | make the selected volume the active partition                      |
| `delete part`           | delete the active partition                                        |
| `extend`                | extend the active volume using all available free space            |
| `exit`                  | exits the diskpart utility and returns control to the active shell |

## Delete a partition

*This works in both, command prompt or PowerShell (remove comments if using cmd)*

```powershell
diskpart
list disk
select disk <num>
list partition
select partition <num>
delete partition override # force delete the selected partition
list partition # confirm the partition has been deleted
exit
```

## Extend a Volume

*Ensure the free space is next to the partition you wish to extend.  
If not, extension is not possible without removing existing partitions*

```powershell
diskpart
list disk
select disk <num>
list volume
select volume <num>
extend # extends volume using all available free space
list volume # confirm volume is extended
exit
```