

## **INT305: Cybersecurity Fundamentals – Lab 4: SSH Configuration and Security Enhancements**

### **Objectives**
- Configure secure SSH access for remote systems.
- Implement additional security measures for user accounts to enhance overall system security.

### **Lab Activities**

#### 1. Configuring SSH Access
- **Edit the SSH configuration file** to enhance security:
  ```bash
  sudo nano /etc/ssh/sshd_config
  ```
- **Disable root login** to prevent direct root access:
  ```
  PermitRootLogin no
  ```
- **Set the SSH port** to a non-standard port to reduce the risk of automated attacks:
  ```
  Port 2222
  ```
- **Restart the SSH service** to apply changes:
  ```bash
  sudo systemctl restart ssh
  ```

#### 2. Setting Up Key-Based Authentication
- **Generate an SSH key pair** for secure access:
  ```bash
  ssh-keygen -t rsa -b 2048
  ```
- **Copy the public key to the remote server** to enable key-based authentication:
  ```bash
  ssh-copy-id username@remote_host
  ```

#### 3. Implementing Security Enhancements
- **Enforce password aging** by editing the `/etc/login.defs` file:
  ```bash
  PASS_MAX_DAYS 90
  PASS_MIN_DAYS 7
  PASS_MIN_LEN 8
  ```
- **Install and configure `pam_cracklib`** for enforcing password complexity:
  ```bash
  sudo apt-get install libpam-cracklib
  ```
- **Add password complexity rules** in the `/etc/pam.d/common-password` file to require at least one uppercase letter, one lowercase letter, one number, and one special character.

### **Hands-On Activity**
- Disable password authentication for SSH by modifying the `sshd_config` file:
  ```bash
  PasswordAuthentication no
  ```
- Restart the SSH service to apply changes:
  ```bash
  sudo systemctl restart ssh
  ```

### **Exercises**
1. **Verify Key-Based Authentication**:
   - Log in to the remote server as `student1` using the SSH key:
     ```bash
     ssh -p 2222 student1@remote_host
     ```
   - Confirm successful access without entering a password.

2. **Test SSH Security**:
   - Attempt to SSH into the server with an incorrect password for the `student1` account and observe the security logs:
     ```bash
     ssh student1@remote_host
     ```
   - Check the logs for failed login attempts:
     ```bash
     sudo tail -n 50 /var/log/auth.log
     ```

3. **Implement Two-Factor Authentication (Optional)**:
   - Install Google Authenticator or a similar tool:
     ```bash
     sudo apt-get install libpam-google-authenticator
     ```
   - Follow the setup instructions to configure two-factor authentication for SSH logins.

### **Deliverables**
- Submit a brief report (1-2 pages) summarizing:
  - The changes made to the SSH configuration and the rationale behind them.
  - A description of the security enhancements implemented.
  - Insights gained from verifying key-based authentication and reviewing security logs.

### **Deadline**
- The report should be submitted by the specified due date, which will be communicated in class.

---

### **Conclusion**
Through these labs, students will gain practical experience in user management, file and directory permissions, ACLs, sudo privileges, SSH configuration, and implementing security enhancements. Understanding these concepts is essential for effective user access management in Linux.
