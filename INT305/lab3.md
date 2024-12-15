
## **INT305:Lab 3: Access Control Lists (ACLs) and Sudo Privileges**

### **Objectives**
- Configure Access Control Lists (ACLs) for enhanced file and directory permissions.
- Manage and understand sudo privileges to allow users administrative access.

### **Lab Activities**

#### 1. Working with ACLs
- **View ACLs** for a file or directory:
  ```bash
  getfacl filename
  ```
- **Set ACLs** to grant specific user access:
  ```bash
  setfacl -m u:student2:rw filename
  ```
- **Remove ACLs** to revoke user access:
  ```bash
  setfacl -x u:student2 filename
  ```

#### 2. Managing Sudo Privileges
- **Edit the sudoers file** using the visudo command for safe editing:
  ```bash
  sudo visudo
  ```
- **Grant `student1` sudo access** without requiring a password:
  ```
  student1 ALL=(ALL) NOPASSWD: ALL
  ```

### **Hands-On Activity**
- Apply an ACL to the `project` directory to grant `student2` read and execute permissions:
  ```bash
  setfacl -m u:student2:rx project
  ```
- Verify the ACL settings:
  ```bash
  getfacl project
  ```

### **Exercise**
- Test `student1`’s sudo access by running the following command:
  ```bash
  sudo whoami
  ```
- Confirm that the output is `root`, indicating successful sudo access.

### **Deliverables**
- Submit a report  summarizing:
  - The commands used to manage ACLs and sudo privileges.
  - The significance of ACLs in managing fine-grained access control.

### **Deadline**
- The report should be submitted by the specified due date, which will be communicated in class.

