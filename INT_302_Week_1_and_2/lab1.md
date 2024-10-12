

## **INT302: Kali Linux Tools and System Security – Lab 1: Reconnaissance (Information Gathering)**

### **Lab Overview**
This lab will guide you through essential reconnaissance techniques to gather preliminary information about a target system or domain during penetration testing. You'll learn to identify IP addresses, retrieve domain registration details, and perform DNS lookups using popular Linux tools such as `ping`, `whois`, and `nslookup`. This hands-on experience will help you gather data that is crucial for vulnerability assessment and further penetration testing.

---

### **Lab Objectives**
By the end of this lab, you will:
1. Use the `ping` command to determine the IP address of a domain.
2. Retrieve domain registration details using the `whois` command.
3. Perform DNS lookups using `nslookup` to gather information about a domain's DNS records.

---

### **Tools Used**
- **Kali Linux**: A Linux distribution used for penetration testing.
- **Terminal**: The command-line interface in Kali Linux to run Linux commands.

---

### **Prerequisites**
- Basic familiarity with Kali Linux and its command-line interface.
- Internet access to run domain lookups.
- An installed and working Kali Linux environment.

---

### **Lab Steps**

#### **Step 1: Get the IP Address of a Domain Using `ping`**

The `ping` command helps you verify the reachability of a domain and returns its IP address.

**Instructions:**
1. Open your **Terminal** in Kali Linux.
2. Run the `ping` command followed by the domain name you want to investigate.

   **Command Syntax**:
   ```bash
   ping <domain>
   ```

   **Example**:
   ```bash
   ping google.com
   ```

**Expected Output**:  
The terminal should return the IP address of the domain along with statistics about packet transmission. For example, `google.com` might return an IP like `142.250.186.206`.

#### **Exercise 1**:  
Use the `ping` command to find the IP addresses of the following domains:
- `facebook.com`
- `twitter.com`
- `amazon.com`

**Record Your Answers**:
1. `facebook.com`: __________
2. `twitter.com`: __________
3. `amazon.com`: __________

---

#### **Step 2: Retrieve Domain Registration Details Using `whois`**

The `whois` command fetches domain registration details such as registrar, creation date, and expiration date.

**Instructions:**
1. In the terminal, use the `whois` command followed by the domain name.

   **Command Syntax**:
   ```bash
   whois <domain>
   ```

   **Example**:
   ```bash
   whois facebook.com
   ```

**Expected Output**:  
You'll see details like:
- Registrar information (e.g., `MarkMonitor Inc.`)
- Domain creation and expiration dates
- Registrant information (if available)

#### **Exercise 2**:  
Run the `whois` command for the following domains:
- `github.com`
- `linkedin.com`
- `apple.com`

**Answer These Questions**:
1. What is the registration expiration date for `github.com`? __________  
2. Who is the registrar for `linkedin.com`? __________  
3. What country is the registrant of `apple.com` from? __________

---

#### **Step 3: Perform a DNS Lookup Using `nslookup`**

The `nslookup` command queries DNS servers to retrieve DNS records and IP addresses.

**Instructions:**
1. Run the `nslookup` command followed by the domain name.

   **Command Syntax**:
   ```bash
   nslookup <domain>
   ```

   **Example**:
   ```bash
   nslookup microsoft.com
   ```

**Expected Output**:  
You will see details like:
- The IP address(es) of the domain
- Name servers (NS)
- DNS record information

#### **Exercise 3**:  
Use `nslookup` to look up DNS information for the following domains:
- `bbc.co.uk`
- `netflix.com`

**Answer These Questions**:
1. What is the IP address for `bbc.co.uk`? __________  
2. What are the name servers (NS) for `netflix.com`? __________

---

### **Submission Instructions**
Submit your results for the exercises above, including:
- IP addresses retrieved using `ping`
- Domain registration details from `whois`
- DNS information from `nslookup`

---

### **Conclusion**
In this lab, you learned the fundamentals of information gathering using basic Linux networking commands. These reconnaissance techniques are essential in any penetration testing engagement, providing crucial details before moving on to more advanced stages of security analysis.

---

### **Next Steps**
In the next lab, we will continue exploring Kali Linux tools by diving deeper into vulnerability scanning and mapping attack surfaces.

