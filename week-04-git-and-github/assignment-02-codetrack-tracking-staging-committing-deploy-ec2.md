# Assignment 2 — CodeTrack: Tracking, Staging, Committing + Deploy to EC2

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will track and stage project files, create two meaningful Git commits in `CodeTrack`, verify your commit history, and deploy the CodeTrack static website to an EC2 instance using Nginx. This connects local version-control practice with a basic manual deployment workflow used in real DevOps environments.

---

# Task 1 — Verify Git Setup and Enter the Repository

## Goal

Confirm that Git works and that you are inside the correct `CodeTrack` repository.

### Evidence

#### Screenshot 1 — Output of `pwd` showing you're inside `CodeTrack`

<img width="269" height="110" alt="Screenshot 2026-10-15 at 10 35 28" src="https://github.com/user-attachments/assets/e9771dbf-9734-4e68-bc7c-257d564b8bf6" />


---

#### Screenshot 2 — Output of `git status` showing no "not a git repository" error
<img width="354" height="189" alt="Screenshot 2026-10-15 at 10 35 41" src="https://github.com/user-attachments/assets/3c341f81-f13e-42ba-b263-f07bb869e90f" />


---

# Task 2 — Create index.html and style.css

## Goal

Create the two starter UI files inside `CodeTrack`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `index.html` and `style.css`

<img width="341" height="46" alt="Screenshot 2026-10-15 at 10 37 33" src="https://github.com/user-attachments/assets/4655dd86-5bef-45fb-b4e1-009d1df7c33a" />


---

# Task 3 — Add Starter Content

## Goal

Copy the provided starter HTML and CSS content into your local `index.html` and `style.css` files.

### Evidence

#### Screenshot 4 — Your editor showing the contents of `index.html` and `style.css`
<img width="1012" height="756" alt="Screenshot 2026-10-15 at 10 42 30" src="https://github.com/user-attachments/assets/247ebe89-7547-4751-83d2-d9e6d89fb6a3" />


---

# Task 4 — Track and Stage Files Correctly

## Goal

Confirm both files show as untracked, then stage them individually with `git add`.

### Evidence

#### Screenshot 5 — Output of `git status` showing both files as untracked
<img width="579" height="225" alt="Screenshot 2026-10-15 at 10 46 27" src="https://github.com/user-attachments/assets/293ba430-2e47-494e-932f-2c8798947e76" />


---

#### Screenshot 6 — Output of `git status` showing both files staged under "Changes to be committed"
<img width="544" height="212" alt="Screenshot 2026-10-15 at 10 47 21" src="https://github.com/user-attachments/assets/abf12012-bf49-4b0c-b6e3-3b30b7b1fa89" />


---

# Task 5 — Create the First Commit (Clean Initial Commit)

## Goal

Commit the staged starter files using the message `Initial UI scaffold: add index.html and style.css`, then check the log.

### Evidence

#### Screenshot 7 — Output of `git commit`
<img width="608" height="146" alt="Screenshot 2026-10-15 at 10 49 18" src="https://github.com/user-attachments/assets/504f85bc-2234-44f3-aed1-0cb6c79e8f8d" />


---

#### Screenshot 8 — Output of `git log --oneline` showing the first commit
<img width="608" height="146" alt="Screenshot 2026-10-15 at 10 49 18" src="https://github.com/user-attachments/assets/c37ac1c5-e502-4394-8246-db50a55c55ef" />


---

# Task 6 — Modify index.html and Create a Second Commit

## Goal

Follow the instruction comment inside `index.html` to update the Student Name and Group Name, then commit that change separately using the message `Update homepage content: heading, tagline, CTA button`.

### Evidence

#### Screenshot 9 — Browser showing the updated page with your Student Name and Group Name visible

<img width="707" height="739" alt="Screenshot 2026-10-15 at 10 52 53" src="https://github.com/user-attachments/assets/c9edce71-fd39-4cf7-a3bf-1e96bf50c124" />


---

#### Screenshot 10 — Output of `git status` showing `index.html` as modified

<img width="547" height="162" alt="Screenshot 2026-10-15 at 10 54 14" src="https://github.com/user-attachments/assets/4a5ea8eb-2490-41f4-b5bb-e03fc25c8be4" />


---

#### Screenshot 11 — Output of `git commit`

<img width="612" height="115" alt="Screenshot 2026-10-15 at 10 56 00" src="https://github.com/user-attachments/assets/49c58bdd-3489-4efc-87b8-513d2ff5f3ff" />


---

#### Screenshot 12 — Output of `git log --oneline` showing two commits

<img width="574" height="195" alt="Screenshot 2026-10-15 at 10 56 20" src="https://github.com/user-attachments/assets/4b869884-f77c-4f90-95c4-45d19f168177" />


---

# Task 7 — Deploy to EC2 with Nginx (Static Website)

## Goal

Install and start Nginx on your EC2 instance, then copy `index.html` and `style.css` into the Nginx web root.

### Evidence

#### Screenshot 13 — Output of `systemctl status nginx --no-pager` showing Nginx `active (running)`

<img width="466" height="240" alt="Screenshot 2026-10-24 at 15 26 48" src="https://github.com/user-attachments/assets/7e4444e7-4570-4778-a039-4157535f91dd" />


---

#### Screenshot 14 — Output of `curl -I http://localhost` showing `HTTP/1.1 200 OK`

<img width="329" height="215" alt="Screenshot 2026-10-24 at 15 27 03" src="https://github.com/user-attachments/assets/977c4e3b-9a77-4dd0-b3d9-eede0a9d530a" />


---

#### Screenshot 15 — Browser showing the CodeTrack site loaded at `http://<EC2_PUBLIC_IP>`, with your Full Name and Group Name visible

<img width="809" height="337" alt="Screenshot 2026-10-24 at 15 27 23" src="https://github.com/user-attachments/assets/e19fba4d-8370-43a3-bc85-a997d1a3d56f" />

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/d2Y-zedq

---

#### Screenshot — LinkedIn post showing the deployed CodeTrack application

<img width="830" height="631" alt="Screenshot 2026-10-24 at 15 32 54" src="https://github.com/user-attachments/assets/c0b457f3-c60c-466b-8513-c8990fe10097" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Full Name and Group Name must be visible in the deployed application evidence
- `git log --oneline` output must show at least two meaningful commits
- Do not expose AWS access keys, passwords, private key contents, or other sensitive information

---

# Completion Checklist

- [✅] `CodeTrack` repository verified with `git status` (Screenshots 1–2)
- [✅] `index.html` and `style.css` created and populated (Screenshots 3–4)
- [✅] Starter files staged and committed in the first commit (Screenshots 5–8)
- [✅] Student Name and Group Name updated in `index.html` (Screenshot 9)
- [✅] Second controlled commit created (Screenshots 10–12)
- [✅] Nginx active on the EC2 instance and CodeTrack reachable via its public IP (Screenshots 13–15)
- [✅] LinkedIn post published and URL submitted
- [✅] No sensitive data exposed

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
