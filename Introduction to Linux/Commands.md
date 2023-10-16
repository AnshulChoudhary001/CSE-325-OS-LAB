### Commands Used in Examples:

#### General File and Directory Commands:

- **Linux:**
  - `ls`: List files and directories.
  - `cd directory_name`: Change directory.
  - `pwd`: Print working directory.
  - `mkdir directory_name`: Create a new directory.
  - `touch file_name`: Create a new file.
  - `echo "content" > file_name`: Write content to a file.
  - `cat file_name`: Display file content.
  - `cp source destination`: Copy files/directories.
  - `mv source destination`: Move files/directories.
  - `rm file_name`: Remove/delete a file.
  - `rm -r directory_name`: Remove/delete a directory and its contents.
  - `ln -s source_file link_name`: Create symbolic links.
  - `chmod permissions file_name`: Change file permissions.
  - `chown user_name:group_name file_name`: Change file owner and group.
  
- **Windows:**
  - `Dir`: List files and directories.
  - `cd directory_name`: Change directory.
  - `chdir`: Show current directory.
  - `mkdir directory_name`: Create a new directory.
  - `echo content > file_name`: Write content to a file.
  - `notepad file_name`: Open a file in Notepad.
  - `copy source destination`: Copy files/directories.
  - `move source destination`: Move files/directories.
  - `del file_name`: Delete a file.
  - `rmdir /s directory_name`: Delete a directory and its contents.

#### Specific Examples from Exercises:

- `echo "Your Name: Your Registration Number" > file1.txt`: Write content to a file.
- `mv file1.txt yourRegistrationNo.txt`: Rename a file.
- `cp yourRegistrationNo.txt yourRegistrationNo_copy.txt`: Copy a file.
- `mkdir YourName`: Create a directory.
- `mv yourRegistrationNo_copy.txt YourName/`: Move a file to a directory.

### Additional Common Linux/Ubuntu Commands:

- `ps`: List active processes.
- `top`: Display real-time system statistics.
- `kill process_id`: Terminate a process.
- `df`: Display disk space usage.
- `du`: Show directory space usage.
- `tar`: Archive files.
- `grep pattern file_name`: Search for a pattern in a file.
- `find directory -name file_name`: Search for files or directories.
- `ssh username@hostname`: Connect to a remote server via SSH.
- `scp source_file username@hostname:destination_path`: Copy files securely over SSH.
- `wget URL`: Download files from the internet.
- `history`: View command history.
- `man command_name`: Display manual pages for a command.

Remember, the usage and options of these commands can be explored further by checking the respective man pages (e.g., `man ls` for information about the `ls` command). Additionally, always exercise caution, especially when using commands like `rm` or `mv`, to avoid accidental data loss.


## System Information and Monitoring:

- `uname -a`: Display system information (kernel version, hostname, etc.).
- `lscpu`: Show information about CPU architecture.
- `free -h`: Display available and used memory in a human-readable format.
- `uptime`: Show how long the system has been running and the system load.
- `ps aux`: List detailed information about active processes.
- `htop`: An interactive process viewer, similar to `top`.
- `df -h`: Display disk space usage in a human-readable format.
- `du -h`: Estimate file space usage in a directory.

## User and Permission Management:

- `sudo command_name`: Execute a command with superuser privileges.
- `sudo su`: Switch to the root user.
- `useradd username`: Add a new user.
- `passwd username`: Set a password for a user.
- `userdel username`: Delete a user.
- `groups username`: Display groups a user belongs to.
- `chmod permissions file_or_directory`: Change file/directory permissions.
- `chown user:group file_or_directory`: Change file/directory owner and group.

## Networking:

- `ifconfig`: Display network interface configuration.
- `ip addr show`: Show IP addresses and network interfaces.
- `ping hostname_or_ip`: Check network connectivity to a specific host.
- `nslookup domain`: Query DNS servers for domain information.
- `netstat -tuln`: Display listening ports.
- `ss -tuln`: Similar to `netstat`, display network sockets.
- `traceroute hostname_or_ip`: Display the route packets take to reach a network host.

## Package Management (APT):

- `sudo apt update`: Update the local package database.
- `sudo apt upgrade`: Upgrade installed packages to the latest versions.
- `sudo apt install package_name`: Install a new package.
- `sudo apt remove package_name`: Remove a package.
- `sudo apt search search_term`: Search for packages matching a keyword.
- `dpkg -i package.deb`: Install a Debian package (`.deb` file).

## File and Text Manipulation:

- `cat file_name`: Concatenate and display file content.
- `grep pattern file_name`: Search for a pattern in a file.
- `sed 's/old_pattern/new_pattern/g' file_name`: Search and replace text in a file.
- `awk '{print $1}' file_name`: Extract and print specific columns from a file.
- `head file_name`: Display the first few lines of a file.
- `tail file_name`: Display the last few lines of a file.
- `diff file1 file2`: Show the differences between two files.
- `sort file_name`: Sort lines of text files.
- `uniq file_name`: Report or omit repeated lines from a sorted file.

These commands cover a wide range of tasks and are useful for managing files, users, networks, and system resources in a Linux/Ubuntu environment. Remember to consult the respective man pages (e.g., `man sudo` or `man grep`) for detailed information on each command and its options.
