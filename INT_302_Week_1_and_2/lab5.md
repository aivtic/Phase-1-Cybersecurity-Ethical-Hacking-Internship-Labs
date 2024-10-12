

## **INT302: Kali Linux Tools and System Security – Lab 5: Wireshark**

### **Lab Overview**
Wireshark is a powerful, open-source network protocol analyzer used for network troubleshooting, analysis, and software development. In this lab, you will learn to capture and analyze network traffic using Wireshark and its command-line tool, `tshark`. Understanding network packets and their structure is crucial for identifying vulnerabilities and securing networks.

---

### **Lab Objectives**
By the end of this lab, you will be able to:
1. Launch and navigate the Wireshark GUI effectively.
2. Capture live network traffic using both Wireshark and `tshark`.
3. Apply filters to isolate and analyze specific packets.
4. Understand packet details, including protocols and their flags.
5. Utilize advanced features such as statistics and graphing.
6. Recognize potential security issues in captured traffic.

---

### **Tools Used**
- **Wireshark**: A graphical network protocol analyzer.
- **tshark**: The terminal-based version of Wireshark.

---

### **Prerequisites**
- Basic knowledge of networking concepts.
- Installed Wireshark on your Kali Linux environment.

---

### **Lab Steps**

#### **Step 1: Launching Wireshark**

1. Open a terminal in Kali Linux.
2. Launch Wireshark by typing the following command:

   **Command**:
   ```bash
   wireshark
   ```

3. Familiarize yourself with the interface, noting the main components:
   - **Capture Interfaces**: Where you can select which network interface to capture from.
   - **Packet List Pane**: Displays a list of captured packets.
   - **Packet Details Pane**: Shows detailed information about the selected packet.
   - **Packet Bytes Pane**: Displays the raw data of the selected packet.
   - **Statistics**: Provides information about protocols, conversations, and endpoints.

**Exercise 1**:  
- Explore the Wireshark GUI. Identify and list the main components you see, including where to find the **Statistics** menu.

---

#### **Step 2: Capturing Network Traffic**

**Using the Wireshark GUI:**

1. Select an interface to capture traffic (e.g., `wlan0` for wireless or `eth0` for wired).
2. Click the **Start Capturing Packets** button (the shark fin icon).
3. Allow the capture to run for a few minutes while you browse the internet or perform other network activities.

**Using `tshark`:**

1. Open a new terminal window.
2. Use the following command to capture packets on a specific interface:

   **Command Syntax**:
   ```bash
   tshark -i <interface>
   ```

   **Example**:
   ```bash
   tshark -i wlan0  # Replace with your actual interface
   ```

**Exercise 2**:  
- Capture network traffic using both Wireshark and `tshark`. Compare the two methods and note any differences in the user experience.

---

#### **Step 3: Analyzing Captured Packets**

1. Stop the packet capture in Wireshark by clicking the **Stop Capturing Packets** button (the red square icon).
2. Analyze the captured packets in the Packet List Pane.
3. Apply display filters to isolate specific types of traffic. Common filters include:
   - Filter for HTTP traffic: `http`
   - Filter for DNS traffic: `dns`
   - Filter for specific IP addresses: `ip.addr == <target IP>`
   - Filter for TCP packets: `tcp`

**Exercise 3**:  
- Use filters to analyze different types of traffic. Record the following:
  - Number of HTTP packets captured: __________
  - Number of DNS packets captured: __________
  - Specific IP addresses you identified in the traffic: __________

---

#### **Step 4: Understanding Packet Details**

1. Click on a packet in the Packet List Pane to view its details in the Packet Details Pane.
2. Expand different protocol layers to understand the encapsulation and the data contained within each packet.

**Key Areas to Focus On**:
- Source and Destination IP Addresses
- Protocol Types (TCP, UDP, ICMP, etc.)
- TCP Flags (SYN, ACK, FIN, etc.)
- Application Layer Protocols (HTTP, DNS, etc.)

**Exercise 4**:  
- Select a packet and list the following information:
  - Source IP: __________
  - Destination IP: __________
  - Protocol: __________
  - Any TCP Flags observed: __________

---

#### **Step 5: Advanced Packet Analysis Techniques**

1. **Follow TCP Stream**: 
   - Right-click on any TCP packet and select **Follow** > **TCP Stream** to see the entire conversation.
   - This feature is useful for understanding the context of the traffic.

**Exercise 5**:  
- Follow a TCP stream for a specific session and summarize the data exchanged between the client and server.

2. **Protocol Hierarchy**: 
   - Navigate to **Statistics** > **Protocol Hierarchy** to see a breakdown of captured protocols.
   - This will help you identify which protocols are most common in your capture.

**Exercise 6**:  
- Take a screenshot of the Protocol Hierarchy and analyze the data. Which protocol is most prevalent in your capture? __________

3. **IO Graphs**: 
   - Access **Statistics** > **IO Graphs** to visualize traffic over time.
   - This can help identify spikes in traffic, indicating potential issues or security events.

**Exercise 7**:  
- Create an IO Graph showing TCP traffic. Describe any noticeable patterns you observe: __________

---

#### **Step 6: Exporting Captured Data**

1. Save your captured packets for further analysis or reporting.
   - Go to **File** > **Save As** and choose a file format (e.g., `.pcap`).

**Exercise 8**:  
- Save your capture file and describe a scenario where you would need to review this data later. What specific findings do you hope to extract?

---

### **Step 7: Practical Applications of Wireshark**

1. **Detecting Network Issues**: 
   - Use Wireshark to analyze a failing network connection or slow performance.
   - Look for excessive retransmissions or packet loss indicators.

**Exercise 9**:  
- Describe a real-world scenario where you would use Wireshark to troubleshoot a network issue. What specific symptoms would you investigate? __________

2. **Security Analysis**:
   - Use Wireshark to identify potential security threats, such as unauthorized access attempts, malware communications, or data exfiltration.
   - Investigate any suspicious packets and document your findings.

**Exercise 10**:  
- Identify at least two potential security threats in your captured traffic. What indicators led you to suspect these activities? __________

---

### **Conclusion**
In this lab, you have gained hands-on experience with Wireshark, capturing and analyzing network traffic. Understanding how to use this tool effectively is essential for network security assessments and troubleshooting network issues. The exercises provided in this lab aim to enhance your skills and prepare you for real-world cybersecurity challenges.

---

### **Next Steps**
In the next lab, we will explore more advanced packet analysis techniques, including dissecting specific protocols, creating custom filters, and identifying vulnerabilities in real-world scenarios.

