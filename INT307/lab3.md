

# INT307 Web Application Security  Lab 3: Command Injection in DVWA

## Overview

In this lab, you will explore Command Injection vulnerabilities within the Damn Vulnerable Web Application (DVWA). Command Injection occurs when an application allows an attacker to execute arbitrary commands on the host operating system due to improper input validation.

You will test various payloads against different levels of command injection vulnerabilities: Low, Medium, High, and Impossible.

### Prerequisites

- Ensure you have DVWA installed and running.
- Familiarize yourself with BurpSuite and the FoxyProxy extension for effective testing.

---

## Exercise Instructions

### **Exercise 1: Low-Level Command Injection**

**Objective:** Identify and exploit a low-level command injection vulnerability.

1. **Access the Command Injection Page**: Navigate to the following URL in your DVWA instance:
   - [Command Injection Low Level](http://localhost/DVWA/vulnerabilities/exec/)
   
2. **Interact with the Input Field**:
   - Locate the input field that asks for an IP address to ping.

3. **Test a Valid IP Address**:
   - Input `127.0.0.1` and submit the form.
   - Observe the response from the application.

4. **Inject a Malicious Command**:
   - Now, use the following payload:
   ```bash
   127.0.0.1 ; whoami ; cat /etc/passwd
   ```
   - Submit the form and record the output.

5. **Reflection**:
   - What information was returned? Discuss the implications of this vulnerability.

---

### **Exercise 2: Medium-Level Command Injection**

**Objective:** Identify and exploit a medium-level command injection vulnerability.

1. **Access the Command Injection Page**: Stay on the same URL as above.

2. **Interact with the Input Field**:
   - Again, locate the input field for the IP address.

3. **Test a Valid IP Address**:
   - Enter `127.0.0.1` and submit to confirm the ping request.

4. **Bypass Input Restrictions**:
   - Use the following payload:
   ```bash
   127.0.0.1 | whoami
   ```
   - Submit the form and observe the result.

5. **Reflection**:
   - How did you bypass the input restrictions? What does this say about the security of the application?

---

### **Exercise 3: High-Level Command Injection**

**Objective:** Identify and exploit a high-level command injection vulnerability.

1. **Access the Command Injection Page**: Use the same URL.

2. **Interact with the Input Field**:
   - Enter `127.0.0.1` as before.

3. **Use a Different Payload**:
   - Test the following command:
   ```bash
   127.0.0.1 |whoami
   ```
   - Submit and check the response.

4. **Reflection**:
   - Did this command execute successfully? Explain why or why not, considering the input sanitization in place.

---

### **Exercise 4: Impossible Command Injection**

**Objective:** Understand the effect of proper input sanitization.

1. **Access the Command Injection Page**: Remain on the same URL.

2. **Test with Various Inputs**:
   - Input `127.0.0.1` and try various commands, attempting to exploit the input field.

3. **Expected Outcome**:
   - The application should prevent command execution.

4. **Reflection**:
   - Discuss whether the application is secure against command injection based on your tests. What sanitization methods are effective?

---

## Lab Report

### **Student Information**

- **Name:** [Your Name]  
- **Student ID:** [Your ID]  
- **Date:** [Date of Lab]  

### **Exercise Summaries**

For each exercise, please summarize your findings below.

#### **Exercise 1 Summary**
- **Output Observed:**
  - [Document the output received]
- **Implications:**
  - [Discuss the implications of the vulnerability]

---

#### **Exercise 2 Summary**
- **Output Observed:**
  - [Document the output received]
- **Implications:**
  - [Discuss the implications of the vulnerability]

---

#### **Exercise 3 Summary**
- **Output Observed:**
  - [Document the output received]
- **Implications:**
  - [Discuss the implications of the vulnerability]

---

#### **Exercise 4 Summary**
- **Output Observed:**
  - [Document the output received]
- **Implications:**
  - [Discuss the effectiveness of the application’s input sanitization]

---

## Conclusion

In this lab, you have learned about Command Injection vulnerabilities and how they can be exploited at different levels. Take note of the importance of input validation and sanitization to secure applications against such attacks.

### **Submission Instructions**
- Complete your lab report and submit .

---

