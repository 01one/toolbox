# Virtual RAM in Linux

### Check the Swap Size
```
sudo swapon --show
```

### Disable the Swap
Disable the existing swap file:
```
sudo swapoff /swapfile
```

### Resize the swap file to for example 22.8GB
Increase as needed - 3 times the device RAM:
```
sudo fallocate -l 22.8G /swapfile
```

If fallocate is not available, use dd:
```
sudo dd if=/dev/zero of=/swapfile bs=1M count=23552
```

### Set Permissions
Ensure that only the root user can read and write to the swap file:
```
sudo chmod 600 /swapfile
```

### Set Up Swap Space
Activate the resized swap file:
```
sudo mkswap /swapfile
sudo swapon /swapfile
```

### Update Swap Information
Update the swap information in the /etc/fstab file:
```
sudo sed -i 's/\/swapfile.*/\/swapfile none swap sw 0 0/' /etc/fstab
```

### Check the changes
Verify the changes and reboot:
```
swapon --show
```

### Ensure Persistence Across Reboots
To ensure that the changes are persistent across reboots, you can check and update the /etc/fstab file:
```
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```

This command appends a new entry for the swap file to the /etc/fstab file, making the swap file configuration persistent.
