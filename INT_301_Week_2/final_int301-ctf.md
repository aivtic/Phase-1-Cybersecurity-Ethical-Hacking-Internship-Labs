### **Linux Capture The Flag (CTF) Challenge: Command, Networking, Permissions & Basic Bash Scripting**

---

# **CTF Overview:**

**Objective:**  
In this challenge, you will navigate through a series of real-world Linux-based scenarios on your **local machine**. Each challenge will require you to use Linux commands, understand networking concepts, manage file permissions, and use basic bash scripting. Your goal is to find the hidden flags, which represent critical pieces of information that an attacker could exploit. 

You will complete the challenges directly on your system, using terminal commands to simulate real attacks, and then apply your Linux knowledge to secure the environment.

---

## **Scenario 1: Misconfigured Permissions and Hidden Flag**

**Story:**
As a system administrator, you’ve discovered that someone has misconfigured file permissions on a critical file, leaving it world-readable. An attacker has placed a flag in this file, and you must find it and fix the permissions.

**Your Task:**
1. **Simulate the Vulnerability**: Create a file with insecure permissions and add a flag inside it.
   ```bash
   sudo touch /tmp/secret.txt
   sudo chmod 777 /tmp/secret.txt
   echo "flag{permissions_misconfigured}" > /tmp/secret.txt
   ```

**Objective:**
- Find the file with incorrect permissions by listing all files in `/tmp` with `ls -l`.
   ```bash
   ls -l /tmp
   ```
- Capture the flag by reading the contents of the file.
   ```bash
   cat /tmp/secret.txt
   ```

**Flag:** `flag{permissions_misconfigured}`  
**Bonus:** Correct the permissions using `chmod 600 /tmp/secret.txt`.

---

## **Scenario 2: Basic Bash Scripting – Automating Flag Discovery**

**Story:**
You need to create a bash script that automatically searches for hidden flags inside a specific directory. The attacker has left several flags across multiple directories, and you need to automate the process of finding them.

**Your Task:**
1. **Simulate the Attack**: Create a few hidden files in a directory with flags inside them.
   ```bash
   mkdir ~/flags_dir
   echo "flag{bash_script_discovered_1}" > ~/flags_dir/.flag1
   echo "flag{bash_script_discovered_2}" > ~/flags_dir/.flag2
   ```

2. **Write a Bash Script**: Create a script called `flag_finder.sh` to search for hidden files and extract their contents.
   ```bash
   #!/bin/bash
   find ~/flags_dir -name ".*" -exec cat {} \;
   ```

**Objective:**
- Run the bash script and capture the flags.
   ```bash
   bash flag_finder.sh
   ```

**Flags:** `flag{bash_script_discovered_1}`, `flag{bash_script_discovered_2}`  
**Bonus:** Extend the script to find flags across multiple directories.

---

## **Scenario 3: Networking – Trace the Attacker's IP Address**

**Story:**
An attacker has logged into your system through SSH from a suspicious IP address. You need to trace this IP and capture the flag.

**Your Task:**
1. **Simulate the Attack**: Add fake SSH login entries to `/var/log/auth.log` with a hidden flag.
   ```bash
   sudo echo "Accepted password for root from 192.168.1.100 port 22 ssh2" >> /var/log/auth.log
   sudo echo "flag{ssh_attack_ip_traced}" >> /var/log/auth.log
   ```

**Objective:**
- Use `grep` to search for the attacker's IP in the log file.
   ```bash
   grep "192.168.1.100" /var/log/auth.log
   ```

**Flag:** `flag{ssh_attack_ip_traced}`  
**Bonus:** Secure your SSH configuration by disabling password authentication.

---

## **Scenario 4: Network Interface Monitoring**

**Story:**
You suspect there’s been unusual network activity on your system. You need to monitor your network interface to capture traffic and locate the hidden flag left by the attacker.

**Your Task:**
1. **Simulate the Attack**: Create a log file with network interface activity and a hidden flag.
   ```bash
   echo "eth0: RX packets 100 TX packets 200" > /tmp/network.log
   echo "flag{network_monitoring_successful}" >> /tmp/network.log
   ```

**Objective:**
- Use `ifconfig` to monitor network interfaces and `grep` to locate the flag in the log file.
   ```bash
   ifconfig eth0
   grep "flag" /tmp/network.log
   ```

**Flag:** `flag{network_monitoring_successful}`  
**Bonus:** Set up network traffic monitoring using `tcpdump` or `netstat`.

---

## **Scenario 5: SSH Brute-Force Attack Simulation**

**Story:**
The system has experienced a brute-force attack, where multiple SSH login attempts were made from various IP addresses. You must identify the malicious IP addresses and capture the flag.

**Your Task:**
1. **Simulate the Attack**: Add multiple SSH login attempts to the `/var/log/auth.log` file with a hidden flag.
   ```bash
   sudo echo "Failed password for root from 203.0.113.5" >> /var/log/auth.log
   sudo echo "Failed password for root from 198.51.100.2" >> /var/log/auth.log
   sudo echo "flag{ssh_bruteforce_flag}" >> /var/log/auth.log
   ```

**Objective:**
- Use `grep` to find all failed SSH login attempts and capture the flag.
   ```bash
   grep "Failed password" /var/log/auth.log
   ```

**Flag:** `flag{ssh_bruteforce_flag}`  
**Bonus:** Block the IP addresses using `iptables` or `ufw`.

---

## **Scenario 6: Permissions Escalation**

**Story:**
The attacker has created a SUID binary that can be exploited to elevate privileges. Your job is to locate this binary, capture the flag, and secure the system.

**Your Task:**
1. **Simulate the Attack**: Create a file with SUID permissions and hide a flag in it.
   ```bash
   sudo touch /usr/local/bin/suid_exploit
   sudo chmod u+s /usr/local/bin/suid_exploit
   echo "flag{suid_privilege_escalation}" > /usr/local/bin/suid_exploit
   ```

**Objective:**
- Use `find` to locate files with SUID permissions and read the flag.
   ```bash
   find / -perm /4000 2>/dev/null
   cat /usr/local/bin/suid_exploit
   ```

**Flag:** `flag{suid_privilege_escalation}`  
**Bonus:** Secure your system by removing unauthorized SUID binaries.

---

## **Scenario 7: Creating and Scheduling a Malicious Cron Job**

**Story:**
An attacker has scheduled a malicious cron job that runs a script every minute to leak sensitive information. Your task is to uncover this cron job and capture the flag.

**Your Task:**
1. **Simulate the Attack**: Create a cron job that writes a flag to a log file every minute.
   ```bash
   echo "* * * * * echo 'flag{cron_job_discovered}' >> /tmp/cron.log" | sudo tee /var/spool/cron/crontabs/root
   ```

**Objective:**
- Use `crontab -l` to list the cron jobs and check `/tmp/cron.log` for the flag.
   ```bash
   crontab -l
   cat /tmp/cron.log
   ```

**Flag:** `flag{cron_job_discovered}`  
**Bonus:** Remove the malicious cron job and clean up the logs.

---

## **Scenario 8: File Integrity Monitoring with Hashing**

**Story:**
You suspect that critical system files have been tampered with. Your task is to check the integrity of a file by comparing its hash value before and after the suspected modification.

**Your Task:**
1. **Simulate the Attack**: Modify a critical file and add a hidden flag inside.
   ```bash
   echo "flag{file_integrity_compromised}" >> /etc/hostname
   ```

**Objective:**
- Calculate the hash of the file using `sha256sum` and detect the change.
   ```bash
   sha256sum /etc/hostname
   ```

**Flag:** `flag{file_integrity_compromised}`  
**Bonus:** Restore the file’s integrity by removing the unauthorized changes.

---

## **Scenario 9: IP Table Configuration and Firewall Setup**

**Story:**
An attacker has altered your firewall rules, leaving your system exposed. You need to check your current IP table rules, find the flag, and restore proper security.

**Your Task:**
1. **Simulate the Attack**: Add a flag to your current IP table rules.
   ```bash
   sudo iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT
   echo "flag{iptables_flag}" >> /etc/iptables/rules.v4
   ```

**Objective:**
- Use `iptables -L` to review the rules and capture the flag from the file.
   ```bash
   iptables -L
   cat /etc/iptables/rules.v4
   ```

**Flag:** `flag{iptables_flag}`  
**Bonus:** Harden your firewall by blocking all unnecessary ports and IP ranges.

---

## **Completion:**

Congratulations! You

 have successfully completed the Linux CTF challenge. By finding all the flags, you’ve gained hands-on experience with Linux commands, networking, file permissions, and bash scripting.

