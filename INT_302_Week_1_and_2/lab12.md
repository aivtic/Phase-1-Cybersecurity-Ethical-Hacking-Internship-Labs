
## **INT302: Kali Linux Tools and System Security – Lab 12: John the Ripper**

### **Lab Overview**
In this lab, you will gain hands-on experience with **John the Ripper**, a powerful password-cracking tool. This lab will cover the practical use of John the Ripper for cracking password hashes in different formats. By simulating real-world password attacks, you will understand how to audit passwords and strengthen your security knowledge.

---

### **Lab Objectives**
By the end of this lab, students will:
1. Understand how to use **John the Ripper** to crack password hashes.
2. Learn about various password hash formats and modes supported by John the Ripper.
3. Perform password cracking exercises using **different attack techniques**, including dictionary and brute force attacks.
4. Analyze the success of these techniques and understand password complexities.

---

### **Tools Used**
- **John the Ripper**: A powerful password-cracking tool.
- **Wordlists**: Common password files for dictionary attacks.
- **Hashcat**: Can be introduced for comparison with John the Ripper, though focus will remain on John the Ripper.

---

### **Prerequisites**
- Basic knowledge of **Linux commands**.
- Familiarity with **cryptography** and **password hashing**.

---

### **Lab Steps**

#### **Step 1: Installing John the Ripper**

1. **Ensure John the Ripper is Installed**:
   - In Kali Linux, John the Ripper comes pre-installed, but if not:
     ```bash
     sudo apt install john
     ```

2. **Check the Version**:
   - Verify the installation by checking the version:
     ```bash
     john --version
     ```

**Exercise 1**:  
- What version of John the Ripper are you using? __________

---

#### **Step 2: Understanding Password Hashes**

1. **Identify Hash Types**:
   - Before cracking passwords, identify the hash type. For example, you can check hash examples here:
     ```bash
     cat /etc/shadow
     ```
   - Observe the hashed passwords in the `/etc/shadow` file.

2. **Popular Hash Formats**:
   - MD5, SHA-1, and DES are common formats that John can handle.

**Exercise 2**:  
- Using John the Ripper, how do you identify the type of a given hash? Run the following command on sample hashes:
     ```bash
     john --format=raw-md5 <hashfile>
     ```

---

#### **Step 3: Cracking Passwords with Wordlists**

1. **Using Default Wordlist**:
   - Use the default wordlist (`rockyou.txt`) to attempt cracking a simple MD5 hash:
     ```bash
     john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
     ```

**Exercise 3**:  
- Download a sample hash and crack it using the wordlist. What was the password? Was it successful? __________

2. **Adding Custom Wordlists**:
   - Create a custom wordlist file with possible passwords:
     ```bash
     echo -e "password1\nletmein\nadmin123" > custom_wordlist.txt
     ```

**Exercise 4**:  
- Run John with your custom wordlist on a given hash. Was your list successful in cracking the hash? __________

---

#### **Step 4: Brute Force Mode**

1. **Understanding Brute Force**:
   - If the wordlist attack fails, you can switch to brute force mode:
     ```bash
     john --incremental hash.txt
     ```

2. **Time and Complexity**:
   - Brute force takes longer but tries every possible combination.

**Exercise 5**:  
- Perform a brute force attack on a hash. How long did the attack take, and was it successful? __________

---

#### **Step 5: Cracking Windows Password Hashes**

1. **Dumping Windows Hashes**:
   - Extract password hashes from a Windows machine using tools like `pwdump` or `hashdump`.
   - Example hash (LM or NTLM):
     ```
     john --format=nt hashfile
     ```

**Exercise 6**:  
- Attempt cracking NTLM hashes using the `rockyou.txt` wordlist. Were you successful? How complex was the password? __________

---

#### **Step 6: Advanced Cracking with Rules**

1. **Adding Rules for More Power**:
   - John the Ripper allows you to create rules that modify the wordlist:
     ```bash
     john --wordlist=rockyou.txt --rules --format=raw-md5 hash.txt
     ```

**Exercise 7**:  
- Use rules with a wordlist attack to crack a complex password. What was the result? __________

---

### **Analysis and Conclusion**

- Discuss the **success rates** of different cracking techniques and the **importance of strong passwords**.
- Highlight why **password length**, **complexity**, and **use of salts** are essential to improving security.

---

### **Additional Exercises**

1. **Create Custom Hashes**:  
   - Create a custom hash (MD5 or SHA-256) using Python:
     ```python
     import hashlib
     print(hashlib.md5(b'password').hexdigest())
     ```
   - Try cracking it using John.

2. **Benchmark Performance**:  
   - Run a benchmark test to see how fast John can run on your machine:
     ```bash
     john --test
     ```

3. **Compare with Hashcat**:  
   - (Optional) Install **Hashcat** and compare its performance with John the Ripper for similar tasks.

---

### **Conclusion**
In this lab, you have explored the power of John the Ripper for cracking passwords and learned various techniques to improve your penetration testing skills. Continue to experiment with different hash types and explore password-cracking techniques.

---

