

## **INT311 - Basic Computer Skills for Digital Forensics – Lab 4**

### **Lab Title:**  
**Introduction to Operating Systems and File Systems in Linux**

---

### **Objective:**
This lab aims to provide students with foundational knowledge of Linux operating systems, focusing on file systems, directory structures, and essential commands. Students will learn about the benefits and challenges of using Linux for digital forensics and gain hands-on experience in managing files, performing system updates, and understanding networking commands in a Linux environment.

---

### **Part 1: Understanding Linux for Digital Forensics**

1. **Good and Bad Aspects of Linux in Digital Forensics:**
   - Discuss the advantages of using Linux for digital forensics, such as its open-source nature, powerful command-line tools, and extensive community support.
   - Address the potential challenges, including compatibility issues with certain file systems and software, and the learning curve for users new to Linux.

   **Task:**
   - Write a brief summary of at least two advantages and two challenges of using Linux for digital forensics.

---

### **Part 2: Virtual File System and File Structure**

1. **Virtual File System (VFS):**
   - Explain what a Virtual File System is and its role in Linux.
   - Discuss how VFS allows Linux to support multiple file systems seamlessly.

2. **File Structure:**
   - Describe the hierarchical file structure in Linux and the significance of the root directory (`/`).

   **Task:**
   - Create a diagram representing the Linux file structure, highlighting key directories such as `/home`, `/etc`, `/usr`, and `/var`.

---

### **Part 3: Path and Path Variable**

1. **Path Variable:**
   - Define what the path variable is in Linux and its importance in executing commands.

   **Task:**
   - Display the current path variable by executing the command:
     ```bash
     echo $PATH
     ```
   - Add a new directory (e.g., **`/home/yourusername/scripts`**) to the path variable temporarily for the session:
     ```bash
     export PATH=$PATH:/home/yourusername/scripts
     ```

   **Task:**
   - Confirm the new path by executing the **`echo $PATH`** command again.

---

### **Part 4: Essential Linux Commands**

1. **Creating Folders and Files:**
   - Use the following commands to create a new directory named **`forensics_lab`** and create two text files within it:
     ```bash
     mkdir ~/forensics_lab
     touch ~/forensics_lab/file1.txt ~/forensics_lab/file2.txt
     ```

2. **File Copying and Deletion:**
   - Copy **`file1.txt`** to a new file named **`file1_copy.txt`**:
     ```bash
     cp ~/forensics_lab/file1.txt ~/forensics_lab/file1_copy.txt
     ```
   - Delete **`file2.txt`**:
     ```bash
     rm ~/forensics_lab/file2.txt
     ```

   **Task:**
   - Verify that the copy and deletion were successful by listing the contents of the **`forensics_lab`** directory:
     ```bash
     ls ~/forensics_lab
     ```

---

### **Part 5: Searching for Information**

1. **Searching for Files:**
   - Use the `find` command to search for all `.txt` files in the **`forensics_lab`** directory:
     ```bash
     find ~/forensics_lab -name "*.txt"
     ```

   **Task:**
   - Document the output of the command and explain what it shows.

---

### **Part 6: Networking in Linux**

1. **Basic Networking Commands:**
   - Execute the following commands to gather network information:
     - **`ifconfig`**: Display network interfaces and their configurations.
     - **`ping google.com`**: Check connectivity to Google's servers.
     - **`traceroute google.com`**: Trace the route to Google.
   - Use **nmap** to scan the localhost for port 21:
     ```bash
     nmap localhost -p 21
     ```

   - Use **netcat** to set up a simple TCP connection:
     ```bash
     nc -l -p 12345
     ```
   - Use **wget** to download an image:
     ```bash
     wget https://pbs.twimg.com/media/DulILzQXcAAkFMV.jpg
     ```

   **Task:**
   - Document the outputs of these commands and explain the significance of the information provided.

---

### **Part 7: File Management**

1. **Zipping and Unzipping Files:**
   - Create a compressed archive of the **`forensics_lab`** directory:
     ```bash
     zip -r forensics_lab.zip ~/forensics_lab
     ```
   - Unzip the created archive into a new directory:
     ```bash
     mkdir ~/uncompressed_lab
     unzip forensics_lab.zip -d ~/uncompressed_lab
     ```

   **Task:**
   - Verify the contents of the uncompressed directory to ensure all files were restored correctly:
     ```bash
     ls ~/uncompressed_lab
     ```

---

### **Part 8: Creating a Shell Script**

1. **Creating a Shell Script:**
   - Create a shell script named **`sys_info.sh`** with the following content:
   ```bash
   #!/bin/bash
   echo "System Information:"
   uname -a
   free -h
   df -h
   ```
   - Make the script executable:
   ```bash
   chmod +x ~/forensics_lab/sys_info.sh
   ```

   **Task:**
   - Run the script from the terminal:
   ```bash
   ~/forensics_lab/sys_info.sh
   ```

   - Document the output observed from executing the script.

---

### **Part 9: Installing Software**

1. **Installing Terminator:**
   - Use the following command to install **Terminator**, a terminal emulator:
   ```bash
   sudo apt install terminator
   ```

   **Task:**
   - Document the installation steps and any outputs observed during the installation process.

---

### **Part 10: Updating/Installing Software**

1. **Updating Software:**
   - Use the following command to update the package list and upgrade installed packages:
   ```bash
   sudo apt update && sudo apt upgrade
   ```

---

### **Submission Requirements:**

- Submit a PDF document containing:
  - Screenshots of the commands executed and their outputs.
  - Summaries and explanations for each task completed.
  - The shell script you created and its output.

- Ensure your document is well-organized, clearly labeled, and includes your name and student ID at the top.

---

### **Grading Criteria:**

- **Correctness:** Accuracy of file and folder management, networking commands, and script execution.
- **Clarity:** Clear explanations and documentation of the process.
- **Depth:** Thoroughness of explanations regarding Linux file systems and commands.
- **Documentation:** Professional presentation of findings with appropriate screenshots and organization.

---

### **Important Notes:**

- This lab will provide you with essential skills for working with Linux systems and understanding file systems relevant to digital forensics.
- Be sure to explore the various Linux commands and their options to further enhance your skills.

---

Good luck!