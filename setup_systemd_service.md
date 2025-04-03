# Python Server Setup

Python server as a systemd service for automatic startup and management.

## Initial Setup

```bash
# Create and activate virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```



## System Username and Project Path  

get system username:  

```bash
whoami
```

absolute path of your project directory

```bash
pwd
```


## Create a Systemd Service

```bash
# Create a service file
sudo nano /etc/systemd/system/my_python_server.service
```

Add the following content to the file:

```ini
[Unit]
Description=Python Web Server
After=network.target

[Service]
User=your_username
WorkingDirectory=/path/to/your/project
Environment="PATH=/path/to/your/project/venv/bin"
ExecStart=/path/to/your/project/venv/bin/python /path/to/your/project/app.py
Restart=always  # Ensures the service restarts if it fails

[Install]
WantedBy=multi-user.target
```

## Manage the Service

```bash
# Reload systemd to apply changes
sudo systemctl daemon-reload

# Enable the service to start on boot
sudo systemctl enable my_python_server

# Start the service
sudo systemctl start my_python_server

# Check service status
sudo systemctl status my_python_server
```

## Common Service Commands

```bash
# Restart the server after making changes
sudo systemctl restart my_python_server

# Stop the server
sudo systemctl stop my_python_server

# Check logs for debugging
journalctl -u my_python_server --follow
```
