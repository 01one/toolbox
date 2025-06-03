# SSH Configuration

## Installation and Configuration

### Basic Setup
```bash
# Install SSH server
sudo apt update
sudo apt install openssh-server

# Enable SSH service
sudo systemctl enable sshd
```

### Restrict SSH to Local IP
```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Add or modify the following line
ListenAddress 192.168.1.100  # Replace with your local IP

# Restart the service
sudo systemctl restart sshd
```

### Connect to SSH Server
```bash
ssh username@server_ip_address
```

## Security Enhancements

### Two-Factor Authentication with Google Authenticator

1. Install Google Authenticator:
```bash
sudo apt-get update
sudo apt-get install libpam-google-authenticator
```

2. Run the setup:
```bash
google-authenticator
```

3. Configure PAM:
```bash
# Edit PAM configuration
sudo nano /etc/pam.d/sshd

# Add at the top of the file
auth required pam_google_authenticator.so
```

4. Update SSH configuration:
```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Set the following options
ChallengeResponseAuthentication yes
UsePAM yes
KbdInteractiveAuthentication yes
```

5. Apply changes:
```bash
sudo systemctl restart sshd
```

## Restrict or Disable SSH

### Restrict SSH to Localhost Only
```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Set listening address to localhost
ListenAddress 127.0.0.1

# Restart service
sudo systemctl restart ssh
```

### Stop SSH Service
```bash
# Stop the service
sudo systemctl stop ssh

# Disable automatic startup (optional)
sudo systemctl disable ssh

# Verify status
sudo systemctl status ssh
```

### Completely Disable SSH
```bash
# Stop and disable both service and socket
sudo systemctl stop ssh.socket
sudo systemctl disable ssh.socket
```
