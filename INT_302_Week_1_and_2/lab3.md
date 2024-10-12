

## **INT302: Kali Linux Tools and System Security – Lab 3: Subdomain Hunting**

### **Lab Overview**
In this lab, you will learn how to identify subdomains associated with a target domain using various tools. Subdomain hunting is a crucial part of reconnaissance in penetration testing, as it helps identify additional attack surfaces that may not be immediately visible. We will utilize `sublist3r` for subdomain enumeration, `dirb` for directory discovery, and `theHarvester` for gathering information from public sources.

---

### **Lab Objectives**
By the end of this lab, you will:
1. Perform subdomain enumeration using `sublist3r`.
2. Discover hidden directories on a target web server using `dirb`.
3. Utilize `theHarvester` to gather additional information about the target domain.

---

### **Tools Used**
- **Kali Linux**: A Linux distribution tailored for penetration testing.
- **sublist3r**: A tool designed for subdomain enumeration.
- **dirb**: A web content scanner for discovering hidden directories.
- **theHarvester**: A tool for gathering emails and subdomains from public sources.

---

### **Prerequisites**
- Basic knowledge of Kali Linux and command-line operations.
- Internet access to perform scans on live web servers.
- Tools `sublist3r`, `dirb`, and `theHarvester` installed in your Kali Linux environment (they usually come pre-installed).

---

### **Lab Steps**

#### **Step 1: Subdomain Enumeration Using `sublist3r`**

`sublist3r` is an effective tool for finding subdomains of a target domain.

**Instructions:**
1. Open your **Terminal** in Kali Linux.
2. Use the `sublist3r` command followed by the target domain.

   **Command Syntax**:
   ```bash
   sublist3r -d <target domain>
   ```

   **Example**:
   ```bash
   sublist3r -d example.com
   ```

**Expected Output**:  
The output will display a list of subdomains associated with the specified domain.

#### **Exercise 1**:  
Run the `sublist3r` command for the following domains:
- `github.com`
- `google.com`

**Record Your Findings**:
1. **Subdomains for github.com**:
   - __________
2. **Subdomains for google.com**:
   - __________

---

#### **Step 2: Directory Discovery Using `dirb`**

`dirb` is a powerful tool for discovering hidden directories and files on web servers.

**Instructions:**
1. In the terminal, run the `dirb` command followed by the target URL.

   **Command Syntax**:
   ```bash
   dirb <target URL>
   ```

   **Example**:
   ```bash
   dirb https://example.com
   ```

**Expected Output**:  
The command will return a list of directories and files found on the web server.

#### **Exercise 2**:  
Perform a directory discovery scan on the following targets:
- `http://example.com`
- `http://example.org`

**Record Your Findings**:
1. **Directories for example.com**:
   - __________
2. **Directories for example.org**:
   - __________

---

#### **Step 3: Information Gathering Using `theHarvester`**

`theHarvester` is a tool for gathering emails, subdomains, and other relevant information from search engines.

**Instructions:**
1. In the terminal, run the `theHarvester` command followed by the target domain.

   **Command Syntax**:
   ```bash
   theharvester -d <target domain> -b google
   ```

   **Example**:
   ```bash
   theharvester -d example.com -b google
   ```

**Expected Output**:  
The output will show collected emails and other information about the specified domain.

#### **Exercise 3**:  
Use `theHarvester` to gather information on the following domain:
- `example.com`

**Record Your Findings**:
- **Emails and Information Gathered**:
  - __________

---

### **Submission Instructions**
Submit your results from all exercises, including:
- Detected subdomains from `sublist3r`.
- Discovered directories from `dirb`.
- Information gathered using `theHarvester`.

---

### **Conclusion**
In this lab, you explored techniques for subdomain hunting and directory discovery using various tools. This knowledge is essential for identifying potential vulnerabilities and attack vectors in a target's infrastructure.

---
