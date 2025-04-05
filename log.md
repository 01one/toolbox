## watch the log file .. its will update in real time
```bash
tail -f logfile.log
```

## fixed total lines to watch updates
```bash
tail -n 100 -f logfile.log
```


## View entire log file with scrolling
```bash
less logfile.log
```
- Use arrow keys to navigate
- Press `/` followed by text to search
- Press `q` to quit

## Display first lines of a log file
```bash
head -n 20 logfile.log  # Shows first 20 lines
```

## Display last lines without following
```bash
tail -n 50 logfile.log  # Shows last 50 lines
```

## Filtering and Searching

## Filter logs in real-time
```bash
tail -f logfile.log | grep "ERROR"
```

## Highlight patterns while watching logs
```bash
tail -f logfile.log | grep --color=always "ERROR\|WARNING\|INFO"
```

## Search for pattern in log file
```bash
grep "Failed login" logfile.log
```

## Case-insensitive search
```bash
grep -i "error" logfile.log
```

## Show line numbers with matches
```bash
grep -n "exception" logfile.log
```

## Count occurrences of pattern
```bash
grep -c "404 Not Found" access.log
```

## Advanced Monitoring

## Watch multiple log files simultaneously
```bash
tail -f log1.log log2.log log3.log
```

## Monitor logs with timestamps
```bash
tail -f logfile.log | while read line; do echo "$(date +%T): $line"; done
```

## Filter by time range (using sed)
```bash
sed -n '/2025-01-01 10:00:00/,/2025-02-01 11:00:00/p' logfile.log
```

## Extract specific columns with awk
```bash
tail -f logfile.log | awk '{print $1, $4, $9}'  # Print columns 1, 4, and 9
```

## Log Analysis

## Count unique IP addresses in access log
```bash
cat access.log | awk '{print $1}' | sort | uniq -c | sort -nr
```

## Find the top 10 most common errors
```bash
grep "ERROR" logfile.log | cut -d: -f4 | sort | uniq -c | sort -nr | head -10
```

## Analyze HTTP status codes
```bash
cat access.log | grep -o 'HTTP/[0-9.]* [0-9]*' | cut -d' ' -f2 | sort | uniq -c | sort -nr
```

## Calculate average response time
```bash
awk '{sum+=$10; count++} END {print "Average response time:", sum/count, "ms"}' access.log
```

## Log Management

## Compress old logs
```bash
gzip logfile.log.1
```

## Archive logs older than 7 days
```bash
find /var/log -name "*.log" -type f -mtime +7 -exec gzip {} \;
```

## Rotate logs manually
```bash
mv logfile.log logfile.log.1
touch logfile.log
chmod 644 logfile.log
```

## Split large log files
```bash
split -b 100M large_logfile.log segment_
```

## Specialized Tools

## View logs with journalctl (systemd)
```bash
journalctl -u service-name -f
```

## Apache access log analysis with GoAccess
```bash
goaccess access.log -c
```

## Docker container logs
```bash
docker logs --tail 100 -f container_name
```

