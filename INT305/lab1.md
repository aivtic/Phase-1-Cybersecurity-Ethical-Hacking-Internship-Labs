
### **Lab 1: User Management**

#### **Objective:**
To learn how to create, modify, and manage user accounts securely in a Linux environment, understanding best practices for user account management.

#### **Materials Required:**
- Linux operating system (Ubuntu, Kali Linux, or similar)
- Terminal access with sudo privileges

#### **Tasks:**

1. **Creating User Accounts:**
   - Create a new user account named `student1` using the `adduser` command. This command sets up the user with a home directory and prompts for additional information.
     ```bash
     sudo adduser student1
     ```
   - Verify the user creation by checking the user ID and group information:
     ```bash
     id student1
     ```

2. **Modifying User Accounts:**
   - Change the password for `student1` to ensure security. Follow the prompts to enter and confirm the new password:
     ```bash
     sudo passwd student1
     ```
   - Create a new group called `students` (if it does not already exist) and add `student1` to this group to manage permissions effectively:
     ```bash
     sudo groupadd students  # Only if the group doesn't exist
     sudo usermod -aG students student1
     ```

3. **Locking and Unlocking User Accounts:**
   - Check if `student1` is currently active by listing any processes associated with the user:
     ```bash
     ps -u student1
     ```
   - If there are any active processes, terminate them to ensure the user can be locked:
     ```bash
     sudo pkill -u student1
     ```
   - Lock the user account to prevent `student1` from logging in. This is useful for temporary suspensions:
     ```bash
     sudo usermod -L student1
     ```
   - To unlock the user account, allowing access again:
     ```bash
     sudo usermod -U student1
     ```

4. **Deleting User Accounts:**
   - To delete `student1` while keeping their home directory and files, use:
     ```bash
     sudo deluser student1
     ```
   - To completely remove the user and their home directory, use the following command:
     ```bash
     sudo deluser --remove-home student1
     ```

#### **Exercise:**
1. Create a user named `student1` following the steps outlined above.
2. Add `student1` to the `students` group.
3. Lock the account to prevent access.
4. Delete the user, first keeping their home directory, and then completely removing the user and their files.

#### **Submission Requirements:**
- Document each step you performed in the exercise, including any outputs received from the terminal.
- Submit your report as a PDF, including any challenges faced and how you overcame them.

### **Conclusion:**
This lab provides foundational knowledge and practical experience in user management within Linux, crucial for maintaining secure systems and ensuring appropriate access control for users.

