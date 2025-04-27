# Backlight,  Battery and GUI Management
## Controlling Display Backlight

### Find your backlight interface
```bash
ls /sys/class/backlight/
```
This will display available interfaces like `intel_backlight`, `acpi_video0`, or similar.

### Adjust backlight brightness
For Intel backlight (where 0 means turn off):
```bash
sudo tee /sys/class/backlight/intel_backlight/brightness <<< 0
```

## Battery Management

### Check battery percentage
```bash
upower -i /org/freedesktop/UPower/devices/battery_BAT0 | grep percentage
```


```bash
cat /sys/class/power_supply/BAT0/capacity
```
### power profile
```bash
powerprofilesctl get
```



#### GUI settings
Use the GUI to turn it on or off.

## Display Manager Control

### Check active display manager
If you're unsure which display manager is in use, check with:
```bash
ps aux | grep dm
```

### Stop/Start Display Manager
For LightDM:
```bash
sudo service lightdm stop
sudo service lightdm start
```

Or for GDM3:
```bash
sudo service gdm3 stop
sudo service gdm3 start
```

> **Note**: When your GUI is turned off (after stopping the display manager), you can still access the terminal:
> - Press `Ctrl+Alt+F2` through `Ctrl+Alt+F6` to switch to a virtual console
> - Log in with your username and password
> - Restart the GUI with: `sudo service lightdm start` or `sudo service gdm3 start` (depending on your system)
