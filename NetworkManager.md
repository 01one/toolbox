## setup PPPoE (Point-to-Point Protocol over Ethernet) connection directly to linux pc 
get the device interface first
```bash
nmcli device status
```
```
Look for your Ethernet interface (e.g., `enp3s0`, `eth0`, etc.)
if its eth0 it will be like this
ifname eth0 con-name
```

```bash
nmcli connection add type pppoe ifname <interface_name> con-name "your_connection_name" pppoe.username isp_given_username pppoe.password isp_given_password autoconnect yes

```

## Verify connection
```bash
nmcli connection show
```

## to restart NetworkManager
```bash
sudo systemctl restart NetworkManager
```


## Basic connection management
```bash
# Connect manually
nmcli connection up "your_connection_name"

# Disconnect
nmcli connection down "your_connection_name"
```
