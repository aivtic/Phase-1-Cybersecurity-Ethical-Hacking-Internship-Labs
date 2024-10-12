

## **INT302: Kali Linux Tools and System Security – Lab 4: Basic Port Scanning**

### **Lab Overview**
In this lab, you will perform basic and advanced port scanning techniques using `nmap` and `nikto`. You will gather the IP addresses of your OWASP Broken Web Applications Project VM and utilize these IPs for scanning to identify open ports, services running on those ports, potential vulnerabilities, and the operating system of the target.

---

### **Lab Objectives**
By the end of this lab, you will:
1. Conduct a basic port scan using `nmap`.
2. Perform an aggressive scan to determine service versions and the operating system.
3. Utilize `nmap` for vulnerability scanning.
4. Use `nikto` to perform web server vulnerability scans.

---

### **Tools Used**
- **Kali Linux**: A Linux distribution tailored for penetration testing.
- **nmap**: A versatile network scanning tool for discovering hosts and services on a computer network.
- **nikto**: A web server scanner that tests for dangerous files/programs, outdated server software, and other vulnerabilities.

---

### **Prerequisites**
- Basic knowledge of Kali Linux and command-line operations.
- Access to the OWASP Broken Web Applications Project VM.
- `nmap` and `nikto` installed in your Kali Linux environment (they usually come pre-installed).

---

### **Lab Steps**

#### **Step 1: Gather the IP Address of Your OWASP VM**

**Instructions:**
1. Start your OWASP Broken Web Applications Project VM.
2. Open a terminal and run the following command to find the IP address:

   **Command Syntax**:
   ```bash
   ifconfig
   ```

3. Look for the `inet` address under your active network interface (usually `eth0` or `ens33`).

**Record the IP Address**:
- **OWASP VM IP Address**: __________

---

#### **Step 2: Basic Port Scanning with `nmap`**

Now that you have the IP address of your OWASP VM, use `nmap` to discover open ports.

**Instructions:**
1. Open your **Terminal** in Kali Linux.
2. Use the following command to scan for open ports on your OWASP VM.

   **Command Syntax**:
   ```bash
   nmap <IP address>
   ```

   **Example**:
   ```bash
   nmap 192.168.56.101  # Replace with the actual IP of your OWASP VM
   ```

**Expected Output**:  
The output will display a list of open ports on the specified IP address.

#### **Exercise 1**:  
Perform a basic port scan on your OWASP VM IP address and record your findings:
- **Open Ports**:
  - __________

---

#### **Step 3: Aggressive Scanning with `nmap`**

Aggressive scanning with `nmap` can reveal service versions and the operating system running on open ports.

**Instructions:**
1. Use the following command to perform an aggressive scan.

   **Command Syntax**:
   ```bash
   nmap -sV -O <IP address>
   ```

   **Example**:
   ```bash
   nmap -sV -O 192.168.56.101  # Replace with the actual IP of your OWASP VM
   ```

**Expected Output**:  
The output will display open ports, service versions, and operating system details.

#### **Exercise 2**:  
Perform an aggressive scan on your OWASP VM IP address and record your findings:
- **Service Versions**:
  - __________
- **Operating System**:
  - __________

---

#### **Step 4: Vulnerability Scanning with `nmap`**

`nmap` allows you to run vulnerability scans against the target system.

**Instructions:**
1. Use the following command to perform a vulnerability scan.

   **Command Syntax**:
   ```bash
   nmap --script vuln <IP address>
   ```

   **Example**:
   ```bash
   nmap --script vuln 192.168.56.101  # Replace with the actual IP of your OWASP VM
   ```

**Expected Output**:  
The output will display any vulnerabilities found on the target system.

#### **Exercise 3**:  
Conduct a vulnerability scan on your OWASP VM IP address and record your findings:
- **Vulnerabilities**:
  - __________

---

#### **Step 5: Web Vulnerability Scanning with `nikto`**

`nikto` is a comprehensive web server scanner that checks for various vulnerabilities.

**Instructions:**
1. Use the following command to perform a web server vulnerability scan.

   **Command Syntax**:
   ```bash
   nikto -h <target URL>
   ```

   **Example**:
   ```bash
   nikto -h http://192.168.56.101  # Replace with the actual URL of your OWASP VM
   ```

**Expected Output**:  
The output will display any vulnerabilities found on the web server.

#### **Exercise 4**:  
Perform a vulnerability scan on your OWASP VM and record your findings:
- **Vulnerabilities Found**:
  - __________

---

### **Submission Instructions**
Submit your results from all exercises, including:
- Detected open ports from the basic scan.
- Service versions and operating system from the aggressive scan.
- Any vulnerabilities discovered using `nmap`.
- Vulnerabilities found using `nikto`.

---

### **Conclusion**
In this lab, you explored techniques for basic port scanning and vulnerability assessment using `nmap` and `nikto`. These skills are essential for identifying potential attack vectors and securing network infrastructures.

---
