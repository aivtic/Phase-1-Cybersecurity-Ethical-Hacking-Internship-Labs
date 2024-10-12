

## **INT302: Kali Linux Tools and System Security – Lab 2: Website Enumeration and Information Gathering**

### **Lab Overview**
This lab focuses on website enumeration and information gathering techniques that are essential in the reconnaissance phase of penetration testing. You will learn to detect web technologies used by a target website and perform aggressive scanning to gather detailed information. We will utilize the `whatweb` tool, a powerful utility designed for identifying web technologies.

---

### **Lab Objectives**
By the end of this lab, you will:
1. Detect web technologies used by a website or server using the `whatweb` command.
2. Perform aggressive scanning on a target IP address or URL to extract detailed information about its web technologies.

---

### **Tools Used**
- **Kali Linux**: A Linux distribution tailored for penetration testing.
- **Terminal**: The command-line interface to execute commands.

---

### **Prerequisites**
- Basic knowledge of Kali Linux and command-line operations.
- Internet access to perform scans on live web servers.
- `whatweb` installed in your Kali Linux environment (it usually comes pre-installed).

---

### **Lab Steps**

#### **Step 1: Detect Web Technologies Using `whatweb`**

The `whatweb` command allows you to identify the technologies used by a web application, including the server type, programming languages, and content management systems.

**Instructions:**
1. Open your **Terminal** in Kali Linux.
2. Use the `whatweb` command followed by the target IP address or URL.

   **Command Syntax**:
   ```bash
   whatweb <IP address or URL>
   ```

   **Example**:
   ```bash
   whatweb 192.168.1.1
   ```

**Expected Output**:  
The output will display various technologies detected on the specified web server, including web server software, programming languages, frameworks, and more.

#### **Exercise 1**:  
Run the `whatweb` command to detect technologies for the following targets:
- `example.com`
- `stackoverflow.com`
- `github.com`

**Record Your Findings**:
1. **example.com**: __________
2. **stackoverflow.com**: __________
3. **github.com**: __________

---

#### **Step 2: Perform Aggressive Scanning Using `whatweb`**

The `--aggression` option allows for more thorough scanning by enabling additional checks, which can reveal more information about the target.

**Instructions:**
1. In the terminal, run the `whatweb` command with the `--aggression` option.

   **Command Syntax**:
   ```bash
   whatweb --aggression 3 -v <IP address or URL>
   ```

   **Example**:
   ```bash
   whatweb --aggression 3 -v example.com
   ```

**Expected Output**:  
The command will provide a verbose output with more detailed information about the technologies detected on the web application.

#### **Exercise 2**:  
Perform an aggressive scan on the following targets:
- `google.com`
- `facebook.com`

**Record Your Findings**:
1. **google.com**: __________
2. **facebook.com**: __________

---

### **Submission Instructions**
Submit your results from both exercises, including:
- Detected web technologies from the `whatweb` command.
- Detailed findings from the aggressive scans.

---

### **Conclusion**
In this lab, you explored important techniques for website enumeration and information gathering using the `whatweb` tool. Understanding the technologies and software running on target systems is crucial for developing effective penetration testing strategies.

---

