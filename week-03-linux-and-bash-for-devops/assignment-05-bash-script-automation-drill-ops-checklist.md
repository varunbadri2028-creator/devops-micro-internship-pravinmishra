# Assignment 5 — Bash Script Automation Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will practice Bash scripting by building a series of small automation scripts covering environment setup, variables, arrays, loops, file conditionals, if-else logic, and functions. These scripts form the foundation of real-world Linux automation used in DevOps, cloud, and production support environments.

---

# Task 1 — Bash Environment & Workspace Setup

## Goal

Verify that Bash is available on your system and create a clean workspace for this assignment.

### Evidence

#### Screenshot 1 — Output of `echo $SHELL` and `bash --version`

<img width="932" height="177" alt="Screenshot 2026-10-08 185451" src="https://github.com/user-attachments/assets/14b7606e-ca01-4a6e-85cc-2af27aa7cd7d" />


#### Screenshot 2 — Output of `pwd` and `ls -lah` showing the scripts directory

<img width="706" height="238" alt="Screenshot 2026-10-08 185622" src="https://github.com/user-attachments/assets/fc65ab6d-6071-4589-a270-1431695ce0e3" />


### Notes

Answer the following in your own words:

**1. What is Bash?**

Bash is a command-line shell used in Linux systems. It allows us to run commands and create scripts to automate different tasks.

**2. What is the difference between shell and Bash?**

A shell is a program that provides an interface to interact with the operating system. Bash is one specific type of shell. Other shells include Zsh and Fish.

**3. Why is it important to confirm the Bash version before writing scripts?**

Different Bash versions may support different features and syntax. Checking the version helps make sure the script works correctly in the environment where it will be executed.

# Task 2 — Your First Bash Script

## Goal

Create your first Bash script, make it executable, and run it from the terminal.

### Evidence

#### Screenshot 1 — Content of `first-script.sh`

<img width="945" height="168" alt="Screenshot 2026-10-08 190214" src="https://github.com/user-attachments/assets/e84b553c-0ed9-47e8-b4f2-ed94b3815825" />


#### Screenshot 2 — Output of `./first-script.sh`

<img width="928" height="160" alt="Screenshot 2026-10-08 190535" src="https://github.com/user-attachments/assets/3769ba46-5183-44c6-912b-a8f804ebebe3" />


#### Screenshot 3 — Output of `ls -l first-script.sh` showing executable permission

<img width="912" height="127" alt="Screenshot 2026-10-08 231533" src="https://github.com/user-attachments/assets/928df9fa-dcdb-4f0f-93d7-0cd57078d73e" />


### Notes

Answer the following in your own words:

**1. What is the purpose of `#!/bin/bash`?**

#!/bin/bash tells the system to run the script using the Bash shell. It is called the shebang line.

**2. Why do we use `chmod +x` before running a script?**

chmod +x gives the script execute permission. This allows us to run it directly using ./script.sh.

**3. What is the difference between running a script using `./script.sh` and `bash script.sh`?**

./script.sh runs the script directly and requires execute permission. bash script.sh runs the script through Bash directly, so the execute permission is not required.

# Task 3 — Variables: User Information Script

## Goal

Use variables to store and display user-related information.

### Evidence

#### Screenshot 1 — Content of `user-info.sh`

<img width="940" height="335" alt="Screenshot 2026-10-08 231930" src="https://github.com/user-attachments/assets/db2ca348-8192-481c-9aa4-0f9bae122e17" />


#### Screenshot 2 — Output of `./user-info.sh`

<img width="920" height="162" alt="Screenshot 2026-10-08 232035" src="https://github.com/user-attachments/assets/2fa8cc18-511a-4eb6-9f8b-21c5e8ec5cca" />


### Notes

Answer the following in your own words:

**1. What is a variable in Bash?**

A variable in Bash is used to store a value, such as a name, number, or text, so it can be used later in the script.

**2. Why should we avoid spaces around the `=` sign when creating variables?**

Bash does not allow spaces around = when assigning a value. For example, name="Varun" is correct, while name = "Varun" is treated as a command and causes an error.

**3. How do you access the value stored inside a Bash variable?**

We use the $ symbol followed by the variable name. For example, if name="B. Varun Kumar", we use $name to access its value.

# Task 4 — Arrays & Loops: Tools Checklist Script

## Goal

Use arrays and loops to print a checklist of tools used in Bash scripting.

### Evidence

#### Screenshot 1 — Content of `tools-checklist.sh`

<img width="922" height="372" alt="Screenshot 2026-10-08 232338" src="https://github.com/user-attachments/assets/55a98045-eb23-4e8a-ab39-6b369d112ff1" />


#### Screenshot 2 — Output of `./tools-checklist.sh`

<img width="925" height="263" alt="Screenshot 2026-10-08 232452" src="https://github.com/user-attachments/assets/d4a8a8fc-3e76-4c8a-8079-d76dc177b167" />


### Notes

Answer the following in your own words:

**1. What is an array in Bash?**

An array in Bash is a variable that can store multiple values under one variable name.

**2. Why are arrays useful in scripts?**

Arrays are useful when we need to store and process a list of related values. They make it easier to work with multiple items using loops.

**3. What does `"${tools[@]}"` mean?**

"${tools[@]}" refers to all the values stored in the tools array. It allows the for loop to process each tool separately.

**4. What is the purpose of the `for` loop in this script?**

The for loop goes through each tool stored in the tools array and prints them one by one as part of the checklist.

# Task 5 — Loops: Number Counter Script

## Goal

Use loops to repeat a task multiple times.

### Evidence

#### Screenshot 1 — Content of `counter.sh`

<img width="903" height="302" alt="Screenshot 2026-10-08 232934" src="https://github.com/user-attachments/assets/507e2c16-235c-484f-84f9-d03e1591b63e" />


#### Screenshot 2 — Output of `./counter.sh`

<img width="883" height="242" alt="Screenshot 2026-10-08 233026" src="https://github.com/user-attachments/assets/3bd96154-32f5-4e98-88c7-fdd79019900d" />


### Notes

Answer the following in your own words:

**1. What is a loop?**

A loop is a programming structure that repeats a set of commands multiple times.

**2. Why do we use loops in Bash scripting?**

We use loops to repeat tasks automatically without writing the same commands again and again. This makes scripts shorter and easier to manage.

**3. How many times did the loop run in your script?**

The loop ran 5 times, counting from 1 to 5.

**4. What would you change if you wanted the loop to run 10 times?**

I would change {1..5} to {1..10} in the for loop.

# Task 6 — Files & Conditionals: File Validation Script

## Goal

Use file checks and conditionals to verify whether files and directories exist.

### Evidence

#### Screenshot 1 — Output of `ls -lah ../test-folder`

<img width="930" height="167" alt="Screenshot 2026-10-08 233811" src="https://github.com/user-attachments/assets/ce7f1ff6-1cae-4eee-a8f1-66557f6bdd27" />


#### Screenshot 2 — Content of `file-check.sh`

<img width="922" height="491" alt="Screenshot 2026-10-08 234022" src="https://github.com/user-attachments/assets/5d591da4-0c3f-401e-b36a-f9454490054e" />


#### Screenshot 3 — Output of `./file-check.sh`

<img width="917" height="120" alt="Screenshot 2026-10-08 234134" src="https://github.com/user-attachments/assets/6a03a84d-e1bb-42f2-b2e1-411f3a147605" />

### Notes

Answer the following in your own words:

**1. What does `-d` check in Bash?**

-d checks whether the given path exists and is a directory.

**2. What does `-f` check in Bash?**

-f checks whether the given path exists and is a regular file.

**3. Why should file and directory paths be stored in variables?**

Storing paths in variables makes the script easier to read, reuse, and modify, and avoids repeating the same path multiple times.

**4. What happens if the file does not exist?**

The -f condition becomes false, so the else block runs and displays that the file does not exist.

# Task 7 — Conditionals: Pass or Retry Script

## Goal

Use if-else conditionals to make decisions based on a variable value.

### Evidence

#### Screenshot 1 — Content of `score-check.sh` with `score=85`

<img width="922" height="352" alt="Screenshot 2026-10-08 234455" src="https://github.com/user-attachments/assets/c14fa8b7-7aec-4625-8d93-2325f10586b8" />


#### Screenshot 2 — Output showing `Result: Pass`

<img width="917" height="118" alt="Screenshot 2026-10-08 234548" src="https://github.com/user-attachments/assets/f626f11d-ec5f-49ca-9ab0-458a392e9914" />


#### Screenshot 3 — Content of `score-check.sh` with `score=55`

<img width="911" height="333" alt="Screenshot 2026-10-08 234702" src="https://github.com/user-attachments/assets/af389421-2f9b-4047-a2c6-1962ee7e1ef8" />


#### Screenshot 4 — Output showing `Result: Retry`

<img width="922" height="122" alt="Screenshot 2026-10-08 234748" src="https://github.com/user-attachments/assets/220ae699-a19a-46ed-ae1c-eaf67f528d22" />


### Notes

Answer the following in your own words:

**1. What is the purpose of if-else in Bash?**

if-else is used to make decisions in a Bash script based on whether a condition is true or false.

**2. What does `-ge` mean?**

-ge means greater than or equal to.

**3. Why should conditions be tested with different values?**

Testing different values helps verify that the script works correctly for different situations, such as both Pass and Retry cases.

**4. How can conditionals help in automation scripts?**

Conditionals allow scripts to make decisions automatically and perform different actions depending on the situation.

# Task 8 — Functions: Final Bash Automation Script

## Goal

Create a final Bash script using functions to organize reusable code.

### Evidence

#### Screenshot 1 — Content of `final-automation.sh`

<img width="931" height="1012" alt="Screenshot 2026-10-08 235255" src="https://github.com/user-attachments/assets/83e65a72-e90a-40b1-b19a-4b445d4597fe" />


#### Screenshot 2 — Output of `./final-automation.sh`

<img width="923" height="283" alt="Screenshot 2026-10-08 235351" src="https://github.com/user-attachments/assets/75e2d85d-b62c-4888-a770-1ec3077386ba" />


#### Screenshot 3 — Output of `ls -lah` showing all created scripts

<img width="890" height="288" alt="Screenshot 2026-10-08 235458" src="https://github.com/user-attachments/assets/d42527c7-bc12-4c78-aa3d-1ba91df0bddf" />


### Notes

Answer the following in your own words:

**1. What is a function in Bash?**

A function is a reusable block of commands that performs a specific task in a Bash script.

**2. Why are functions useful in scripts?**

Functions make scripts organized, reusable, and easier to read. They also avoid repeating the same commands.

**3. Which functions did you create in this script?**

I created four functions:

show_info() — displays user and internship information.
show_tools() — displays the list of DevOps tools using a loop.
check_files() — checks whether the directory and file exist.
check_score() — checks the score and displays Pass or Retry

**4. How does this final script combine variables, arrays, loops, conditionals, files, and functions?**

The script uses variables for information like the name and score, an array to store tools, a loop to display each tool, conditionals to check files and the score, and functions to organize all these tasks into separate reusable sections.

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dj5njznW

#### Screenshot — Published LinkedIn post

<img width="1632" height="840" alt="Screenshot 2026-10-08 235932" src="https://github.com/user-attachments/assets/3495c930-131a-4649-b8ff-12662b0d253e" />


# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- All script files must be created and run successfully
- Required notes must be answered clearly for every task
- Do not expose sensitive information (keys, passwords, credentials)

---

# Completion Checklist

- [ ] Task 1: Environment setup verified, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: First script created, executed, permissions verified (Screenshots 1–3, Notes answered)
- [ ] Task 3: Variables script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 4: Arrays and loops script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 5: Counter loop script created and run (Screenshots 1–2, Notes answered)
- [ ] Task 6: File validation script created and run (Screenshots 1–3, Notes answered)
- [ ] Task 7: Pass/Retry conditional script tested with both values (Screenshots 1–4, Notes answered)
- [ ] Task 8: Final automation script created and run (Screenshots 1–3, Notes answered)
- [ ] All scripts run without errors
- [ ] Full Name visible in all required screenshots
- [ ] LinkedIn post published and URL submitted
- [ ] No sensitive data exposed

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://dmi.pravinmishra.com?utm_source=github&utm_medium=readme  
- 🎓 University: https://university.pravinmishra.com?utm_source=github&utm_medium=readme  
- 💬 Discord Community: https://discord.pravinmishra.com?utm_source=github&utm_medium=readme  
- 📝 Blog: https://dmi.pravinmishra.com/blog?utm_source=github&utm_medium=readme  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
