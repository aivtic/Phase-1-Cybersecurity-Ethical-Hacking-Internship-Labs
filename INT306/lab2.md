

### **INT306: Cryptography – Lab 2: Exploring Hash Functions**

---

#### **Overview**
Hash functions are crucial components in cryptography, providing integrity and authentication. They convert input data (of any size) into a fixed-length output (hash) that represents the original data. This lab will cover the fundamentals of hash functions, their properties, and practical exercises to solidify your understanding.

---

### **Understanding Hash Functions**

**Definition:** A hash function takes an input and returns a fixed-size string of bytes. The output, called a hash value or digest, uniquely represents the data.

**Key Properties:**
1. **Deterministic:** The same input will always produce the same output.
2. **Fast computation:** Hash values should be quick to compute.
3. **Pre-image resistance:** It should be difficult to reverse-engineer the original input from its hash value.
4. **Small changes affect output:** A tiny change in the input should produce a drastically different hash.
5. **Collision resistance:** It should be challenging to find two different inputs that produce the same hash output.

**Common Hash Functions:**
- **MD5:** Produces a 128-bit hash value, often represented as a 32-character hexadecimal number. (Note: Not recommended for security purposes)
- **SHA-1:** Produces a 160-bit hash value.
- **SHA-256:** Part of the SHA-2 family, produces a 256-bit hash value.

---

### **Hash Function Examples**

#### **Example 1: MD5**
**Input:** “Hello World”  
**MD5 Hash:** `5eb63bbbe01eeed093cb22bb8f5ac6`  

#### **Example 2: SHA-256**
**Input:** “Cryptography Lab”  
**SHA-256 Hash:** `b0b84c2e9c5f1ec3e379ef4be8e12df02e9da8b4043ec8ff074e1c2c4205a05b`

---

### **Exercises**

#### **Exercise 1: Compute Hash Values**
Using an online hash generator or a programming tool, compute the hash values for the following strings:
1. “Cryptography”
2. “Hash Functions”
3. “INT306”

**Task:** Record the hash values for MD5 and SHA-256. Discuss the differences in the output length and characteristics.

---

#### **Exercise 2: Understanding Collisions**
Research and describe a known collision attack on hash functions, such as the one found in MD5 or SHA-1.  
**Task:** Summarize the implications of this attack and how it affects data integrity.

---

#### **Exercise 3: Hash Function Properties**
Using a text editor, create a file with the following content:  
```
Lab 2: Exploring Hash Functions
Learning outcomes: Understand the importance of hash functions in cryptography.
```
**Task:** 
1. Save the file with a unique name.
2. Compute the SHA-256 hash of the file.
3. Modify a single character in the file and recompute the SHA-256 hash.  
**Question:** Discuss how the hash changes and why this property is significant.

---

#### **Exercise 4: Password Hashing**
Implement a simple password hashing mechanism using a programming language of your choice (e.g., Python, Java, etc.) to hash user passwords using SHA-256.  
**Task:**
1. Create a script that prompts for a password input and outputs the corresponding hash.
2. Discuss why it’s essential to hash passwords instead of storing them as plain text.

---

#### **Exercise 5: Rainbow Table Creation**
**Objective:** Create rainbow tables for common passwords and their hashes to understand the vulnerabilities in hash functions.

1. **Common Password List:** Gather a list of common passwords (e.g., "password", "123456", "qwerty", etc.) and their corresponding hashes using a chosen hash function (e.g., MD5 or SHA-256).
  
2. **Create Rainbow Tables:**
   - Write a script that generates hashes for the common passwords and stores them in a table format.
   - For example, your rainbow table could have columns like:
     - Password
     - MD5 Hash
     - SHA-256 Hash

3. **Using the Rainbow Table:**
   - Provide an example of how to use your rainbow table to crack a password hash. Take a hash generated from one of the common passwords and show how you can find the original password by checking your rainbow table.

**Discussion:** Reflect on the importance of using strong, unique passwords and the implications of using weak passwords in light of rainbow table attacks.

---

#### **Exercise 6: Real-World Application**
Choose an application that utilizes hash functions (e.g., cryptocurrency, digital signatures, or file integrity checks).  
**Task:** Write a one-page report detailing how hash functions are used in that application, including potential vulnerabilities and real-world implications.

---

#### **Exercise 7: Implementing a Hash Table**
As a supplementary exercise, implement a simple hash table in any programming language.  
**Task:** 
1. Define the basic operations (insert, search, delete).
2. Discuss how hash functions contribute to the efficiency of hash tables.

---

### **Conclusion**
Through this lab, students will gain hands-on experience with hash functions, understand their importance in securing data integrity, and explore real-world applications, including the creation of rainbow tables that highlight the vulnerabilities of common password hashes. This foundational knowledge will prepare students for more advanced topics in cryptography.

---

Feel free to adjust any part of this outline to better suit your course goals!