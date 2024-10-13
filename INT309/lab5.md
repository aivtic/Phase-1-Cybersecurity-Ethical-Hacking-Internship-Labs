

## **INT309: Web Technologies and Database Security – Lab 5: Database Backup, Restoration, and Securing Access**

### **Overview**
In this final lab, you will learn two critical components of database management and security: **Database Backup and Restoration**, and **Securing Database Access in Web Applications**. Mastering these skills will prepare you to protect sensitive data, ensure business continuity, and secure your databases from unauthorized access.

### **Lab Objectives**
- Learn the steps to back up and restore a MySQL database using **phpMyAdmin** and the **MySQL command line**.
- Understand how to automate backups for production environments using **cron jobs** and **scheduled tasks**.
- Implement security measures to protect database access in web applications, including **user privilege management**, **connection encryption**, and **SQL injection prevention**.

### **Prerequisites**
- A running **XAMPP** server with **MySQL** and **phpMyAdmin**.
- Knowledge of basic SQL commands and working with MySQL databases.
- Basic familiarity with PHP for database access in web applications.

---

### **Exercise Instructions**

#### **Exercise 1: Database Backup Using phpMyAdmin**
1. **Open phpMyAdmin**:
   - Access **phpMyAdmin** via your XAMPP control panel.

2. **Select Database for Backup**:
   - Choose an existing database you’ve created during previous labs (e.g., a database for a web application).

3. **Export the Database**:
   - Navigate to the **Export** tab and choose the **Quick Export** method to back up your entire database structure and data.

4. **Save the Export**:
   - Download the exported `.sql` file and save it as a backup.

5. **Reflection**:
   - Discuss the importance of regular backups and how quick exports via phpMyAdmin can help prevent data loss.

---

#### **Exercise 2: Manual Backup Using MySQL Command Line**
1. **Open the Command Line Interface**:
   - Access the MySQL command line by opening the **XAMPP Shell**.

2. **Run the Backup Command**:
   - Use the `mysqldump` command to manually back up the same database. The syntax should look like this:
   ```bash
   mysqldump -u root -p your_database_name > backup_name.sql
   ```

3. **Reflection**:
   - Compare the manual command-line method with phpMyAdmin. When would it be beneficial to use each approach?

---

#### **Exercise 3: Automating Database Backups (Cron Jobs for Linux or Scheduled Tasks for Windows)**
1. **Set Up a Cron Job (Linux)**:
   - On a Linux machine or virtual machine, configure a cron job to automatically back up the database every day at a specific time:
   ```bash
   0 2 * * * mysqldump -u root -p your_database_name > /path_to_backup/backup_name.sql
   ```

2. **Set Up a Scheduled Task (Windows)**:
   - On Windows, use the **Task Scheduler** to automate a MySQL backup, specifying the command in a batch file that runs daily.

3. **Reflection**:
   - Explain how automating backups reduces the risk of data loss in production systems.

---

#### **Exercise 4: Restoring Databases**
1. **Restore via phpMyAdmin**:
   - Simulate a data loss scenario. Use phpMyAdmin’s **Import** feature to restore the database from the `.sql` file you created earlier.

2. **Restore via MySQL Command Line**:
   - Similarly, restore the database using the MySQL command line:
   ```bash
   mysql -u root -p your_database_name < backup_name.sql
   ```

3. **Reflection**:
   - Discuss the importance of testing backups regularly to ensure their integrity.

---

#### **Exercise 5: Securing Database Access in Web Applications**
1. **User Privilege Management**:
   - In **phpMyAdmin**, create a new MySQL user account with **limited privileges** (e.g., SELECT, INSERT) specifically for a web application.
   - Limit access to only the necessary tables to practice the principle of **least privilege**.

2. **Encrypting Connections**:
   - Enable SSL for MySQL connections to ensure secure communication between the database and the web server. Discuss how to implement this in a production environment.

3. **SQL Injection Prevention**:
   - Update a PHP web application to use **prepared statements** with **PDO** or **MySQLi** to prevent SQL injection attacks. Here’s an example:
   ```php
   $stmt = $pdo->prepare('SELECT * FROM users WHERE username = :username');
   $stmt->execute(['username' => $user_input]);
   $user = $stmt->fetch();
   ```

4. **Reflection**:
   - Summarize the importance of limiting database access and using secure methods to connect to and query the database.

---

### **Lab Conclusion**
In this final lab, you have gained hands-on experience in essential tasks for managing and securing databases in a web application environment. From automating backup processes to restoring databases in the event of failure, you now understand the importance of ensuring data availability. Furthermore, securing access to databases in web applications reinforces the significance of protection against unauthorized access and vulnerabilities like SQL injection.

### **Report Submission**
Prepare and submit a comprehensive PDF report summarizing your:
- Backup and restoration processes (with screenshots and commands used).
- Reflections on automating backups.
- Insights gained from securing database access.
- Code snippets and screenshots for SQL injection prevention techniques.

**Submission Format**: PDF report, no larger than 5MB. 

---

### **Celebrating Completion**
Congratulations on completing the final lab! You are now equipped with practical skills in database management and security, vital for real-world web development and administration. Your journey doesn’t stop here. Continue to explore advanced topics like **database optimization** and **scaling** for large-scale applications, and always prioritize data security in your future projects.
