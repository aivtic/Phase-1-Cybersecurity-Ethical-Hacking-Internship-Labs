

## **INT305: Lab 2: File and Directory Permissions**

### **Objectives**
- Understand how to set and manage permissions for files and directories in Linux.
- Learn the significance of permissions in securing files and directories against unauthorized access.

### **Lab Activities**

#### 1. Understanding Permissions
- Begin by checking the current permissions of a file:
  ```bash
  ls -l filename
  ```
- Learn to change file permissions using numeric mode:
  ```bash
  chmod 755 filename
  ```
- Change file permissions using symbolic mode:
  ```bash
  chmod u+x filename
  ```

#### 2. Managing Directory Permissions
- Set permissions for a directory to allow the owner full access while restricting others:
  ```bash
  chmod 755 directoryname
  ```
- Change the ownership of a directory to a specific user and group:
  ```bash
  chown -R owner:group directoryname
  ```

### **Hands-On Activity**
- Create a directory named `project`:
  ```bash
  mkdir project
  ```
- Set the permissions of the `project` directory to `755`:
  ```bash
  chmod 755 project
  ```
- Change the ownership of the `project` directory to `student1` and the group to `students`:
  ```bash
  chown student1:students project
  ```

### **Exercise**
- Create a directory named `my_project`.
- Set its permissions to `755`.
- Change its ownership to `student1:students`.

### **Deliverables**
- Submit a  report summarizing:
  - The commands used for checking and modifying permissions.
  - The significance of file and directory permissions in cybersecurity.

### **Deadline**
- The report should be submitted by the specified due date, which will be communicated in class.

