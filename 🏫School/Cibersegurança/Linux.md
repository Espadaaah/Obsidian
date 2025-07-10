# Linux Commands
### Navigation

```bash
pwd                  # Print working directory
ls                   # List files in current directory
ls -lah              # Long listing, all files, human readable
cd /path/to/dir      # Change directory
cd ..                # Go up one level
cd ~                 # Go to home directory
```

---

### File Operations

```bash
touch file.txt                 # Create empty file
mkdir myfolder                 # Create directory
cp file1.txt file2.txt         # Copy file
cp -r folder1/ folder2/        # Copy folder recursively
mv old.txt new.txt             # Move or rename file
rm file.txt                    # Delete file
rm -r folder/                  # Delete folder recursively
```

---

### Viewing Files

```bash
cat file.txt                   # Print file contents
less file.txt                  # Scroll through file (q to quit)
head -n 10 file.txt            # First 10 lines
tail -n 10 file.txt            # Last 10 lines
```

---

### Searching

```bash
grep "text" file.txt           # Search in file
grep -r "text" folder/         # Search recursively
find . -name "*.txt"           # Find files by name
```

---

### Permissions

```bash
chmod +x script.sh             # Make file executable
chmod 755 file                 # rwxr-xr-x
chown user:group file          # Change owner
```

---

### Package Management

#### Debian/Ubuntu:

```bash
sudo apt update                # Update package lists
sudo apt upgrade               # Upgrade packages
sudo apt install pkgname       # Install package
sudo apt remove pkgname        # Remove package
```

#### Red Hat/CentOS:

```bash
sudo yum install pkgname
```

---

### System Info

```bash
uname -a                       # Kernel info
top                            # Real-time processes
htop                           # Better process viewer
df -h                          # Disk usage
free -h                        # RAM usage
```

---

### Process Management

```bash
ps aux                         # List all processes
kill PID                       # Kill process by PID
kill -9 PID                    # Force kill
```

---

### Networking

```bash
ip a                           # Show IP addresses
ping google.com                # Test connection
netstat -tulnp                 # List ports (need net-tools)
curl ifconfig.me               # Get external IP
```

---

### Other Useful Commands

```bash
man ls                         # Show help for a command
history                        # Command history
!!                             # Repeat last command
alias ll='ls -lah'             # Create alias
```

---

## Example: Combine Commands

```bash
ls -lah | grep "Jan"           # Show files modified in January
find . -name "*.log" | xargs rm  # Delete all .log files
```

---
