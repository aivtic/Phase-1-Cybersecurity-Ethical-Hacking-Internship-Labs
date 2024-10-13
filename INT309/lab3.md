
## **INT309: Web Technologies and Database Security – Lab 3: Introduction to Databases and SQL**

### **Overview**
In this lab, you will explore the fundamentals of relational databases, focusing on MySQL, one of the most popular database management systems. Through hands-on exercises, you will learn to create and manage databases, build tables, define relationships, and query data using SQL (Structured Query Language). By the end of this lab, you will have a solid understanding of database structure and the basic SQL commands used in real-world applications.

### **Prerequisites**
- Basic knowledge of relational databases and SQL concepts.
- XAMPP installed on your local machine (for Apache server, MySQL, PHP, and Perl).

### **Lab Objectives**
- Understand the basic concepts of relational databases.
- Learn how to set up a MySQL database using XAMPP.
- Create and manage tables with various data types.
- Perform basic SQL queries (SELECT, INSERT, UPDATE, DELETE) and understand their practical applications.

### **Exercise Instructions**

#### **Exercise 1: Setting Up MySQL with XAMPP**

1. **Install and Run XAMPP**:
   - If you haven’t already, download and install XAMPP from [https://www.apachefriends.org/](https://www.apachefriends.org/).
   - Launch XAMPP and start the **Apache** and **MySQL** services from the XAMPP Control Panel.

2. **Access phpMyAdmin**:
   - Open your web browser and navigate to `http://localhost/phpmyadmin/`.
   - phpMyAdmin is a web-based tool provided by XAMPP for managing MySQL databases. 

3. **Create a New Database**:
   - In phpMyAdmin, click on the **Databases** tab.
   - Enter the name `student_management_system` for your new database and click **Create**.
   - This database will store information about students, courses, and enrollments.

4. **Reflection**:
   - Explain why a web application like a Student Management System would need a relational database. What are the benefits of using MySQL in such applications?

---

#### **Exercise 2: Creating Tables and Defining Columns**

1. **Create a `students` Table**:
   - After creating the database, click on the `student_management_system` database.
   - Create a new table named `students` with the following columns:
     - `student_id` (INT, Primary Key, Auto Increment)
     - `first_name` (VARCHAR(50))
     - `last_name` (VARCHAR(50))
     - `email` (VARCHAR(100), Unique)
     - `date_of_birth` (DATE)
   - Click **Save** to create the table.

2. **Create a `courses` Table**:
   - Create a second table named `courses` with the following columns:
     - `course_id` (INT, Primary Key, Auto Increment)
     - `course_name` (VARCHAR(100))
     - `credits` (INT)
   - Click **Save**.

3. **Create an `enrollments` Table** (Relationship Between Students and Courses):
   - Create a third table named `enrollments` to track which students are enrolled in which courses. This table should have the following columns:
     - `enrollment_id` (INT, Primary Key, Auto Increment)
     - `student_id` (INT, Foreign Key referencing `students.student_id`)
     - `course_id` (INT, Foreign Key referencing `courses.course_id`)
     - `enrollment_date` (DATE)
   - Click **Save** to complete the table creation.

4. **Reflection**:
   - Discuss how relationships are established between tables in a relational database. Why are **foreign keys** important in maintaining data integrity?

---

#### **Exercise 3: Inserting Data into the Tables**

1. **Insert Sample Data into the `students` Table**:
   - Open the SQL tab in phpMyAdmin and execute the following SQL statement to insert some students:
     ```sql
     INSERT INTO students (first_name, last_name, email, date_of_birth)
     VALUES 
     ('John', 'Doe', 'john.doe@example.com', '1995-04-12'),
     ('Jane', 'Smith', 'jane.smith@example.com', '1998-09-05'),
     ('Tom', 'Brown', 'tom.brown@example.com', '1997-11-22');
     ```

2. **Insert Sample Data into the `courses` Table**:
   - Insert some sample courses using the following SQL statement:
     ```sql
     INSERT INTO courses (course_name, credits)
     VALUES 
     ('Introduction to Databases', 3),
     ('Web Development', 4),
     ('Cybersecurity Fundamentals', 3);
     ```

3. **Insert Sample Data into the `enrollments` Table**:
   - Enroll the students into different courses using this SQL statement:
     ```sql
     INSERT INTO enrollments (student_id, course_id, enrollment_date)
     VALUES 
     (1, 1, '2024-01-15'),
     (2, 2, '2024-01-17'),
     (3, 3, '2024-01-19'),
     (1, 2, '2024-01-20');
     ```

4. **Reflection**:
   - Explain how inserting data into tables allows the database to become useful for managing information. Why is **data consistency** crucial when inserting related data across tables?

---

#### **Exercise 4: Querying the Database**

1. **Retrieve All Students**:
   - Use a SQL query to retrieve all records from the `students` table:
     ```sql
     SELECT * FROM students;
     ```

2. **Retrieve Students Enrolled in a Specific Course**:
   - Write a SQL query to retrieve students enrolled in "Web Development":
     ```sql
     SELECT s.first_name, s.last_name, c.course_name
     FROM students s
     JOIN enrollments e ON s.student_id = e.student_id
     JOIN courses c ON e.course_id = c.course_id
     WHERE c.course_name = 'Web Development';
     ```

3. **Update a Student’s Email Address**:
   - Update the email address for `John Doe` using the following SQL statement:
     ```sql
     UPDATE students
     SET email = 'john.newemail@example.com'
     WHERE first_name = 'John' AND last_name = 'Doe';
     ```

4. **Delete an Enrollment Record**:
   - Delete the enrollment record for `Jane Smith` from the `enrollments` table:
     ```sql
     DELETE FROM enrollments
     WHERE student_id = 2 AND course_id = 2;
     ```

5. **Reflection**:
   - Discuss how SQL allows you to query and manipulate data in a relational database. How do **JOINs** facilitate retrieving related information from multiple tables?

---

### **Report Submission**
At the end of this lab, you are required to submit a report summarizing your findings and reflections from each exercise. Your report should include:

- Screenshots of your tables and queries.
- A summary of how the `student_management_system` database was designed.
- Reflections on the SQL queries executed, and the importance of relational databases in web applications.
- Any insights into potential improvements for database structure or performance.

**Submission Format**: Submit your report as a PDF file. Ensure that it is well-organized and clearly addresses each part of the lab.

---

### **Conclusion**
In this lab, you learned how to create a MySQL database using XAMPP, design tables with relationships, and perform SQL queries to manage data. Understanding these concepts is essential for building and maintaining secure and efficient web applications.

