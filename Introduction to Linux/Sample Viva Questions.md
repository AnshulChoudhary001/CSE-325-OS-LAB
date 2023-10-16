### Viva Questions

1. **How Windows is different from Linux?**
   - **File System:** Windows uses drive letters (C:, D:, etc.) while Linux has a single root directory (/).
   - **User Interface:** Windows typically uses a graphical user interface (GUI) whereas Linux offers both GUI and command-line interface (CLI).
   - **Licensing:** Windows is a proprietary operating system, whereas Linux is open-source, which means its source code is accessible to the public.
   - **Security Model:** Linux has a robust and fine-grained permission system, while Windows uses access control lists (ACLs) and user groups for security.
   - **File Paths:** Windows uses backslashes (\) in file paths, while Linux uses forward slashes (/).
   - **Case Sensitivity:** Linux file system is case-sensitive, whereas Windows is not by default.

2. **Differentiate internal and external commands in Linux.**
   - **Internal Commands:** Internal commands in Linux are built into the shell (like Bash) and are directly executed by the shell. They are a part of the shell itself and do not exist as separate executable files on the file system. Examples include `cd`, `pwd`, and `echo`.
   - **External Commands:** External commands are separate executable files located in directories listed in the system's PATH variable. They are independent programs that can be run from the command line. Examples include `ls`, `cp`, and `grep`.

3. **Name any 3 Windows and Linux flavors.**
   - **Windows:**
     - Windows 10
     - Windows Server 2019
     - Windows 11
   - **Linux:**
     - Ubuntu
     - CentOS
     - Fedora

4. **List different file systems used in Windows and Linux.**
   - **Windows File Systems:**
     - NTFS (New Technology File System)
     - FAT32 (File Allocation Table 32)
     - exFAT (Extended File Allocation Table)
   - **Linux File Systems:**
     - ext4 (Fourth Extended File System)
     - ext3 (Third Extended File System)
     - Btrfs (B-tree File System)
     - XFS (X File System)
     - ZFS (Zettabyte File System)

5. **What are the different types of files in the Linux environment?**
   - **Regular Files:** These are regular files that contain data, text, or program instructions.
   - **Directories:** Files that are used to store other files and directories.
   - **Symbolic Links (Soft Links):** Pointers to another file or directory location in the file system.
   - **Device Files:** Represent devices connected to the system, such as hard drives, printers, or terminals. There are two types: block devices (like hard drives) and character devices (like keyboards).
   - **Special Files:** Provide access to specific resources, like `/dev/null` (null device) and `/dev/random` (random number generator).
   - **Sockets:** Used for inter-process communication (IPC) between processes on the same or different systems.
   - **Pipes:** Enable communication between processes within the same system.
