**Lab Exercises README**

## Exercise 1: Creating a Directory, Creating a File, and Listing Contents

```c
#include<stdio.h>
#include<dirent.h>
#include<sys/stat.h>
#include<sys/types.h>
#include<fcntl.h>
#include<unistd.h>

int main() {
    // Creating a directory on the desktop
    int dir_creation = mkdir("~/Desktop/NewDirectory", 0777);

    if (dir_creation != -1) {
        printf("Directory created successfully!\n");

        // Changing the working directory to the newly created one
        int dir_change = chdir("~/Desktop/NewDirectory");

        if (dir_change != -1) {
            printf("Working directory changed successfully!\n");

            // Creating a file inside the directory
            int file_creation = creat("NewFile.txt", 0666);

            if (file_creation != -1) {
                printf("File created successfully!\n");

                // Listing the contents of the directory
                DIR *dp = opendir(".");
                struct dirent *dptr;

                printf("Contents of the directory:\n");
                while ((dptr = readdir(dp)) != NULL) {
                    printf("%s\n", dptr->d_name);
                }

                closedir(dp);
            } else {
                printf("Error creating the file!\n");
            }
        } else {
            printf("Error changing the working directory!\n");
        }
    } else {
        printf("Error creating the directory!\n");
    }

    return 0;
}
```

## Exercise 2: Copying Contents of One Directory to a Newly Created Directory

```c
#include<stdio.h>
#include<dirent.h>
#include<sys/stat.h>
#include<sys/types.h>
#include<fcntl.h>
#include<unistd.h>

int main() {
    // Creating a source directory on the desktop
    int dir_creation_source = mkdir("~/Desktop/SourceDirectory", 0777);

    if (dir_creation_source != -1) {
        printf("Source directory created successfully!\n");

        // Creating a destination directory on the desktop
        int dir_creation_dest = mkdir("~/Desktop/DestinationDirectory", 0777);

        if (dir_creation_dest != -1) {
            printf("Destination directory created successfully!\n");

            // Changing the working directory to the source directory
            int dir_change_source = chdir("~/Desktop/SourceDirectory");

            if (dir_change_source != -1) {
                printf("Working directory changed to the source directory!\n");

                // Creating a file inside the source directory
                int file_creation_source = creat("SourceFile.txt", 0666);

                if (file_creation_source != -1) {
                    printf("File created inside the source directory!\n");

                    // Copying contents of the source directory to the destination directory
                    DIR *dp_source = opendir(".");
                    struct dirent *dptr_source;

                    while ((dptr_source = readdir(dp_source)) != NULL) {
                        // Copy each file/directory to the destination directory
                        // Note: This is a simplified example and does not handle subdirectories recursively
                        int copy_result = link(dptr_source->d_name, "~/Desktop/DestinationDirectory");
                        
                        if (copy_result != -1) {
                            printf("Copied: %s\n", dptr_source->d_name);
                        } else {
                            printf("Error copying: %s\n", dptr_source->d_name);
                        }
                    }

                    closedir(dp_source);
                } else {
                    printf("Error creating a file inside the source directory!\n");
                }
            } else {
                printf("Error changing the working directory to the source directory!\n");
            }
        } else {
            printf("Error creating the destination directory!\n");
        }
    } else {
        printf("Error creating the source directory!\n");
    }

    return 0;
}
```

### Explanation

- **Exercise 1:** This program creates a directory on the desktop, changes the working directory to the new one, creates a file inside it, and then lists the contents of the directory.

- **Exercise 2:** This program creates a source directory on the desktop, a destination directory on the desktop, and changes the working directory to the source directory. It then creates a file inside the source directory and copies the contents of the source directory to the destination directory. Note that this is a simplified example and does not handle subdirectories recursively.
