

## **INT312 - Basic Networking Skills for Digital Forensics – Lab 3**

### **Lab Title:**  
**Lab on Packet Sniffing and Interception & Lab on DNS Spoofing and ARP Poisoning**

---

### **Objective:**
In this dual lab assignment, you will explore the mechanics of packet sniffing, DNS spoofing, and ARP poisoning attacks. You will simulate a Man-in-the-Middle (MITM) attack to intercept network traffic, redirect users to a fake bank login page, and manipulate DNS traffic to deceive users. By the end of this lab, you will understand how to conduct and analyze DNS spoofing attacks and the security implications involved.

---

## **Part 1: Packet Sniffing and Interception**

### **1. Setup the Lab Environment:**
- **Kali Linux Machine as the Attacker:**
  - Ensure the Kali Linux machine is set up and connected to the same local area network (LAN) as the victim machine.
- **Install Packet Sniffing Tools:**
  - Install and configure tools like **Wireshark** or **tcpdump** for sniffing network packets.

#### **Question:**
- What are the key tools used for packet sniffing in a network? 
- How do they capture and analyze network traffic?

---

### **2. Capturing Network Traffic:**
- **Use Wireshark or tcpdump:**
  - Start capturing network packets while the victim is browsing a legitimate website (e.g., any bank login page).

#### **Task:**
- Take screenshots of the network traffic capture, focusing on HTTP requests, IP addresses, and MAC addresses.

#### **Question:**
- What information can be extracted from the captured packets? 
- Identify any sensitive information (e.g., cookies, passwords, or session IDs).

---

### **3. Analyze Network Traffic:**
- **Filter Traffic in Wireshark:**
  - Focus on HTTP, TCP, and DNS packets.

#### **Task:**
- Document the source IP addresses, destination IP addresses, source MAC addresses, and destination MAC addresses from the captured traffic.

#### **Question:**
- How can this intercepted data be used in a potential attack?

---

## **Part 2: DNS Spoofing and ARP Poisoning**

### **1. DNS Spoofing Traffic Files:**
- **Download DNS Spoofing Traffic Files:**
  - Retrieve the DNS Spoofing Traffic Files from the provided link.

#### **Goal:**
- Simulate a DNS Spoofing attack to redirect users to a fake login page when they type an incorrect URL and analyze the captured traffic to understand how the attack is executed.

---

## **Part 3: DNS Spoofing Attack**

### **1. Launch the Man-In-The-Middle Attack:**
- **ARP Poisoning Attack:**
  - Use Kali Linux to perform an ARP poisoning attack, placing yourself between the victim and the router using tools like **Ettercap** or **Bettercap**.

#### **Task:**
- Capture screenshots of the ARP Poisoning attack in action, showing the ARP table of the victim before and after the attack.

#### **Question:**
- What changes do you notice in the victim’s ARP table after the attack?

---

### **2. DNS Spoofing Setup:**
- **Configure DNS Spoofing:**
  - After launching the MITM attack, set up DNS Spoofing on Kali Linux.
  - Use tools like **dnschef** or **dnsspoof** to intercept DNS queries and provide a fake IP address for the target domain.

#### **Task:**
- Create a fake bank login page using simple HTML/CSS, and host it on the attacker's machine using a web server (e.g., Apache).
- Capture screenshots of the fake login page that users will be redirected to.

---

### **3. Analyze DNS Spoofing Traffic:**
- **Capture and Analyze DNS Traffic:**
  - Use Wireshark or tcpdump to analyze the DNS traffic after the spoofing attack.

#### **Task:**
- Identify the DNS query sent by the victim and the spoofed DNS response provided by the attacker.

#### **Question:**
- What differences do you notice between a normal DNS query/response and a spoofed one? 
- How does the attacker successfully intercept and manipulate the DNS traffic?

---

### **4. Intercepting DNS Responses:**
- **Modify DNS Response:**
  - Using Kali, intercept and modify the DNS response to provide the victim with a fake IP address for the requested domain (e.g., bank.com).

#### **Task:**
- Capture screenshots of the DNS query and response, showing the original DNS server response and the attacker’s forged response.

#### **Question:**
- How does DNS spoofing impact the victim’s browsing experience? 
- What security risks does this pose?

---

## **Part 4: ARP Poisoning and MITM Attack**

### **1. Initiating ARP Poisoning:**
- **Use Ettercap or Bettercap:**
  - Initiate the ARP Poisoning attack to place yourself between the victim and the router.

#### **Task:**
- Take screenshots of the ARP poisoning process, showing the manipulated ARP entries in the victim’s system.

---

### **2. Analyzing ARP Poisoning Impact:**
- **Analyze Captured Traffic:**
  - Use Wireshark to analyze traffic after initiating the ARP poisoning attack. Focus on manipulated traffic, where packets intended for the legitimate DNS server are now sent to the attacker.

#### **Question:**
- How does ARP poisoning facilitate DNS spoofing? 
- What vulnerabilities in the ARP protocol are exploited to perform this attack?

---

## **Part 5: Analysis and Reflection**

### **1. Understanding Key Components of DNS Attacks:**
- **Summarize Key Components:**
  - Summarize the key components of DNS attacks such as ARP poisoning, DNS spoofing, and MITM.

#### **Question:**
- How do these attacks work together to create a successful DNS spoofing attack?

---

### **2. Detecting and Preventing DNS Spoofing:**
- **Reflect on Prevention Methods:**
  - Consider both technical measures (e.g., DNSSEC, ARP spoofing detection tools) and user-level precautions (e.g., SSL/TLS certificates).

#### **Question:**
- How can network administrators protect against DNS spoofing and ARP poisoning attacks?

---

## **Part 6: Additional Questions**

### **1. Analyzing DNS Spoof Traffic:**
- **Thoroughly Analyze Captured Traffic:**
  - Pay attention to the DNS queries, responses, and ARP traffic.

#### **Questions:**
- What are the IP addresses of the victim and the attacker during the attack? 
- What are the MAC addresses?
- How can you differentiate between legitimate and spoofed DNS responses?

---

### **2. Cracking Router Password:**
- **Attempt to Crack the Router Password:**
  - Use tools like **Hydra** or **John the Ripper**.

#### **Task:**
- Document the steps to crack the router’s password and provide screenshots of the process.

#### **Question:**
- What is the password of the router?

---

### **3. Extracting Sensitive Data:**
- **Analyze Packet Capture for Sensitive Information:**
  - Look for credentials, session tokens, or cookies intercepted during the DNS spoofing attack.

#### **Question:**
- Were you able to extract any sensitive data? 
- How could this data be used in a real-world attack?

---

### **4. Ethical and Legal Considerations:**
- **Discuss Ethical and Legal Implications:**
  - Reflect on how penetration testers should handle these attacks in a professional environment.

---

## **Submission Requirements:**
- **Lab Report:** 
  - A detailed PDF document answering all questions, providing analysis, and explaining each step.
- **Screenshots:** 
  - Include clearly labeled screenshots for each task.
- **PCAP File:** 
  - Submit the captured DNS spoof traffic as part of your report.
- **Submission Format:** 
  - Submit all the files in a single ZIP file, not exceeding 5MB.

---

This lab provides hands-on experience with packet sniffing, DNS spoofing, and ARP poisoning, allowing you to understand how attackers manipulate network traffic to intercept sensitive data. Make sure to thoroughly document each step and submit all necessary files for evaluation. Good luck!