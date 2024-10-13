Here's the enhanced **Lab 1: User Management** with the **Exercise** section added:

---

## **INT304: Network Security and Protocols – Lab 1: User Management**

### **Objectives**
- Learn how to create, modify, and manage user accounts securely in Linux.
- Understand the importance of user account management for maintaining system security.
- Practice best practices in user administration, including user creation, modification, and deletion.

### **Lab Activities**

#### **Overview of User Management**
- Begin by reviewing the materials on user management in Linux. Focus on understanding the significance of secure user account management in preventing unauthorized access to systems.

#### **Creating User Accounts**
- Create a new user named `student1` using the following command:
  ```bash
  sudo adduser student1
  ```
- Verify that the user account has been created successfully:
  ```bash
  id student1
  ```

#### **Modifying User Accounts**
- Change the password for `student1` to ensure secure access:
  ```bash
  sudo passwd student1
  ```
- Create a group named `students` and add `student1` to this group to manage permissions effectively:
  ```bash
  sudo groupadd students  # Only if the group doesn't exist
  sudo usermod -aG students student1
  ```

#### **Locking and Unlocking User Accounts**
- Check for any active processes associated with `student1`:
  ```bash
  ps -u student1
  ```
- Terminate any processes if necessary:
  ```bash
  sudo pkill -u student1
  ```
- Lock the user account:
  ```bash
  sudo usermod -L student1
  ```
- Unlock the user account when needed:
  ```bash
  sudo usermod -U student1
  ```

#### **Deleting User Accounts**
- Delete `student1` while keeping their home directory:
  ```bash
  sudo deluser student1
  ```
- Completely remove the user and their home directory:
  ```bash
  sudo deluser --remove-home student1
  ```

### **Exercise**
1. **User Account Creation and Modification:**
   - Create a user named `student1`.
   - Add `student1` to the group `students`.
   - Change the password for `student1` to a secure value.

2. **Account Locking and Unlocking:**
   - Check for any active processes under `student1` and terminate them if necessary.
   - Lock the `student1` account and verify that the account is locked.
   - Unlock the account and confirm it is accessible again.

3. **User Account Deletion:**
   - Delete the `student1` user account while keeping the home directory.
   - Finally, remove `student1` completely, including their home directory.

### **Hands-On Activity**
- Perform the tasks outlined above in a Linux environment.
- Document each command executed and any outputs received.
- Reflect on the implications of user management practices in maintaining system security.

### **Group Discussion**
- Discuss the importance of secure user account management in operating systems.
- Encourage participants to share their experiences and challenges faced during the hands-on activities.

### **Deliverables**
- Compile a report summarizing your findings from the lab activities, including:
  - Steps taken to create, modify, lock, unlock, and delete user accounts.
  - Challenges encountered and how they were addressed.
  - Insights gained regarding user management practices.

### **Deadline**
The report should be submitted by the specified due date, which will be communicated in class.

