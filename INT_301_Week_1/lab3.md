
# Lab 3: Networking Commands

## Objectives
In this lab, you will:
- Learn how to use basic and advanced networking commands.
- Understand how to configure network interfaces and diagnose network issues.
- Use tools to monitor and analyze network traffic.

## Background / Scenario
Networking is a fundamental aspect of cybersecurity and system administration. Familiarity with networking commands allows you to configure, manage, and troubleshoot network connections effectively. Kali Linux includes a range of powerful tools for networking, making it an essential skill for ethical hackers and security professionals.

## Required Resources
- Kali Linux virtual machine (VM).
- Internet access.

## Instructions

### Part 1: Displaying Network Configuration

1. **Open a Terminal**:
   - Start your Kali Linux VM.
   - Open a terminal by clicking the terminal icon.

2. **Check Network Interfaces**:
   - Use the following command to display the current network interfaces and their configuration:
   ```bash
   ip addr show
   ```
   - **Explanation**: The `ip addr show` command provides detailed information about all network interfaces, including IP addresses, MAC addresses, and status.

   - **Example Output**:
     ```
     2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
         link/ether 08:00:27:12:34:56 brd ff:ff:ff:ff:ff:ff
         inet 192.168.1.10/24 brd 192.168.1.255 scope global eth0
         valid_lft forever preferred_lft forever
     ```

3. **List Routing Table**:
   - To view the routing table, run:
   ```bash
   ip route show
   ```
   - **Explanation**: This command displays the routing table, which contains information on how packets are routed through the network.

   - **Example Output**:
     ```
     default via 192.168.1.1 dev eth0
     192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
     ```

### Part 2: Testing Network Connectivity

1. **Ping a Host**:
   - Use the `ping` command to test connectivity to a remote host, such as Google:
   ```bash
   ping -c 4 google.com
   ```
   - **Explanation**: The `-c 4` option sends 4 packets. The `ping` command checks if the host is reachable and measures the round-trip time for messages sent.

   - **Example Output**:
     ```
     PING google.com (172.217.5.110) 56(84) bytes of data.
     64 bytes from lhr25s10-in-f14.1e100.net: icmp_seq=1 ttl=118 time=10.4 ms
     ...
     ```

2. **Trace Route to a Host**:
   - Use the `traceroute` command to see the path packets take to a destination:
   ```bash
   traceroute google.com
   ```
   - **Explanation**: `traceroute` shows the sequence of hops between your machine and the destination, helping diagnose where delays or failures occur.

   - **Example Output**:
     ```
     traceroute to google.com (172.217.5.110), 30 hops max, 60 byte packets
      1  router.local (192.168.1.1)  1.234 ms  1.012 ms  1.003 ms
      2  10.0.0.1 (10.0.0.1)  10.234 ms  10.012 ms  10.003 ms
      ...
     ```

### Part 3: Configuring Network Interfaces

1. **View Current Interface Configuration**:
   - Use the following command to see the current settings for your network interfaces:
   ```bash
   ifconfig
   ```
   - **Explanation**: The `ifconfig` command displays the configuration of all active network interfaces.

   - **Example Output**:
     ```
     eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
             inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
             ...
     ```

2. **Manually Configure an Interface**:
   - To assign a static IP address to an interface (for example, `eth0`), use:
   ```bash
   sudo ip addr add 192.168.1.20/24 dev eth0
   ```
   - **Explanation**: This command assigns the IP address `192.168.1.20` with a subnet mask of `255.255.255.0` to the interface `eth0`.

3. **Bring the Interface Up**:
   - Activate the configured interface with:
   ```bash
   sudo ip link set eth0 up
   ```
   - **Explanation**: This command enables the specified interface, making it active.

### Part 4: Monitoring Network Traffic

1. **Install `tcpdump`**:
   - Use the following command to install `tcpdump`, a powerful packet analysis tool:
   ```bash
   sudo apt install tcpdump
   ```
   - **Explanation**: This command installs `tcpdump`, allowing you to capture and analyze network traffic.

   - **Example Output**:
     ```
     The following NEW packages will be installed:
       tcpdump
     ...
     ```

2. **Capture Network Traffic**:
   - Use `tcpdump` to capture packets on `eth0`:
   ```bash
   sudo tcpdump -i eth0 -c 10
   ```
   - **Explanation**: The `-i` option specifies the interface, and `-c 10` limits the capture to 10 packets.

   - **Example Output**:
     ```
     10:30:01.123456 IP 192.168.1.10 > 192.168.1.1: ICMP echo request, id 1234, seq 1, length 64
     10:30:01.123457 IP 192.168.1.1 > 192.168.1.10: ICMP echo reply, id 1234, seq 1, length 64
     ...
     ```

3. **Analyze Network Traffic**:
   - To see live traffic, run:
   ```bash
   sudo tcpdump -i eth0
   ```
   - **Explanation**: This command captures and displays all traffic on `eth0` in real-time. Use `Ctrl + C` to stop the capture.

### Part 5: Final Review

1. **Check Network Status**:
   - Use the following command to see the status of all interfaces:
   ```bash
   nmcli device status
   ```
   - **Explanation**: This command provides a summary of all network interfaces, showing their connection status.

   - **Example Output**:
     ```
     DEVICE  TYPE      STATE        CONNECTION
     eth0    ethernet  connected    Wired connection 1
     wlan0   wifi      disconnected  --
     ```

2. **Check Firewall Status**:
   - Check if the firewall is active and what rules are in place:
   ```bash
   sudo ufw status verbose
   ```
   - **Explanation**: This command shows the status of the Uncomplicated Firewall (UFW) and its rules.

   - **Example Output**:
     ```
     Status: active
     To                         Action      From
     --                         ------      ----
     22/tcp                     ALLOW       Anywhere
     ```

### Conclusion
In this lab, you have learned essential networking commands and tools available in Kali Linux. Mastery of these commands allows you to effectively manage and troubleshoot network connections, which is crucial in cybersecurity roles.

