# Assignment 2 — Deploy a React App on Ubuntu VM Using Nginx

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will deploy a React application on an Ubuntu EC2 instance and serve it using Nginx. You will provision a Linux server, install the required tools, personalize the application with your details, and verify that it is publicly accessible via a browser.

---

# Task 1 — Setup Environment (Node.js & npm)

## Goal

Install Node.js and npm on the Ubuntu VM and verify the installation.

### Evidence

#### Screenshot 1 — Output of `node -v && npm -v` showing installed versions

<img width="518" height="136" alt="Screenshot 2026-10-06 213403" src="https://github.com/user-attachments/assets/73fe70ca-dbb5-4b6a-a7be-62411fc6a6b2" />


# Task 2 — Setup Environment (Nginx)

## Goal

Install Nginx, start the service, and confirm it is running.

### Evidence

#### Screenshot 2 — Output of `systemctl status nginx --no-pager` showing Active (running)

<img width="1920" height="1080" alt="Screenshot (207)" src="https://github.com/user-attachments/assets/1dcbd681-0de7-4b40-91f3-987a80cd2db9" />


# Task 3 — Clone React Application

## Goal

Clone the project repository and verify the project files are present.

### Evidence

#### Screenshot 3 — Output of `ls` inside the `my-react-app` directory showing project files

<img width="776" height="191" alt="Screenshot 2026-10-06 215724" src="https://github.com/user-attachments/assets/8b924998-6146-4c41-97c1-3e5c6bfba1f4" />

# Task 4 — Modify Application (Personalization)

## Goal

Update `App.js` with your full name and the current date.

### Evidence

#### Screenshot 4 — `nano App.js` open showing your full name and date filled in

<img width="861" height="117" alt="Screenshot 2026-10-06 220211" src="https://github.com/user-attachments/assets/83e0c168-1900-446a-93be-1a836b39de4c" />


# Task 5 — Build React Application

## Goal

Install dependencies and generate the production build.

### Evidence

#### Screenshot 5 — Output of `ls` inside `my-react-app` showing the `build/` folder generated

<img width="857" height="117" alt="Screenshot 2026-10-06 220452" src="https://github.com/user-attachments/assets/30363b20-8ef4-45c3-977a-08797f069043" />


# Task 6 — Deploy React Build to Nginx Web Root

## Goal

Copy the production build files to the Nginx web root directory.

### Evidence

#### Screenshot 6 — Output of `ls /var/www/html/` showing the deployed build contents

<img width="587" height="97" alt="Screenshot 2026-10-06 220645" src="https://github.com/user-attachments/assets/679c81a0-b359-45c5-8288-e4df0ca0821d" />


# Task 7 — Configure Nginx for React Application

## Goal

Apply Nginx configuration for React routing and confirm the service is active.

### Evidence

#### Screenshot 7 — Output of `systemctl is-active nginx` showing `active`

<img width="632" height="95" alt="Screenshot 2026-10-06 220822" src="https://github.com/user-attachments/assets/89f6632d-c561-4c94-9bb0-d4832bd39136" />


#### Screenshot 8 — Output of `cat /etc/nginx/sites-available/default` showing the Nginx config

<img width="925" height="1011" alt="Screenshot 2026-10-06 220927" src="https://github.com/user-attachments/assets/8d09d91a-07c3-4de7-a8b3-8f8f6b62bc67" />


# Task 8 — Test Deployment

## Goal

Verify the React application is publicly accessible via the server's public IP.

### Evidence

#### Screenshot 9 — Output of `curl ifconfig.me` showing the server's public IP address

<img width="525" height="50" alt="Screenshot 2026-10-06 221022" src="https://github.com/user-attachments/assets/efdac88d-1675-49a2-b041-6ad57a878728" />


#### Screenshot 10 — Browser showing the deployed React app at `http://<public-ip>` with your name and date visible

<img width="772" height="565" alt="Screenshot 2026-10-06 221208" src="https://github.com/user-attachments/assets/19124af2-9c47-443e-8e43-bea3edd99519" />


# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dgG7jz-e

#### Screenshot — LinkedIn post showing the deployed application

<img width="1920" height="1080" alt="Screenshot (208)" src="https://github.com/user-attachments/assets/d4c8e6ff-e92e-41b5-a077-7fc32f686678" />


# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [ ] Node.js and npm installed and verified (Screenshot 1)
- [ ] Nginx installed and running (Screenshot 2)
- [ ] Repository cloned and files verified (Screenshot 3)
- [ ] App.js updated with full name and date (Screenshot 4)
- [ ] Production build generated (Screenshot 5)
- [ ] Build files deployed to Nginx web root (Screenshot 6)
- [ ] Nginx configured and active (Screenshots 7 & 8)
- [ ] Public IP retrieved (Screenshot 9)
- [ ] React app accessible in browser with personal details visible (Screenshot 10)
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
