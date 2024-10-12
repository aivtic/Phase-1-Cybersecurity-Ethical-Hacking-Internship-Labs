

## **INT302: Kali Linux Tools and System Security – Lab 11: Tor and Proxychains**

### **Lab Overview**
In this lab, participants will explore the use of Tor for anonymous browsing and Proxychains for routing traffic through multiple proxies. This lab will provide students with practical skills to protect their identity and enhance their security while conducting penetration testing and other security-related activities.

---

### **Lab Objectives**
By the end of this lab, you will be able to:
1. Understand how Tor operates and its role in anonymity.
2. Configure and use Proxychains to route network traffic through Tor.
3. Conduct secure browsing and maintain anonymity using Tor and Proxychains.

---

### **Tools Used**
- **Tor**: A free software for enabling anonymous communication over the internet.
- **Proxychains**: A tool that forces any TCP connection made by any given application to follow through proxy (Tor, in this case).

---

### **Prerequisites**
- Basic understanding of networking concepts.
- Familiarity with command-line operations in Linux.

---

### **Lab Steps**

#### **Step 1: Installing Tor and Proxychains**

1. **Installing Tor**:
   - Open your terminal in Kali Linux and install Tor:
     ```bash
     sudo apt update
     sudo apt install tor
     ```

2. **Installing Proxychains**:
   - Ensure Proxychains is installed:
     ```bash
     sudo apt install proxychains
     ```

#### **Step 2: Configuring Tor**

1. **Starting the Tor Service**:
   - Start the Tor service to enable anonymous browsing:
     ```bash
     sudo service tor start
     ```

2. **Verifying Tor is Running**:
   - Check if Tor is running correctly:
     ```bash
     systemctl status tor
     ```

**Exercise 1**:  
- What output do you see when checking the Tor status? Is it running? __________

#### **Step 3: Configuring Proxychains**

1. **Editing Proxychains Configuration**:
   - Open the Proxychains configuration file for editing:
     ```bash
     sudo nano /etc/proxychains.conf
     ```
   - Uncomment the following line to enable Tor:
     ```
     dynamic_chain
     proxy_dns
     [ProxyList]
     # add proxy here ...
     # meanwile
     # defaults set to tor
     socks5 127.0.0.1 9050
     ```

**Exercise 2**:  
- What are the different proxy modes available in Proxychains? Briefly explain each. __________

#### **Step 4: Using Tor with Proxychains**

1. **Testing Anonymity with Curl**:
   - Use Proxychains to make an anonymous request using `curl`:
     ```bash
     proxychains curl https://httpbin.org/ip
     ```

**Exercise 3**:  
- What IP address do you see in the output? How does it compare to your actual IP address? __________

2. **Browsing with Firefox**:
   - Open Firefox with Proxychains to browse the web anonymously:
     ```bash
     proxychains firefox
     ```

**Exercise 4**:  
- Navigate to any website and check your IP address using a service like `https://www.whatismyip.com/`. Does it show the Tor exit node IP address? __________

#### **Step 5: Advanced Usage of Proxychains**

1. **Using Proxychains with Other Tools**:
   - Try using Proxychains with other command-line tools like `nmap`:
     ```bash
     proxychains nmap -sT -Pn <target-ip>
     ```

**Exercise 5**:  
- How does routing your Nmap scans through Tor affect your scanning capabilities? What limitations did you encounter? __________

2. **Combining Proxychains with Other Proxies**:
   - Add additional proxies to the Proxychains configuration file to test different routes.

**Exercise 6**:  
- Experiment with adding another HTTP proxy (e.g., a public proxy server) and rerun your curl command. How does the response change? __________

---

### **Step 6: Analyzing Results**

1. **Understanding Limitations and Risks**:
   - Discuss the limitations of using Tor and Proxychains for anonymity.
   - Consider the potential for traffic analysis and exit node vulnerabilities.

**Exercise 7**:  
- What are some risks associated with using Tor? What precautions can you take while using it? __________

---

### **Conclusion**
In this lab, you gained hands-on experience using Tor for anonymous browsing and Proxychains for routing network traffic. You learned how to configure both tools and analyze their effectiveness in maintaining anonymity online.

---

### **Next Steps**
In the next lab, we will focus on advanced techniques for web application testing, including the use of tools like Burp Suite and OWASP ZAP.

---
