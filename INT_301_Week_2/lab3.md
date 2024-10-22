

# Lab 3: Automating Advanced File Management and Permissions in Linux

## Lab Overview
In this lab, students will focus on automating file management tasks with bash scripts, including handling file permissions, ownership changes, and access control. This will provide essential skills to automate common file administration tasks while ensuring proper security practices in Linux environments.

### Learning Objectives:
1. Automate the management of file and directory permissions.
2. Automate changing ownership of files and directories.
3. Use conditional statements to handle permission errors.
4. Implement automated security practices by managing file access control lists (ACLs).
5. Master file archiving, compression, and backups while retaining permissions.

---

## Part 1: Automating File Permissions

### 1.1 Viewing and Modifying Permissions
We will begin by scripting the process of viewing and modifying file permissions.

1. Open a terminal and create a bash script:
   ```bash
   nano manage_permissions.sh
   ```

2. In the script, write the following commands to display the permissions of a file:
   ```bash
   #!/bin/bash
   # Script to manage file permissions

   file="/home/labfile.txt"

   echo "Viewing file permissions for $file..."
   ls -l $file

   echo "Changing permissions to read, write, and execute for the owner..."
   chmod u+rwx $file

   echo "New permissions for $file:"
   ls -l $file
   ```

3. Save and make the script executable:
   ```bash
   chmod +x manage_permissions.sh
   ```

4. Run the script to test permission changes:
   ```bash
   ./manage_permissions.sh
   ```

### 1.2 Automating Recursive Permission Changes
Permissions often need to be set recursively, especially for directories. Let’s automate this.

1. Modify the script to recursively change directory permissions:
   ```bash
   directory="/home/labdir"

   echo "Changing permissions for all files in $directory recursively..."
   chmod -R 755 $directory

   echo "Listing permissions for all files in $directory..."
   ls -l $directory
   ```

This will apply read, write, and execute permissions for the owner and read/execute for group and others recursively.

---

## Part 2: Automating Ownership Changes

### 2.1 Changing File Ownership
We will now script ownership changes for files and directories.

1. Add to your script to change ownership of a file:
   ```bash
   echo "Changing ownership of $file to user 'john'..."
   chown john $file

   echo "Ownership of $file has been changed:"
   ls -l $file
   ```

2. Run the script and ensure the ownership is updated.

### 2.2 Recursive Ownership Changes
Ownership changes can also be applied recursively. Here’s how to automate that:

1. Modify the script to change ownership recursively:
   ```bash
   echo "Changing ownership of all files in $directory to user 'john'..."
   chown -R john $directory

   echo "Listing ownership for all files in $directory..."
   ls -l $directory
   ```

This will change ownership of all files and directories within `/home/labdir`.

---

## Part 3: Automating Permission Errors and Conditional Handling

### 3.1 Handling Permission Errors
Sometimes, permission or ownership changes may fail. Let’s add error handling to our script.

1. Modify your script to handle permission errors:
   ```bash
   if [ -e $file ]; then
       chmod u+rwx $file
       echo "Permissions changed successfully."
   else
       echo "Error: $file does not exist!"
   fi
   ```

This script checks if the file exists before attempting to change permissions and outputs an error if the file is not found.

---

## Part 4: Automating Access Control Lists (ACLs)

### 4.1 Managing File ACLs
Access control lists (ACLs) allow more granular permission control beyond the traditional user/group/other model.

1. Add the following to your script to apply ACLs to a file:
   ```bash
   echo "Applying ACL for user 'john' to read the file..."
   setfacl -m u:john:r /home/labfile.txt

   echo "Viewing ACL for $file..."
   getfacl /home/labfile.txt
   ```

2. Save and run the script. This will grant user `john` read access to `labfile.txt`.

### 4.2 Removing ACLs
You can also automate the removal of ACLs:

1. Modify the script to remove ACLs:
   ```bash
   echo "Removing ACL for user 'john'..."
   setfacl -x u:john /home/labfile.txt

   echo "ACL removed. Current ACL for $file:"
   getfacl /home/labfile.txt
   ```

---

## Part 5: Automating File Archiving and Compression with Permissions

### 5.1 Retaining Permissions in Archives
It’s important to retain permissions and ownership information when archiving files. Let’s automate the process of archiving while keeping permissions intact.

1. Add this code to your script to archive and compress a directory:
   ```bash
   echo "Archiving and compressing the /home/labdir directory..."
   tar -czvf /tmp/labdir_backup.tar.gz /home/labdir --preserve-permissions

   echo "Backup created with preserved permissions."
   ```

2. This command ensures that when the `/home/labdir` directory is restored from the backup, the permissions and ownership settings are retained.

---

## Part 6: Exercises

### Exercise 1: Automated Permission Checker
Write a bash script that:
1. Takes a directory as an input.
2. Checks the permissions of all files in the directory.
3. If any file is missing execute permissions for the owner, the script should automatically apply `u+x`.

### Exercise 2: Bulk Ownership Change
Write a bash script that:
1. Accepts a directory path and username as input.
2. Recursively changes the ownership of all files in the directory to the specified user.

### Exercise 3: Automated ACL Management
Write a script that:
1. Sets a default ACL on a directory for a specific user to have read and execute permissions on all newly created files.
2. Ensures that the ACL remains in place even if the user creates new files in the directory.

### Exercise 4: Scheduled Backup Script
Write a script that:
1. Automates the creation of daily backups for a specified directory.
2. Ensures that file permissions and ownership are preserved in the backup.
3. The script should save backups with the current date in the filename (e.g., `backup_2024-10-12.tar.gz`).

---

## Part 7: Conclusion

In this lab, you've explored how to automate advanced file management tasks in Linux using bash scripts. You’ve learned how to manage file permissions and ownership, handle ACLs, and automate backups while preserving important file metadata. Mastering these skills will help you efficiently manage and secure files in any Linux environment, especially in administrative or security-sensitive contexts.

--- 

This lab builds upon previous scripting skills, focusing on more advanced file management practices. By automating these tasks, students can improve system security, reduce errors, and save time in managing file permissions, ownership, and backups.