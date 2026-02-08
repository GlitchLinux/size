## Get actual sizes of folders and files the easy way

**Installation and Usage:**

1. **Save the script** as `size` (without `.py` extension) in `/usr/local/bin/` or any directory in your PATH:

```bash
sudo nano /usr/local/bin/size
```

2. **Make it executable**:

```bash
sudo chmod +x /usr/local/bin/size
```

3. **Usage examples**:

```bash
# Basic usage
size file.txt
size /folder/

# Recursive directory size
size -r /etc/
size --recursive /home/user/

# Specific units
size -k /path/to/file.txt
size -m /path/to/folder/
size -g large_file.iso
size -t massive_directory/

# Help
size -h
```

## lis full contents of directories by size:

** size --list feature examples:**

```bash
# Create list of files in directory sorted by size
size --list /var/log/
# Creates: /tmp/size_list_var_log_20240115_143022.txt
# Prompts: Show list of /var/log/: Y/n

# Recursive list
size --list -r /home/user/
# Creates: /tmp/size_list_home_user_recursive_20240115_143022.txt

# List with specific unit
size --list -m /etc/
# Sizes displayed in megabytes in the list

# Combination
size --list -r -g /var/www/
# Recursive list with sizes in gigabytes
```

**Features of the `--list` option:**

1. **Creates timestamped files** in `/tmp/` with descriptive names
2. **Shows top 20 entries** when prompted with 'Y'
3. **Includes metadata** in the file (date, recursive mode, total files)
4. **Handles long paths** by truncating for display
5. **Shows total size** and file count
6. **Fallback option** - if user cancels prompt, shows file location
7. **Works with unit flags** (`-k`, `-m`, `-g`, `-t`) for consistent formatting

**Example output:**
```
$ size --list -r /var/log/
Created list of 142 files
Total size: 184MB
List saved to: /tmp/size_list_var_log_recursive_20240115_143022.txt
Show list? [Y/n]: Y

====================================
Top 20 largest files in '/var/log/':
====================================
  1.       84.2MB  .../syslog.1
  2.       56.8MB  .../auth.log.1
  3.       12.4MB  .../kern.log.1
  4.        8.2MB  .../syslog
  5.        5.6MB  .../auth.log

... (15 more lines)
... and 122 more files in the complete list

Full list available at: /tmp/size_list_var_log_recursive_20240115_143022.txt
``` 
