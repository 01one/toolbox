# System Automatic Restart


## Method 1: Using Cron Jobs (Recurring Restarts)

Cron jobs allow you to schedule commands to run at specified intervals.

### Setting Up a Daily Restart at 3:00 AM

```bash
# Edit the crontab file
sudo crontab -e

# Add this line to restart daily at 3:00 AM
0 3 * * * /sbin/shutdown -r now
```

### Common Cron Schedule Patterns

| Schedule | Cron Expression | Description |
|----------|----------------|-------------|
| Daily at 1:00 AM | `0 1 * * * /sbin/shutdown -r now` | Restarts every day at 1:00 AM |
| Every Sunday at 4:00 AM | `0 4 * * 0 /sbin/shutdown -r now` | Restarts weekly on Sundays |
| Every 6 hours | `0 */6 * * * /sbin/shutdown -r now` | Restarts every 6 hours |

### Cron Format Explained

```
MIN HOUR DAY MONTH DAYOFWEEK COMMAND
```

- **MIN**: Minute (0-59)
- **HOUR**: Hour (0-23)
- **DAY**: Day of month (1-31)
- **MONTH**: Month (1-12)
- **DAYOFWEEK**: Day of week (0-6, where 0 is Sunday)
- **COMMAND**: Command to execute

## Method 2: One-Time Scheduled Restart

To schedule a one-time restart:

```bash
# Restart 24 hours from now
sudo shutdown -r +1440

# Restart at a specific time today
sudo shutdown -r 23:00

# Cancel a scheduled restart
sudo shutdown -c
```

### Checking Scheduled Shutdowns/Restarts

```bash
# Check if a shutdown/restart is scheduled
cat /run/systemd/shutdown/scheduled

# Cancel a scheduled shutdown/restart
sudo shutdown -c

# Schedule a restart at specific time (e.g., 11:00 PM)
# sudo shutdown -r 23:00

# view the scheduled shutdown if there is any
cat /run/systemd/shutdown/scheduled

# View scheduled shutdown in human-readable time format
awk -F= '/^USEC=/ { print $2 }' /run/systemd/shutdown/scheduled | awk '{ print strftime("%Y-%m-%d %H:%M:%S", $1 / 1000000) }'
```



## Method 3: Using systemd Timer (Modern Systems)

For systems using systemd, you can create a timer:

1. Create a service file:

```bash
sudo nano /etc/systemd/system/restart.service
```

Add the following content:

```
[Unit]
Description=System Restart Service

[Service]
Type=oneshot
ExecStart=/sbin/shutdown -r now

[Install]
WantedBy=multi-user.target
```

2. Create a timer file:

```bash
sudo nano /etc/systemd/system/restart.timer
```

Add the following content for a daily 3:00 AM restart:

```
[Unit]
Description=Daily System Restart Timer

[Timer]
OnCalendar=*-*-* 03:00:00
Persistent=true

[Install]
WantedBy=timers.target
```

3. Enable and start the timer:

```bash
sudo systemctl enable restart.timer
sudo systemctl start restart.timer
```

## Checking Your Scheduled Restarts

### For Cron Jobs
```bash
sudo crontab -l
```

### For Systemd Timers
```bash
systemctl list-timers
```

## Additional Notes

- Always test restart schedules during non-critical hours
- Consider setting up monitoring to verify restarts occur as expected
- For production systems, implement proper service recovery mechanisms
