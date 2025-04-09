# Archive Commands

## ZIP

### Create a ZIP archive

#### Compress all files in current directory
```bash
zip archive.zip *
```

#### Compress a directory and its contents (recursive)
```bash
zip -r archive.zip directory_name/
```

#### Compress multiple specific files
```bash
zip archive.zip file1.txt file2.jpg document.pdf
```

#### Compress with password protection
```bash
zip -e archive.zip file1.txt file2.jpg
```

### Extract a ZIP archive

#### Extract to current directory
```bash
unzip archive.zip
```

#### Extract to a specific directory
```bash
unzip archive.zip -d /path/to/extract/
```

#### Extract a specific file from archive
```bash
unzip archive.zip specific_file.txt
```

#### List contents without extracting
```bash
unzip -l archive.zip
```

#### Test archive integrity
```bash
unzip -t archive.zip
```

## TAR Commands (common on Linux/Unix)

### Create TAR archives

#### Create a tar archive
```bash
tar -cvf archive.tar directory/
```

#### Create a gzipped tar archive
```bash
tar -czvf archive.tar.gz directory/
```

#### Create a bzip2 compressed tar archive
```bash
tar -cjvf archive.tar.bz2 directory/
```

### Extract TAR archives

#### Extract a tar archive
```bash
tar -xvf archive.tar
```

#### Extract a gzipped tar archive
```bash
tar -xzvf archive.tar.gz
```

#### Extract a bzip2 compressed tar archive
```bash
tar -xjvf archive.tar.bz2
```

#### Extract to a specific directory
```bash
tar -xvf archive.tar -C /path/to/extract/
```

## Other Archive Commands

### 7z (7-Zip)

#### Create a 7z archive
```bash
7z a archive.7z directory/
```

#### Extract a 7z archive
```bash
7z x archive.7z
```

### RAR

#### Create a RAR archive
```bash
rar a archive.rar directory/
```

#### Extract a RAR archive
```bash
rar x archive.rar
```

## Command Options Explained

### ZIP Options
- `-r`: Recursive (include subdirectories)
- `-e`: Encrypt (password protect)
- `-q`: Quiet mode (less verbose)
- `-d`: Specify destination directory for extraction
- `-l`: List contents without extracting
- `-t`: Test archive integrity

### TAR Options
- `c`: Create new archive
- `x`: Extract files
- `v`: Verbose (show progress)
- `f`: Specify filename
- `z`: Filter through gzip
- `j`: Filter through bzip2
- `C`: Change to directory before performing operations
