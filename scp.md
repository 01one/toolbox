SCP (Secure Copy Protocol) is a command-line utility that allows securely transfer files between hosts on a network. It uses SSH for data transfer and provides the same authentication and security.

### Upload a file to a remote server

```bash
scp /path/to/local/file.txt username@remote_host:/path/to/destination/
```

### Download a file from a remote server

```bash
scp username@remote_host:/path/to/remote/file.txt /path/to/local/destination/
```

### Transfer an entire directory

```bash
scp -r /path/to/local/directory username@remote_host:/path/to/destination/
```

### Specify a different port

```bash
scp -P 2222 /path/to/local/file.txt username@remote_host:/path/to/destination/
```


- `-r`: Recursively copy entire directories
- `-P port`: Specify a different port (capital P)
- `-p`: Preserve modification times, access times, and modes from the original file
- `-q`: Quiet mode - don't show progress or warning messages
- `-C`: Compress data during transfer
- `-l limit`: Limit bandwidth used (in Kbit/s)
