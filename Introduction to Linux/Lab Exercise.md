### Lab Exercise 1
**Explore the file system of a Windows system and a Linux system and write prime differences.**

**Windows File System:**
- Windows uses drive letters (C:, D:, etc.) to represent different storage devices.
- Path separator is backslash `\`.
- Windows is not case-sensitive regarding file and folder names.
- File extensions are used to determine file type.

**Linux File System:**
- Linux has a single root directory represented by `/`.
- Path separator is forward slash `/`.
- Linux is case-sensitive regarding file and folder names.
- File types are determined by file permissions, not extensions.

*Prime Differences:*
- **Path Representation:** Windows uses drive letters (C:, D:) while Linux uses a single root directory (`/`).
- **Case Sensitivity:** Linux is case-sensitive, so `file.txt` and `File.txt` are considered different files. Windows is not case-sensitive in this context.
- **File Types:** Windows relies on file extensions (like `.txt`, `.exe`) to identify file types, while Linux uses file permissions.

### Lab Exercise 2
**Create a file in your Linux system, in your current user’s home directory, named as `file1.txt`. Write your name and Registration number in the `file1.txt` using `cat` command. Now rename the file using `mv` command, the new name must be “`yourRegistrationNo.txt`”.**

```bash
# Create file and write content
echo "Your Name: Your Registration Number" > file1.txt

# Verify file content
cat file1.txt

# Rename the file
mv file1.txt yourRegistrationNo.txt

# Verify the new file name
ls
```

### Lab Exercise 3
**Create a copy of the file you have created with your registration number. Now delete the original file.**

```bash
# Create a copy of the file
cp yourRegistrationNo.txt yourRegistrationNo_copy.txt

# Verify the copied file
ls

# Delete the original file
rm yourRegistrationNo.txt

# Verify the deletion
ls
```

### Lab Exercise 4
**Create a directory with your name and move all the files (using `mv` command) created by you in the currently logged-in user’s home directory.**

```bash
# Create a directory with your name
mkdir YourName

# Move files to the new directory
mv yourRegistrationNo_copy.txt YourName/

# Verify the move
ls
ls YourName/
```

### Lab Exercise 5
**Create multiple directories using a single command. (Directories' names can be your friends’ names.)**

```bash
# Create multiple directories
mkdir Friend1 Friend2 Friend3

# Verify the creation of directories
ls
```

These commands assume you are using a Linux system. Please adjust the commands accordingly if you are using a Windows system with a Linux subsystem or any other environment.
