

## **INT312 - Basic Networking Skills for Digital Forensics – Lab 2**

### **Lab Title:**  
**Capturing and Analyzing HTTP Traffic with Embedded Images**

---

### **Objective:**
This lab focuses on capturing and analyzing HTTP traffic, including extracting images transmitted over the network. By the end of this lab, you will understand how to capture, analyze, and extract data from network traffic, which is a crucial skill in digital forensics.

---

### **Part 1: Capture HTTP Traffic**

1. **Set Up Wireshark:**
   - Open Wireshark and select the appropriate network interface (e.g., Wi-Fi or Ethernet).
   - Start capturing packets before making an HTTP request to a website that contains an embedded image.

2. **Access a Website with an Embedded Image:**
   - Open a web browser and navigate to a website with an embedded image (you may choose any website that you like or use the example below):
     ```plaintext
     http://example.com
     ```

3. **Stop the Capture:**
   - After the page loads, stop the packet capture in Wireshark.

---

### **Part 2: Captured HTTP Traffic Overview**

1. **Identify the HTTP GET Request:**
   - In Wireshark, filter the traffic to show only HTTP packets:
     ```plaintext
     http
     ```
   - Look for the second HTTP GET request in the list of captured packets. 

2. **Analyze the Second HTTP GET Request/Response:**
   - Click on the second HTTP GET request packet.
   - Analyze the following details:
     - **Request Line:** Check the URL being requested.
     - **Headers:** Review relevant headers such as `User-Agent`, `Accept`, `Host`, etc.
   - Locate the corresponding HTTP response packet.
     - **Status Code:** Check if the response is successful (200 OK).
     - **Headers:** Review the `Content-Type` and `Content-Length` headers.
     - **Payload:** If the response contains an image, identify the details related to the image.

3. **Capture Screenshots:**
   - Take screenshots of:
     - The Wireshark packet details for both the GET request and response.
     - The page displaying the embedded image in the browser.

---

### **Part 3: Extract the Image from HTTP Traffic**

1. **Extract the Image File:**
   - Use the following command to extract the image file from the captured HTTP traffic:
     ```bash
     wget https://raw.githubusercontent.com/frankwxu/digital-forensics-lab/main/Illegal_Possession_Images/lab_files/traffic/image2.log
     ```
   - Once downloaded, you will analyze the contents of `image2.log`.

2. **Analyze the Extracted Log File:**
   - Open the `image2.log` file and examine its contents.
   - Identify the bytes corresponding to the image data. You may need to locate the `Content-Type` header to confirm the image format (e.g., JPEG).
   - Use tools like `xxd` or `hexdump` to visualize the raw data in the log file.

---

### **Part 4: Size Relation Between IP Packet and TCP Payload**

1. **Calculate Size Relation:**
   - Analyze the captured packets to calculate the sizes of the IP packets and the TCP payloads.
   - Document the sizes of the following:
     - **IP Packet Size:** This includes the entire IP header and the TCP segment.
     - **TCP Payload Size:** This is the size of the data carried by the TCP segment (excluding headers).
   - You can find these sizes in the Wireshark packet details. Look for:
     - **IP Packet Size:** Found in the `IP` section under `Length`.
     - **TCP Payload Size:** Found in the `TCP` section under `Length`.

2. **Document Your Findings:**
   - Create a table to summarize the sizes for comparison.

---

### **Submission Requirements:**

- Submit a PDF file containing:
  - Screenshots of the HTTP GET request and response packets.
  - Analysis of the second HTTP GET request and response.
  - Documentation of the extracted image process.
  - Summary table showing the size relation between IP packets and TCP payloads.

- Ensure that your file is well-organized and includes your name and student ID at the top of the document.

---

### **Grading Criteria:**

- **Correctness:** Accuracy of captured information and analysis.
- **Clarity:** Clear explanations of processes and captured data.
- **Documentation:** Thorough documentation of steps, findings, and image extraction.
- **Presentation:** Well-organized submission with proper formatting.

---

### **Important Notes:**

- This lab will enhance your understanding of HTTP traffic analysis and the relationship between network layers.
- Feel free to explore additional features of Wireshark and tools for further analysis.

---

Good luck with your lab!