

## **INT302: Kali Linux Tools and System Security – Lab 10: DNS Query Tools and SMB Enumeration**

### **Lab Overview**
In this lab, participants will explore essential DNS query tools (`nslookup`, `host`, and `dig`) and learn how to enumerate SMB shares and users using `enum4linux`. This lab will help students understand how to gather information about domains, hosts, and networked services.

---

### **Lab Objectives**
By the end of this lab, you will be able to:
1. Perform DNS queries using various tools to gather domain information.
2. Use `enum4linux` to enumerate SMB shares and users on a target system.
3. Analyze the results to inform penetration testing efforts.

---

### **Tools Used**
- **nslookup**: A command-line tool for querying the Domain Name System (DNS).
- **host**: A simple utility for performing DNS lookups.
- **dig**: A more flexible and detailed DNS query tool.
- **enum4linux**: A tool for gathering information from Windows machines via SMB.

---

### **Prerequisites**
- Basic understanding of DNS and networking concepts.
- Familiarity with command-line operations in Linux.

---

### **Lab Steps**

#### **Step 1: DNS Queries with nslookup, host, and dig**

1. **Using nslookup**:
   - Open your terminal in Kali Linux.
   - Perform a DNS lookup for a live domain:
     ```bash
     nslookup <target-domain>
     ```
   - Example:
     ```bash
     nslookup example.com
     ```

**Exercise 1**:  
- What information did you obtain from the `nslookup` command? Document the IP addresses and any additional records retrieved. __________

2. **Using host**:
   - Run the following command to get similar information:
     ```bash
     host <target-domain>
     ```
   - Example:
     ```bash
     host example.com
     ```

**Exercise 2**:  
- Compare the output of `host` with `nslookup`. What differences did you observe? __________

3. **Using dig**:
   - Perform a more detailed query using `dig`:
     ```bash
     dig <target-domain>
     ```
   - Example:
     ```bash
     dig example.com
     ```

**Exercise 3**:  
- Analyze the output of the `dig` command. What additional information can you extract compared to the previous tools? __________

4. **Advanced DNS Queries**:
   - Query specific DNS record types (e.g., MX, TXT):
     ```bash
     dig <target-domain> MX
     dig <target-domain> TXT
     ```

**Exercise 4**:  
- What did you learn from querying different record types? How can this information be useful in a penetration test? __________

---

#### **Step 2: SMB Enumeration with enum4linux**

1. **Installing enum4linux** (if not already installed):
   - Ensure that `enum4linux` is installed on your system:
     ```bash
     apt install enum4linux
     ```

2. **Using enum4linux**:
   - Perform SMB enumeration on a target IP address:
     ```bash
     enum4linux -a <target-ip>
     ```
   - Example:
     ```bash
     enum4linux -a 192.168.1.5
     ```

**Exercise 5**:  
- What information did you gather about the target system? Document the shares, users, and any other relevant details found. __________

3. **Filtering Results**:
   - Use specific options to filter results (e.g., listing only shares or users):
     ```bash
     enum4linux -S <target-ip>   # Lists shares
     enum4linux -u <target-ip>   # Lists users
     ```

**Exercise 6**:  
- Compare the results obtained from `enum4linux` with your findings from DNS queries. What insights can you gain about the target network? __________

---

### **Step 3: Analyzing and Reporting Findings**

1. **Combining Data**:
   - Analyze the data gathered from DNS queries and SMB enumeration to draw conclusions about the target network's structure and potential vulnerabilities.

2. **Documenting Your Findings**:
   - Create a report summarizing your findings, including:
     - DNS records obtained (A, MX, TXT, etc.).
     - SMB shares and user information.
     - Insights gained from the analysis.

**Exercise 7**:  
- In your report, outline the methodologies used, tools employed, and key insights. Discuss how this information could be useful in a penetration testing engagement. __________

---

### **Conclusion**
In this lab, you gained hands-on experience using `nslookup`, `host`, `dig`, and `enum4linux` for gathering information about domains and networked systems. You learned how to analyze and document your findings effectively.

---

### **Next Steps**
In the next lab, we will focus on advanced enumeration techniques and exploit development.

