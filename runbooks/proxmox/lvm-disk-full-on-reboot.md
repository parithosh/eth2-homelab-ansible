# Disk full on reboot

## Description

If `nethermind` stops syncing due to no space left on the disk `/dev/mapper/ubuntu--vg-ubuntu--lv` even though the 
proxmox UI shows enough disk space, then it is due to the way LVM disk allocation is performed and the disk needs to 
just be extended. 

- Run `df -H` to check the disk space on the device, `/dev/mapper/ubuntu--vg-ubuntu--lv` would probably show as 
`100% used`. The space shown by `df -H` would probably be smaller than what has been provisioned in the proxmox UI. 
- Run `sudo fdisk -l` to list the disks allocated, you should see `/dev/sdaX` that shows the space provisioned in the UI. 
- This implies that we just need to resize the logical volume to use all the existing and free space of the volume group

## Solution

Run the following commands while SSH-ed into the VM:

- Run the cli tool with `lvm`
- It should show you `lvm>` in the terminal. Run `lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv` to resize 
- Run `exit` to exit the lvm tool
- We now need to resize the file system to use the new available space in the logical volume, this is done with 
`resize2fs /dev/ubuntu-vg/ubuntu-lv`
- You should now be able to check the disk space with `df -H`, the usage should be under `100%` and should show you the
space provisioned in the proxmox UI
- Restart nethermind with `sudo service nethermind start` or whatever command was used to start nethermind
- Check logs to confirm proper functionality