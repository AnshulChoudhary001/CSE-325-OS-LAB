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
