
## **INT302: Kali Linux Tools and System Security – Lab 9: Information Gathering with Recon-ng and Shodan**

### **Lab Overview**
In this lab, participants will learn how to use Recon-ng, a powerful reconnaissance framework, and Shodan, a search engine for internet-connected devices. This lab will provide students with practical skills in gathering intelligence about targets and understanding the security landscape of connected devices.

---

### **Lab Objectives**
By the end of this lab, you will be able to:
1. Set up and navigate Recon-ng for conducting reconnaissance.
2. Utilize Shodan to discover information about devices connected to the internet.
3. Extract valuable intelligence for penetration testing and security assessments.
4. Analyze and document findings effectively.

---

### **Tools Used**
- **Recon-ng**: A full-featured Web Reconnaissance framework written in Python.
- **Shodan**: A search engine that lets users find specific types of computers connected to the internet using a variety of filters.

---

### **Prerequisites**
- Basic understanding of reconnaissance techniques and tools.
- Familiarity with command-line operations in Linux.

---

### **Lab Steps**

#### **Step 1: Setting Up Recon-ng**

1. **Launch Recon-ng**:
   - Open your terminal in Kali Linux.
   - Type `recon-ng` to start the framework.

2. **Creating a New Workspace**:
   - Create a new workspace for this lab:
     ```bash
     workspaces create Lab9_Workspace
     ```

3. **Exploring Modules**:
   - List available modules in Recon-ng:
     ```bash
     show modules
     ```
   - Focus on reconnaissance modules such as `domains`, `contacts`, and `social media`.

**Exercise 1**:  
- List the modules that can be used for domain reconnaissance. What are some key modules you might consider? __________

---

#### **Step 2: Using Recon-ng for Information Gathering**

1. **Adding a Domain**:
   - Add a target domain to your workspace:
     ```bash
     add domains <target-domain>
     ```
   - Replace `<target-domain>` with a live domain, e.g., `example.com`.

2. **Running Modules**:
   - Use the `whois` module to gather registration information:
     ```bash
     use recon/domains-hosts/whois
     run
     ```
   - Explore other modules for gathering information such as `social_media`, `contacts`, etc.

**Exercise 2**:  
- Document the registration details obtained from the `whois` module. What information did you find useful? __________

3. **Automating Data Gathering**:
   - Use additional modules for automated data collection, such as:
     ```bash
     use recon/hosts-hosts/resolve
     run
     ```

**Exercise 3**:  
- What new information was discovered about the target domain? List the subdomains or IP addresses obtained. __________

---

#### **Step 3: Setting Up Shodan**

1. **Creating a Shodan Account**:
   - Go to the [Shodan website](https://www.shodan.io/) and create a free account to obtain an API key.
   - Copy your API key for later use.

2. **Installing Shodan CLI** (if not already installed):
   ```bash
   pip install shodan
   ```

3. **Configuring Shodan**:
   - In your terminal, configure Shodan with your API key:
     ```bash
     shodan init <YOUR_API_KEY>
     ```

**Exercise 4**:  
- Verify that your API key is working by running:
  ```bash
  shodan info
  ```

---

#### **Step 4: Using Shodan for Device Discovery**

1. **Searching for Devices**:
   - Use Shodan to find devices related to your target domain:
     ```bash
     shodan search <target-domain>
     ```
   - Example: 
     ```bash
     shodan search example.com
     ```

**Exercise 5**:  
- What devices were discovered related to the target domain? Provide a brief description of the findings. __________

2. **Advanced Searches**:
   - Utilize advanced search filters, such as:
     - `port`: Find devices on specific ports (e.g., `port:22` for SSH).
     - `country`: Limit searches to specific countries (e.g., `country:US`).

**Exercise 6**:  
- Perform an advanced search using two different filters. Document the results and discuss what types of devices you found. __________

---

#### **Step 5: Analyzing and Reporting Findings**

1. **Combining Data**:
   - Compare the information gathered from Recon-ng and Shodan. Identify overlaps and unique findings.
  
2. **Documenting Your Findings**:
   - Create a report summarizing your findings, including:
     - Target domain details.
     - Devices discovered via Shodan.
     - Insights gained from Recon-ng modules.
  
**Exercise 7**:  
- In your report, outline the methodologies used, tools employed, and key insights. Discuss how this information could be useful in a penetration testing engagement. __________

---

### **Conclusion**
In this lab, you gained hands-on experience using Recon-ng and Shodan for information gathering. You learned how to collect and analyze data from multiple sources to inform penetration testing and security assessments.

---

