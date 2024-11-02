# UNIX-Notes-(dwaraka)

## Overview
UNIX, initially developed in the 1960s by Ken Thompson and Dennis Ritchie at AT&T labs, was rewritten in C in the 1970s. Known for its multitasking and multi-user capabilities, UNIX has a variety of features, commands, and flavors that make it versatile and secure.

---

## Key Features of UNIX

- **Multi-user Support**: Enables multiple users to access the system simultaneously.
- **Multitasking**: Allows several tasks to run concurrently.
- **Shell Scripting**: Supports powerful scripting for automating tasks.
- **Process Tracking**: Monitors and manages system processes.
- **Communication**: Offers multiple methods for inter-process communication.
- **Security**: Provides robust security mechanisms.

---

## Comparison: UNIX vs. Windows

| Feature            | UNIX                       | Windows                        |
|--------------------|----------------------------|--------------------------------|
| Developed By       | AT&T Labs                  | Microsoft                      |
| Kernel             | Monolithic                 | Monolithic & Microkernel       |
| Interface          | CLI only                   | CLI and GUI                    |
| Security           | High                       | Moderate                       |
| File System        | Hierarchical               | NTFS                           |

---

## UNIX and Linux Flavors

- **UNIX**:
  - IBM-AIX 7.3
  - Solaris
  - HP-UX

- **Linux**:
  - Red Hat 9.4
  - Oracle Linux
  - Ubuntu 24.04
  - Fedora
  - Linux Mint

---

## Common UNIX Commands

### User and System Information

- **`who` / `w`**: Displays the users currently connected to the system.


  ```bash
  
  who -a      # Display all users, both active and inactive
  who -b      # Show last reboot time
  who -r      # Display current run level
  who -q      # it will count the connected users

## File and Directory Management

- **`ls`**: Lists files and directories.

  ```bash
  ls -l      # List files with details (permissions, owner, size, date)
  ls -a      # List all files including hidden files
  ls -R      # List directories and subdirectories recursively

### Touch 
- **`touch`  `dwakara`**: Creates an empty file or updates access/modification times.

  ```bash
  touch dwakara.txt
  ```
### CP 
- Copies files or directories :**`cp`**
  
  ```bash
   cp   # it will allows to copy the file from one path to another path with in sever.
- Copy a single file:

  ```bash
    cp source.txt destination.txt
  ```
- Copy directories recursively:

  ```bash
     cp -r dir1/ dir2/
  ```
### MV
  - Moves or renames files: **`mv`**

    ```bash
     mv oldname.txt newname.txt        # Rename file
     mv file.txt /path/to/destination  # Move file to destination
    ```
### MKDIR
  - Creates directories:**`mkdir`**

    ```bash
    mkdir new_directory               # Create a new directory
    mkdir -p /path/to/nested/directory # Create nested directories
     ```

### RM
  - Deletes files.

    ```bash
    rm file.txt                        # Delete a single file
    rm -r directory/                   # Delete directory recursively
    rm -f file.txt                     # Force delete a file
    ```
### File Viewing 
  ### Head 
  **`head`** :Shows the first lines of a file
  ```bash
     head -n 5 file.txt                 # Display the first 5 lines
  ```
 ### TAIL
 **`tail`** :Shows the last lines of a file.
 ```bash
    tail -n 10 file.txt                # Display the last 10 lines
 ```
### LESS
**`less`** :Views file content with navigation support.
   ```bash
      less file.txt                      # Open file with navigation support
   ```
**`more`** :it will also read the file content but it will not allows to perform the navigation keys.
### LINKING FILES
- Hard Link:
   ```bash
     ln source_file hardlink_name
   ```
- Soft Link:
  ```bash
     ln -s source_file softlink_name
  ```
### COMPARING FILES:
# CMP
**`cmp`**: Compares files byte by byte.
```bash
   cmp file1.txt file2.txt
```
# DIFF
**`diff`**: Compares files line by line.
```bash
   diff file1.txt file2.txt
``` 
### ARCHIVING AND COMPRESSING FILES
# TAR
**`tar`**: Archives multiple files.
```bash
   tar -cvf archive.tar files/        # Create a .tar archive
   tar -xvf archive.tar               # Extract a .tar archive
```
# GZIP
**`gzip`**: Compresses a file.
```bash
   gzip file.txt                      # Compress file
```
# GUNZIP
**`gunzip`** Decompresses **`zip`** files
```bash
   gunzip file.txt.gz                 # Decompress file
```
# GREP 


- The `grep` command stands for **Global Regular Expression Print** and is used to search for a string in one or more files.

## Syntax

```bash
grep <options> {pattern} filename
```
### OPTIONS
```bash
   grep -i "pattern" filename   #Ignore case sensitivity in the search.
   grep -n "pattern" filename   #Display line numbers along with matching lines.
   grep -c "pattern" filename   #Print only the count of lines that match the pattern.
   grep -l "pattern" filename   #Display only the names of files with matching lines.
   grep -e "pattern1" -e "pattern2" filename   #Allows searching for multiple strings at the same time.
   grep -w "pattern" filename   #Match whole words only.
   grep -r "pattern" /path/to/directory  #Search recursively in directories.
   grep -v "pattern" filename   #Display non-matching lines.
   grep -o "pattern" filename   #Print only the matching string, not the whole line.
   grep -A 2 "pattern" filename  #-A n : Print n lines after each matching line.
   grep -B 2 "pattern" filename  #-B n : Print n lines before each matching line.
   grep -C 2 "pattern" filename  #-C n : Print n lines both before and after each matching line.
```

# FIND 

- The `find` command is a powerful utility for searching files and directories in the filesystem.
- It provides flexibility with options for filtering results based on name, permissions, size, modification time, creation time, file extension, and more.

## Syntax
```bash
# find {options} {path} -type {f/d} {expression}

# `.` (dot) - Searches in the current directory.
# `/` (slash) - Searches in the root directory.
# `/path` - Searches in the specified path.
```
### Basic Search by Name

- 1. Search for a file by name in the current directory
```bash
       find . -type f -name abc.txt
```
- 2. Search for a directory by name in the current path
```bash
       find . -type d -name india
```
- 3. Search for all `.txt` files
```bash
       find . -type f -name "*.txt"
```
- 4. Search for a specific file (auth.log) in /var/log
```bash
       find /var/log -type f -name auth.log
```

# Search by Permissions

### The `-perm` option filters files by permission type.
# Permission Codes:
## 4: Read
## 2: Write
## 1: Execute

# Example Permission Codes:
```bash
# 777: Full permissions for owner, group, and others (rwxrwxrwx)
# 644: Read and write for owner, read-only for group and others (rw-r--r--)
```
## Find all files with `777` permissions in the current directory
```bash
find . -type f -perm 0777
```
# Search by Owner and Group

## 1. Search for files by group
```bash
find . -type f -group groupname
```
## 2. Search for files by user
```bash
find . -type f -user username
```bash
### Search for Empty Files

# Find empty files in the current directory
```bash
find . -type f -empty
```
# Search by Modification Time (`-mtime`)

## The `-mtime` option filters files based on the last modification time.
## `+N`: Modified more than N days ago
## `-N`: Modified within the last N days

## 1. Find files modified more than 10 days ago
```bash
find . -type f -mtime +10
```
## 2. Find files modified more than 100 days ago
```bash
find . -type f -mtime +100
```
## 3. Find files modified between 50 and 100 days ago
```bash
find . -type f -mtime +50 -mtime -100
```
## 4. Find files modified within the last hour
```bash
find . -type f -mmin -60
```
# Search and Delete Log Files

## 1. Find and delete log files older than 30 days in `/var/log`
```bash
find /var/log -type f -mtime +30 -name "*.log" -exec rm -rf {} \;
```
## 2. Find and delete `.log` files over 1GB in size
```bash
find . -type f -name "*.log" -size +1G -exec rm -rf {} \;
```
## 3. Find and delete `.txt` files larger than 1GB and modified more than 60 days ago
```bash
find . -type f -name "*.txt" -size +1G -mtime +60 -exec rm -rf {} \;
```
# Advanced Usage

## 1. Find a file using inode number
```bash
find . -type f -inum 10008
```
## 2. Find and change permissions of all `0777` files to `0644`
```bash
find . -type f -perm 0777 -exec chmod 0644 {} \;
```
## 3. Find and delete files larger than 1GB in `/var/log` (only top-level directory)
```bash
find /var/log -type f -maxdepth 1 -size +1G -exec rm -rf {} \;
```


  


                              















