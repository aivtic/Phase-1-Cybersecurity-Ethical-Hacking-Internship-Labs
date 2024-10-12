

# Lab 2: Automating Linux Command Shell Navigation

## Lab Overview
In this lab, students will learn how to automate Linux command shell navigation and file management tasks using bash scripts. Students will explore how to traverse directories, manipulate files, and automate common administrative tasks like directory creation, cleanup, and archiving. This lab will include hands-on exercises to ensure mastery of key concepts.

### Learning Objectives:
1. Automate directory navigation using bash scripts.
2. Create, move, and remove files and directories using automation.
3. Use loops to automate repetitive navigation tasks.
4. Utilize conditional statements to manage file operations.
5. Execute commands on multiple directories and files in an automated fashion.

---

## Part 1: Automating Directory Navigation

### 1.1 Basic Navigation
Start by automating the process of navigating directories.

1. Open a terminal and create a bash script:
   ```bash
   nano auto_navigate.sh
   ```

2. In the script, write the following commands to navigate the file system:
   ```bash
   #!/bin/bash
   # Automated navigation script

   echo "Navigating to /home directory..."
   cd /home
   pwd

   echo "Listing files in /home..."
   ls -la
   ```

3. Save and make the script executable:
   ```bash
   chmod +x auto_navigate.sh
   ```

4. Run the script:
   ```bash
   ./auto_navigate.sh
   ```

This script will automatically navigate to the `/home` directory, display the current location using `pwd`, and list all the files and directories within `/home` using `ls -la`.

### 1.2 Automating Directory Creation and Removal
Scripts can automate directory creation and cleanup tasks.

1. Add to your script to create and remove directories:
   ```bash
   echo "Creating directory /home/lab_test..."
   mkdir /home/lab_test
   ls /home

   echo "Removing /home/lab_test directory..."
   rmdir /home/lab_test
   ls /home
   ```

---

## Part 2: Automating File Operations

### 2.1 Creating and Moving Files
We will automate the process of file creation and moving files between directories.

1. Modify the script to create, move, and display a file:
   ```bash
   echo "Creating a new file..."
   touch /home/testfile.txt
   echo "Test file created."

   echo "Moving the file to /tmp directory..."
   mv /home/testfile.txt /tmp
   echo "File moved to /tmp."

   echo "Listing contents of /tmp..."
   ls /tmp
   ```

2. Save and rerun the script to see file creation and movement in action.

### 2.2 Copying and Deleting Files
Let’s automate copying and deleting files.

1. Add copying and deleting operations to the script:
   ```bash
   echo "Copying the file back to /home..."
   cp /tmp/testfile.txt /home
   echo "File copied back to /home."

   echo "Deleting the file from /tmp..."
   rm /tmp/testfile.txt
   echo "File deleted from /tmp."
   ```

---

## Part 3: Automating Recursive Directory Traversal

### 3.1 Using Loops to Navigate Multiple Directories
Sometimes, it is necessary to perform actions across multiple directories. A loop can help automate this process.

1. Create a bash script that navigates through several directories:
   ```bash
   #!/bin/bash
   echo "Navigating and listing contents of directories."

   directories=("/home" "/tmp" "/var")

   for dir in "${directories[@]}"; do
       echo "Navigating to $dir"
       cd $dir
       echo "Contents of $dir:"
       ls -la
       echo ""
   done
   ```

2. Save and run the script. This will loop through the specified directories, navigating to each one and listing its contents.

---

## Part 4: Conditional Automation and Error Handling

### 4.1 Checking for Directory Existence Before Navigation
It’s important to check if a directory exists before navigating into it. Let’s add some error handling to our script.

1. Modify the script to check if a directory exists:
   ```bash
   directory="/home/nonexistent_directory"

   if [ -d "$directory" ]; then
       echo "$directory exists, navigating..."
       cd $directory
   else
       echo "$directory does not exist."
   fi
   ```

2. This will prevent the script from failing if the directory doesn’t exist.

### 4.2 Automatically Creating Missing Directories
Let’s automate the process of creating a directory if it doesn’t exist.

1. Modify the previous script to create the directory if it’s missing:
   ```bash
   if [ ! -d "$directory" ]; then
       echo "$directory does not exist, creating it..."
       mkdir $directory
   fi
   cd $directory
   ```

---

## Part 5: Automating Cleanup and Archiving

### 5.1 Deleting Old Files Automatically
Automate the process of deleting files older than a specified number of days (e.g., 7 days).

1. Add this code to your script:
   ```bash
   echo "Deleting files older than 7 days in /tmp directory..."
   find /tmp -type f -mtime +7 -exec rm {} \;
   echo "Old files deleted."
   ```

This will find and delete any files in `/tmp` that are older than 7 days.

### 5.2 Archiving Directories
You can also automate the process of creating backups.

1. Add this to your script to archive a directory:
   ```bash
   echo "Archiving /home directory..."
   tar -czvf /tmp/home_backup.tar.gz /home
   echo "Backup created in /tmp."
   ```

This command creates a compressed archive of the `/home` directory.

---

## Part 6: Exercises

### Exercise 1: Directory and File Organizer
Write a bash script that:
1. Creates directories for the days of the week (`Monday`, `Tuesday`, etc.).
2. Moves files from `/home` that were created on each day of the week into the corresponding directory.
   
Hints:
- Use the `date` command to determine when a file was created.
- Use loops to automate the process.

### Exercise 2: Automated Log Cleanup
Write a script that:
1. Navigates to the `/var/log` directory.
2. Deletes all `.log` files that are older than 5 days.
3. Archives the remaining `.log` files into a tar archive.

### Exercise 3: Directory Search Script
Write a script that:
1. Takes a directory name as an argument.
2. Searches for that directory on the system and outputs its full path.
3. If the directory does not exist, it should prompt the user to create it.

### Exercise 4: Automated Backup System
Write a bash script that:
1. Creates a daily backup of the `/home` directory.
2. The script should create a separate archive for each day of the week (e.g., `home_backup_Monday.tar.gz`).
3. It should check if a backup for the current day exists, and if so, overwrite it.

---

## Part 7: Conclusion

In this lab, you've learned how to automate common Linux shell navigation tasks using bash scripts. You can now create scripts to automatically move between directories, create, move, delete files, and even automate administrative tasks such as cleaning up logs or backing up files. By continuing to practice these skills, you'll become more efficient in managing Linux environments!

---

