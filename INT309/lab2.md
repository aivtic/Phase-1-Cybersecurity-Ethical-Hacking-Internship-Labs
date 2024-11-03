

## **INT309: Web Technologies and Database Security – Lab 2: Web Development Components and Security Threats**

### **Overview**
In this lab, you will explore the various components involved in web development, including front-end and back-end technologies. You will also identify and analyze common security threats associated with these components. Through practical exercises, you will gain hands-on experience in recognizing vulnerabilities and implementing secure coding practices.

### **Prerequisites**
- Basic knowledge of HTML, CSS, and JavaScript.
- Familiarity with server-side programming languages (e.g., PHP, Node.js).
- Access to a web development environment (e.g., local server, cloud platform).

### **Lab Objectives**
- Understand the key components of web development (front-end and back-end).
- Identify common security threats associated with web development components.
- Analyze the implications of these threats on web applications.
- Implement basic secure coding practices to mitigate vulnerabilities.

### **Exercise Instructions**

#### **Exercise 1: Exploring Front-End Development Components**

1. **Identify Front-End Technologies**:
   - Research and create a list of common front-end technologies used in web development, including:
     - HTML
     - CSS
     - JavaScript
     - Front-end frameworks (e.g., React, Angular, Vue.js)

2. **Create a Simple Front-End Application**:
   - Build a basic web application using HTML, CSS, and JavaScript that includes:
     - A header with a navigation menu.
     - A form for user input (e.g., contact form).
     - Interactive elements (e.g., a button that changes the text when clicked).
   - **Example Code Snippet**:
     ```<?php
// config.php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "test1";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}



// Get form input
$firstname = $_POST['firstname'];
$lastname = $_POST['lastname'];
$school = $_POST['school'];

// 1. SQL Injection Vulnerability (Improperly sanitized query)
$sql = "INSERT INTO users (firstname, lastname, school) VALUES ('$firstname', '$lastname', '$school')";
$conn->query($sql);

// Retrieve all records to demonstrate XSS vulnerability
$result = $conn->query("SELECT * FROM users");



?>



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Front-End App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Contact Us</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <form id="contactForm" action="" method="POST">
            <label for="firstname">First Name:</label>
            <input type="text" name="firstname" id="firstname" required>

            <label for="lastname">Last Name:</label>
            <input type="text" name="lastname" id="lastname" required>

            <label for="school">School:</label>
            <input type="text" name="school" id="school" required>

            <button type="submit">Submit</button>
        </form>
    </main>
    <script src="script.js"></script>


    <title>Form Submission Result</title>
</head>
<body>
    <h1>Submitted Data</h1>
    <p>Thank you, <?php echo $firstname; ?>! Here is the data:</p>

    <table border="1">
        <tr>
            <th>First Name</th>
            <th>Last Name</th>
            <th>School</th>
        </tr>
        <?php while ($row = $result->fetch_assoc()): ?>
        <tr>
            <!-- 2. XSS Vulnerability: Output is not sanitized -->
            <td><?php echo $row['firstname']; ?></td>
            <td><?php echo $row['lastname']; ?></td>
            <td><?php echo $row['school']; ?></td>
        </tr>
        <?php endwhile; ?>
    </table>

    <!-- Sensitive data exposure: Displaying full database contents without restriction -->
    <h2>Database Dump:</h2>
    <?php
    $dumpResult = $conn->query("SELECT * FROM users");
    while ($dumpRow = $dumpResult->fetch_assoc()) {
        echo "User: {$dumpRow['firstname']} {$dumpRow['lastname']}, School: {$dumpRow['school']}<br>";
    }
    ?>

    <a href="index.php">Go Back</a>
</body>
</html>

     ```

3. **Reflection**:
   - Discuss how front-end technologies interact to create a cohesive user experience. What potential security issues arise from poorly implemented front-end code (e.g., XSS, CSRF)?

---

#### **Exercise 2: Understanding Back-End Development Components**

1. **Identify Back-End Technologies**:
   - Create a list of common back-end technologies, including:
     - Server-side programming languages (e.g., PHP, Python, Java, Node.js)
     - Databases (e.g., MySQL, MongoDB, PostgreSQL)
     - Web frameworks (e.g., Express, Django, Laravel)

2. **Create a Simple Back-End Application**:
   - Using a chosen back-end technology, set up a basic server that responds to HTTP requests. For example, using Node.js:
   - **Example Code Snippet**:
     ```javascript
     const express = require('express');
     const app = express();
     const PORT = 3000;

     app.get('/', (req, res) => {
         res.send('Welcome to the Back-End Application!');
     });

     app.listen(PORT, () => {
         console.log(`Server is running on http://localhost:${PORT}`);
     });
     ```

3. **Reflection**:
   - Analyze the role of back-end components in web applications. How do vulnerabilities in the back-end (e.g., SQL injection, insecure APIs) affect overall application security?

---

#### **Exercise 3: Identifying Security Threats**

1. **Research Common Security Threats**:
   - Investigate the OWASP Top Ten list and identify at least five common security threats in web development. Focus on:
     - SQL Injection
     - Cross-Site Scripting (XSS)
     - Cross-Site Request Forgery (CSRF)
     - Security Misconfiguration
     - Insecure Deserialization

2. **Analyze a Sample Application**:
   - Use a vulnerable web application (e.g., DVWA or OWASP Juice Shop) to test for identified vulnerabilities.
   - Perform the following tasks:
     - Attempt an SQL injection attack using a login form.
     - Test for XSS by injecting scripts into input fields.
     - Check for CSRF by submitting a request to change user data without authentication.

3. **Reflection**:
   - Discuss the impact of these security threats on user data and application integrity. What measures can developers implement to mitigate these risks?

---

### **Report Submission**
At the end of this lab, you are required to submit a detailed report summarizing your findings and reflections from each exercise. Your report should include:

- An overview of front-end and back-end development components.
- Identification and analysis of common security threats in web applications.
- Reflections from each exercise, highlighting key observations and lessons learned.
- Screenshots or code snippets where applicable to support your findings.
- Recommendations for secure coding practices in web development.

**Submission Format**: Submit your report as a PDF file. Ensure that it is well-structured and addresses each part of the lab.

---

### **Conclusion**
In this lab, you explored the fundamental components of web development and identified common security threats associated with these components. Understanding these aspects is essential for building secure web applications.


