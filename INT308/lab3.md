

## **INT308: Session Management and Web Security – Lab 3: Cross-Site Request Forgery (CSRF) Protection**

### **Overview**
In this lab, you will learn about Cross-Site Request Forgery (CSRF) attacks and how to implement protection mechanisms to safeguard web applications. You will explore how CSRF attacks exploit the trust that a web application has in the user's browser.

### **Prerequisites**
- Basic knowledge of web application security concepts.
- Familiarity with session management and HTTP requests.
- Access to a web application environment (e.g., DVWA) for testing.

### **Lab Objectives**
- Understand how CSRF attacks work and their impact on web applications.
- Implement CSRF protection using tokens.
- Test the effectiveness of CSRF defenses.

---

### **Exercise 1: Understanding CSRF Attacks**

1. **Explore DVWA**:
   - Open DVWA in your browser and log in with your credentials (admin/password).
   - Navigate to the **CSRF** section of the application.

2. **Simulate a CSRF Attack**:
   - Open a new browser tab or window and create a simple HTML form to simulate a CSRF attack.
   - **Attack Form Example**:
     ```html
     <!DOCTYPE html>
     <html lang="en">
     <head>
         <meta charset="UTF-8">
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>CSRF Attack</title>
     </head>
     <body>
         <form action="http://your-dvwa-url/vulnerabilities/csrf/" method="POST">
             <input type="hidden" name="id" value="2">
             <input type="submit" value="Click me to attack!">
         </form>
     </body>
     </html>
     ```

   - Replace `http://your-dvwa-url` with your actual DVWA URL.
   - Open this HTML file in your browser and click the submit button after logging into DVWA.

3. **Evaluate the Attack**:
   - Observe the outcome of the attack. Did it successfully change the user settings or execute a sensitive action?
   - Discuss how this demonstrates the importance of CSRF protection.

---

### **Exercise 2: Implementing CSRF Protection**

1. **Modify the Application Code**:
   - In your DVWA environment, navigate to the CSRF protection implementation area. If you don’t have one, you can add a CSRF token to forms manually.
   - **PHP Code Example** for generating and validating CSRF tokens:
     ```php
     <?php
     session_start();

     // Generate a CSRF token
     if (empty($_SESSION['csrf_token'])) {
         $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
     }

     // Include CSRF token in forms
     ?>
     <form action="http://your-dvwa-url/vulnerabilities/csrf/" method="POST">
         <input type="hidden" name="id" value="2">
         <input type="hidden" name="csrf_token" value="<?php echo $_SESSION['csrf_token']; ?>">
         <input type="submit" value="Submit">
     </form>
     ```

2. **Validate CSRF Tokens**:
   - Add validation logic to check the CSRF token upon form submission:
   - **PHP Code Example**:
     ```php
     <?php
     session_start();

     // Validate the CSRF token
     if ($_SERVER['REQUEST_METHOD'] === 'POST') {
         if (!hash_equals($_SESSION['csrf_token'], $_POST['csrf_token'])) {
             die("CSRF token validation failed!");
         }
         // Proceed with the request processing
     }
     ?>
     ```

3. **Reflection**:
   - Discuss how CSRF tokens work to prevent unauthorized actions. What other security measures could complement this?

---

### **Exercise 3: Testing CSRF Protection**

1. **Test the Protection**:
   - Open your attack form again but remove the CSRF token field from it.
   - Submit the form to see if the action is allowed without the valid token.

2. **Analyze the Response**:
   - Confirm that the action is denied or fails without the correct CSRF token.
   - Document the results and evaluate how effectively the CSRF protection mechanism worked.

3. **Reflection**:
   - Discuss potential limitations of the CSRF token approach. How might attackers bypass these protections, and what additional strategies could be employed?

---

### **Conclusion**
In this lab, you explored Cross-Site Request Forgery (CSRF) attacks and implemented protection mechanisms using CSRF tokens. Understanding how to defend against CSRF is crucial for maintaining secure web applications.

### **Next Steps**
- Prepare for future labs focusing on additional web security topics, such as **Cross-Site Scripting (XSS)** and **input validation**.

---

### **Report Submission**
- Prepare a report summarizing your findings from the lab exercises. Include the following sections:
  - **Introduction**: Brief overview of CSRF and its implications.
  - **Exercise Summaries**: Details of each exercise, including what was learned and results obtained.
  - **Reflections**: Your thoughts on the effectiveness of CSRF protections and any additional measures you believe could enhance security.
  - **Conclusion**: Summarize the importance of CSRF protection in web applications.
- Submit your report in PDF format via the designated submission portal.

---

### **Additional Exercises (Optional)**
1. **Implement SameSite Cookie Attribute**:
   - Modify the cookie settings to include the `SameSite` attribute to further protect against CSRF attacks. Discuss its implications.
   
2. **Create a Logging Mechanism**:
   - Implement a logging mechanism to track CSRF validation failures and analyze trends over time.

3. **Review Application Code**:
   - Review the entire application code for potential CSRF vulnerabilities and propose solutions for each identified issue.

