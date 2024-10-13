

## **INT308: Session Management and Web Security – Lab 2: Secure Session Management Practices**

### **Overview**
In this lab, you will explore secure session management practices, focusing on how to implement and enforce security measures to protect session data from common vulnerabilities. You will learn best practices for creating and maintaining secure sessions in web applications.

### **Prerequisites**
- Familiarity with web application security concepts.
- Ensure you have access to a web application environment (e.g., DVWA) for testing.
- Basic understanding of PHP and session management.

### **Lab Objectives**
- Identify and implement secure session management techniques.
- Understand the importance of session expiration and invalidation.
- Learn to secure session data against common attacks.

---

### **Exercise 1: Configuring Secure Session Cookies**

1. **Access the Target Application**:
   - Open DVWA (Damn Vulnerable Web Application) in your browser.
   - Log in to the application (use the credentials: admin / password).

2. **Review Current Cookie Settings**:
   - Inspect the session cookie using the browser's developer tools.
   - In Chrome, right-click on the page > Inspect > Application tab > Cookies > [Your Site].
   - Take note of the current attributes of the session cookie.

3. **Modify Server-Side Configuration**:
   - If you have access to the server-side code, open the `config.php` file in your DVWA installation directory (or any file where session handling is configured).
   - Modify the session cookie settings to include security attributes:
   - **PHP Code Example**:
     ```php
     <?php
     // Start the session
     session_start();

     // Set secure cookie parameters
     session_set_cookie_params([
         'lifetime' => 0, // Session cookie
         'path' => '/',
         'domain' => 'yourdomain.com', // Change to your domain
         'secure' => true, // Use only over HTTPS
         'httponly' => true, // Accessible only through HTTP protocol
         'samesite' => 'Strict', // Prevents CSRF attacks
     ]);

     // Regenerate session ID to prevent fixation
     session_regenerate_id(true);
     ?>
     ```

4. **Reflection**:
   - Discuss the impact of these changes on session security. How do they mitigate common vulnerabilities?

---

### **Exercise 2: Implementing Session Expiration and Invalidation**

1. **Understand Session Expiration**:
   - Review how session expiration works and its importance in session management.

2. **Set Session Lifetime**:
   - In the same `config.php` file, configure the session timeout to a reasonable period (e.g., 15 minutes of inactivity).
   - **PHP Code Example**:
     ```php
     <?php
     // Set session garbage collection max lifetime
     ini_set('session.gc_maxlifetime', 900); // 15 minutes

     // Check if the session has expired
     if (isset($_SESSION['LAST_ACTIVITY']) && (time() - $_SESSION['LAST_ACTIVITY'] > 900)) {
         // Last request was more than 15 minutes ago
         session_unset(); // Unset $_SESSION variables
         session_destroy(); // Destroy the session
         header("Location: logout.php"); // Redirect to logout page
     }
     $_SESSION['LAST_ACTIVITY'] = time(); // Update last activity time stamp
     ?>
     ```

3. **Force Logout on Expiration**:
   - Create a simple logout page (`logout.php`) to handle session termination:
   - **logout.php Example**:
     ```php
     <?php
     session_start();
     session_unset(); // Unset session variables
     session_destroy(); // Destroy the session
     header("Location: index.php"); // Redirect to login page
     exit();
     ?>
     ```

4. **Reflection**:
   - Discuss how session expiration contributes to overall application security. What challenges might arise from enforcing session expiration?

---

### **Exercise 3: Testing Session Management Controls**

1. **Simulate an Attack**:
   - Use a second browser or incognito mode to access the application after the session has expired.
   - Log in to the application and wait for 15 minutes without any activity.
   - Try to access a protected page (e.g., your dashboard).

2. **Evaluate Security Measures**:
   - Monitor the application's response to these attempts. Does it deny access appropriately?
   - Check if you are redirected to the logout page after session expiration.

3. **Reflection**:
   - Discuss the effectiveness of the session management controls in place. What additional measures could be implemented to strengthen security?

---

### **Conclusion**
In this lab, you learned about secure session management practices, including the configuration of secure session cookies, session expiration, and invalidation techniques. Implementing these practices is essential for protecting user sessions and ensuring the security of web applications.

### **Next Steps**
- Prepare for the next lab, which will focus on **Cross-Site Request Forgery (CSRF) Protection** within session management frameworks.

---

### **Additional Exercises**
1. **Implement Session Regeneration**: 
   - Modify your existing code to regenerate session IDs at specific intervals or on certain events (e.g., after a successful login).
   - Discuss how this practice enhances security.

2. **Test for Session Fixation**:
   - Attempt a session fixation attack by manually setting a session ID before logging in and observe the application's response.

3. **Evaluate Cookie Security**:
   - Test your application with various cookie settings. What are the implications of each setting on security?

---

### **Report Submission**
At the end of the lab, please submit a report that includes the following:

1. **Title Page**: Include your name, course, lab title, and date.
2. **Lab Overview**: Briefly describe the objectives of the lab.
3. **Exercise Summaries**: Provide a summary of each exercise, including key findings, code snippets used, and reflections.
4. **Discussion**: Discuss the importance of secure session management practices and the potential impact of vulnerabilities.
5. **Recommendations**: Suggest additional security measures that could enhance session management.

### **Submission Guidelines**
- Submit your report as a PDF or Word document.
- Ensure your report is well-organized and free of grammatical errors.
- Submit your report to the designated submission portal by the due date.
