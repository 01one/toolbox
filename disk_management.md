# Disk and Partition Usage Commands

## List Block Devices and Partitions
```bash
lsblk
```

## Check Disk Space Usage
```bash
df -h
```

## Extend Root Partition

### Extend Logical Volume
```bash
sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
```

### Resize Filesystem
```bash
sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
```

### Verify New Size and Free Space
```bash
df -h
```

## To create and format new partition on a new disk (e.g., `/dev/sdb`)

### Create a New Partition
```bash
sudo fdisk /dev/sdb
```
Inside `fdisk`, enter the following commands:
- `n` - new partition
- `p` - primary partition
- `1` - partition number
- `[ENTER]` - accept default first sector
- `[ENTER]` - accept default last sector (use full disk)
- `w` - write changes and exit

### Format Partition with ext4 Filesystem
```bash
sudo mkfs.ext4 /dev/sdb1
```

### Create Mount Directory
```bash
sudo mkdir -p /mnt/hdd
```

### Mount the New Partition
```bash
sudo mount /dev/sdb1 /mnt/hdd
```

### Get the UUID of the Partition
```bash
sudo blkid /dev/sdb1
```
Copy the UUID output, example:
- `UUID="xxxx-xxxx-xxxx-xxxx"`

### Edit `/etc/fstab` to Mount at Boot
```bash
sudo nano /etc/fstab
```
Add this line (replace `xxxx-xxxx-xxxx-xxxx` with your actual UUID):
```plaintext
UUID=xxxx-xxxx-xxxx-xxxx /mnt/hdd ext4 defaults 0 2
```
Save and exit nano (`Ctrl+O`, `Enter`, `Ctrl+X`).

### Test `fstab` and Mounts
```bash
sudo mount -a
```

### Verify Mount
```bash
df -h /mnt/hdd
```
