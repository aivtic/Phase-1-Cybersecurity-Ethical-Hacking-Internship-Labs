Here's a comprehensive lab for **Week 2: Introduction to Bash Scripting**. This lab covers essential bash scripting concepts and provides exercises to reinforce the learning. It can be adapted for beginners to intermediate learners.

---

# Week 2: Introduction to Bash Scripting

## Lab Overview
In this lab, students will learn how to write simple bash scripts and execute them in the Linux shell. By the end of the lab, students should be able to create and run scripts that automate tasks, handle user inputs, and perform basic operations.

### Learning Objectives:
1. Understand the basics of bash scripting syntax.
2. Create and run bash scripts.
3. Work with variables, conditionals, and loops.
4. Take user input in bash scripts.
5. Perform basic file operations using bash scripts.

---

## Part 1: Bash Scripting Basics

### 1.1 What is a Bash Script?
Bash scripting is a way to automate tasks in a Linux environment using commands that are written in the shell scripting language. Bash (Bourne Again Shell) is one of the most popular shells used in Linux.

### 1.2 Creating a Simple Script
Let's start by creating a simple script to display text.

1. Open your terminal.
2. Create a new file with a `.sh` extension:
   ```bash
   nano hello.sh
   ```
3. Inside the file, write the following lines:
   ```bash
   #!/bin/bash
   # This is a comment explaining the purpose of the script

   echo "Hello, World!"
   ```
   The `#!/bin/bash` at the beginning is called a **shebang**. It tells the system to execute the script with the bash interpreter.

4. Save the file and exit the text editor (`CTRL+X`, then press `Y` to confirm).

5. To run the script, make it executable:
   ```bash
   chmod +x hello.sh
   ```

6. Now, execute the script:
   ```bash
   ./hello.sh
   ```

### 1.3 Adding Variables
In bash scripting, variables can store data and be used later in the script.

1. Modify `hello.sh` to include a variable:
   ```bash
   #!/bin/bash
   name="Aminu"
   echo "Hello, $name!"
   ```

2. Run the script again to see the output.

---

## Part 2: Working with Variables, Conditionals, and Loops

### 2.1 Using Variables
In bash, variables don't need to be declared with a type. You simply assign values to them.

Example:
```bash
#!/bin/bash
greeting="Good Morning!"
echo $greeting
```

### 2.2 Conditionals
You can use `if-else` statements to control the flow of your script based on conditions.

Example:
```bash
#!/bin/bash
read -p "Enter your age: " age

if [ $age -ge 18 ]; then
    echo "You are an adult."
else
    echo "You are a minor."
fi
```

### 2.3 Loops
Bash scripting supports both `for` and `while` loops.

Example of a `for` loop:
```bash
#!/bin/bash
for i in {1..5}; do
    echo "Iteration $i"
done
```

Example of a `while` loop:
```bash
#!/bin/bash
count=1
while [ $count -le 5 ]; do
    echo "Loop $count"
    ((count++))
done
```

---

## Part 3: Working with User Input

### 3.1 Reading User Input
Bash scripts can interact with the user by accepting input using the `read` command.

Example:
```bash
#!/bin/bash
read -p "What is your name? " name
echo "Hello, $name!"
```

### 3.2 Command-Line Arguments
Scripts can also accept arguments when they are run.

Example:
```bash
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
```
Run it as:
```bash
./script.sh arg1 arg2
```

---

## Part 4: File Operations in Bash

### 4.1 Checking if a File Exists
You can check if a file exists using conditionals.

Example:
```bash
#!/bin/bash
file="sample.txt"

if [ -e $file ]; then
    echo "$file exists."
else
    echo "$file does not exist."
fi
```

### 4.2 Writing to a File
You can redirect output to a file.

Example:
```bash
#!/bin/bash
echo "This is some text." > output.txt
```

---

## Part 5: Exercises

### Exercise 1: Create a Script that Greets the User
Write a bash script that:
1. Prompts the user for their name.
2. Outputs a greeting that includes their name.

### Exercise 2: Simple Calculator
Write a script that:
1. Prompts the user for two numbers.
2. Prompts the user to choose an operation (addition, subtraction, multiplication, or division).
3. Performs the selected operation on the two numbers and displays the result.

### Exercise 3: File Checker
Write a script that:
1. Prompts the user to enter the name of a file.
2. Checks if the file exists.
3. If the file exists, display its size. If not, prompt the user to create the file.

### Exercise 4: Loop through a List of Names
Write a script that:
1. Stores a list of names in a variable (e.g., `names=("Alice" "Bob" "Charlie")`).
2. Loops through the names and prints a greeting for each one.

---

## Part 6: Conclusion

In this lab, you've learned the basics of bash scripting, including variables, conditionals, loops, and file operations. Bash scripting is a powerful tool for automating tasks and managing systems, and these exercises are just the beginning. Continue practicing by adding more complexity to your scripts!

---

