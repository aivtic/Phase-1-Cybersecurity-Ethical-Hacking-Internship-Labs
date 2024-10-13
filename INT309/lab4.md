
## **INT309: Web Technologies and Database Security – Lab 4: Advanced SQL Queries, Optimization, and Security Best Practices**

### **Overview**
In this lab, you will expand your knowledge of SQL by learning advanced querying techniques, optimizing database performance, and understanding essential database security practices. Through practical exercises, you will gain hands-on experience with more complex SQL queries, learn how to enhance database performance, and implement best practices for securing your database.

### **Prerequisites**
- Completion of Lab 3: Introduction to Databases and SQL.
- Familiarity with basic SQL queries (SELECT, INSERT, UPDATE, DELETE).
- XAMPP installed with MySQL (from previous lab setup).

### **Lab Objectives**
- Learn advanced SQL querying techniques (JOINs, subqueries, aggregate functions).
- Optimize database performance by indexing and normalizing tables.
- Understand and implement database security best practices (user permissions, encryption, and data sanitization).

### **Exercise Instructions**

---

#### **Exercise 1: Advanced SQL Queries**

1. **Using Aggregate Functions**:
   - Retrieve the total number of students enrolled in each course using `COUNT()`:
     ```sql
     SELECT course_name, COUNT(e.student_id) AS student_count
     FROM courses c
     JOIN enrollments e ON c.course_id = e.course_id
     GROUP BY c.course_name;
     ```

2. **Subqueries for Complex Data Retrieval**:
   - Find the student with the highest number of course enrollments using a subquery:
     ```sql
     SELECT s.first_name, s.last_name
     FROM students s
     WHERE s.student_id = (
       SELECT e.student_id
       FROM enrollments e
       GROUP BY e.student_id
       ORDER BY COUNT(e.course_id) DESC
       LIMIT 1
     );
     ```

3. **Join Multiple Tables**:
   - Write a query to retrieve the list of all students and their courses, even if they are not enrolled in any course:
     ```sql
     SELECT s.first_name, s.last_name, c.course_name
     FROM students s
     LEFT JOIN enrollments e ON s.student_id = e.student_id
     LEFT JOIN courses c ON e.course_id = c.course_id;
     ```

4. **Reflection**:
   - Explain how advanced SQL queries, such as subqueries and aggregate functions, help in extracting more meaningful data from a relational database.

---

#### **Exercise 2: Database Optimization Techniques**

1. **Indexing for Query Performance**:
   - Create an index on the `email` column in the `students` table to speed up search queries:
     ```sql
     CREATE INDEX idx_email ON students(email);
     ```

2. **Check Query Performance Before and After Indexing**:
   - Before creating the index, run the following query and record the time taken:
     ```sql
     SELECT * FROM students WHERE email = 'john.doe@example.com';
     ```
   - After creating the index, run the same query again and compare the performance.

3. **Database Normalization**:
   - Review the current table structure and identify if any redundant data or anomalies exist.
   - If necessary, modify the structure to normalize the database. For instance, if the `students` table had redundant data, suggest how splitting tables (1NF, 2NF) might optimize the database.

4. **Reflection**:
   - Discuss how indexing improves query performance and why normalization is important for reducing redundancy and improving database integrity.

---

#### **Exercise 3: Database Security Best Practices**

1. **Managing User Permissions**:
   - Create a new MySQL user with limited permissions for database access:
     ```sql
     CREATE USER 'limited_user'@'localhost' IDENTIFIED BY 'securepassword';
     GRANT SELECT, INSERT ON student_management_system.* TO 'limited_user'@'localhost';
     ```
   - Ensure that this user cannot delete or modify important data.

2. **Encrypting Sensitive Data**:
   - Demonstrate how to use the `AES_ENCRYPT` function to store encrypted student emails:
     ```sql
     INSERT INTO students (first_name, last_name, email, date_of_birth)
     VALUES ('Alice', 'Cooper', AES_ENCRYPT('alice.cooper@example.com', 'encryptionkey'), '1996-07-20');
     ```

3. **Sanitizing User Input to Prevent SQL Injection**:
   - Simulate a SQL injection vulnerability by allowing unsanitized input:
     ```sql
     SELECT * FROM students WHERE email = '$_GET[email]';
     ```
   - Discuss how using prepared statements or escaping user input prevents SQL injection attacks:
     ```php
     $stmt = $pdo->prepare("SELECT * FROM students WHERE email = ?");
     $stmt->execute([$email]);
     ```

4. **Reflection**:
   - Explain the importance of securing databases through user permissions, encryption, and input sanitization. What are the potential consequences of weak database security?

---

### **Report Submission**
At the end of this lab, you are required to submit a detailed report that includes:

- Your findings from each exercise, including the SQL queries used, optimization techniques applied, and security measures implemented.
- Screenshots demonstrating query performance improvements and successful implementation of encryption and user permissions.
- Reflections on the importance of database optimization and security practices in web applications.

**Submission Format**: Submit your report as a PDF file. Ensure that it is well-organized, and each section clearly explains the task and the results achieved.

---

### **Conclusion**
In this lab, you explored advanced SQL queries, database optimization techniques, and essential security best practices for MySQL databases. These skills are crucial for building secure, high-performance web applications that can handle large datasets efficiently.

