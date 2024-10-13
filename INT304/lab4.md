
### **Lab 4: Intrusion Detection Systems (IDS) and Traffic Analysis on Linux**

#### **Objective:**
This lab aims to familiarize students with setting up and configuring an Intrusion Detection System (IDS) on a Linux machine, analyzing network traffic against the OWASP Broken Web Applications VM IP, and identifying potential security threats.

#### **Materials Required:**
- Linux operating system (Ubuntu, Kali Linux, or similar)
- OWASP Broken Web Applications VM (make sure it's running)
- Snort IDS installed on the Linux machine
- Wireshark installed on the Linux machine
- Terminal access

#### **Lab Tasks:**

1. **Install and Configure Snort:**
   - Ensure you have Snort installed. If not, install it using the following command:
     ```bash
     sudo apt-get update
     sudo apt-get install snort
     ```
   - During installation, you will be prompted to set the network interface. Choose the interface that is connected to the network (e.g., `eth0`, `wlan0`).

2. **Configure Snort:**
   - Open the Snort configuration file for editing:
     ```bash
     sudo nano /etc/snort/snort.conf
     ```
   - Set the `HOME_NET` variable to the OWASP VM IP address (e.g., `192.168.56.101`).
   - Uncomment and adjust any relevant rules to ensure they are active.

3. **Start Snort in IDS Mode:**
   - Run Snort in IDS mode to monitor the network:
     ```bash
     sudo snort -A console -c /etc/snort/snort.conf -i <interface>
     ```
   - Replace `<interface>` with the actual network interface (e.g., `eth0`).

4. **Generate Network Traffic:**
   - Use a tool like `hping3` to generate malicious traffic. First, install `hping3` if not already installed:
     ```bash
     sudo apt-get install hping3
     ```
   - Generate a SYN flood attack towards the OWASP VM:
     ```bash
     hping3 -S -p 80 192.168.56.101
     ```
   - This simulates an attack on the web application running on the OWASP VM.

5. **Monitor Traffic with Wireshark:**
   - Open Wireshark and select the same interface Snort is monitoring.
   - Set a filter to display only TCP traffic:
     ```
     tcp
     ```
   - Observe the incoming packets and look for SYN flood patterns.

6. **Analyze Snort Alerts:**
   - Review the Snort console output for alerts triggered by the SYN flood attack.
   - Take note of the types of alerts and corresponding packet details.

7. **Document Findings:**
   - Create a report summarizing:
     - The steps taken to configure and run Snort.
     - Types of traffic generated and the corresponding alerts triggered by Snort.
     - Screenshots from Wireshark showing packet captures during the attack.
     - Analysis of Snort’s effectiveness in detecting and alerting on the simulated attack.

#### **Submission Requirements:**
- **Format:** Submit your completed report as a PDF document.
- **Content:** Include relevant screenshots, configurations, and analysis.
- **Deadline for submission:** [Insert Deadline Date]

---

### **Conclusion:**
This lab provides hands-on experience in setting up an IDS on a Linux environment, demonstrating how to generate malicious traffic against the OWASP BWA VM and analyze the effectiveness of intrusion detection in a practical setting. Understanding these concepts is crucial for maintaining network security.

---
