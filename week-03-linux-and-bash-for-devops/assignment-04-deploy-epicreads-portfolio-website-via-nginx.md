# Assignment 4 — Deploy EpicReads Portfolio Website via Nginx

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will deploy a static portfolio website on an Ubuntu VM using Nginx. You will download the website template, add your ownership proof in the footer, deploy the files to the Nginx web root, and verify the website is publicly accessible via a browser.

---

# Task 0 — Pre-flight Check

## Goal

Verify the Ubuntu VM and Nginx are ready for deployment.

### Evidence

#### Screenshot 0 — Output of `sudo systemctl status nginx --no-pager` showing Active (running)

<img width="913" height="740" alt="Screenshot 2026-10-07 190900" src="https://github.com/user-attachments/assets/63defc6d-9500-448f-a355-7c513924677a" />


# Task 1 — Get the Website Source Code

## Goal

Download and extract the portfolio website template.

### Evidence

#### Screenshot 1 — Output of `ls -la` showing the extracted project folder

<img width="688" height="381" alt="Screenshot 2026-10-07 191309" src="https://github.com/user-attachments/assets/80f97c3a-bff5-4ada-a7ad-f9786b312410" />


# Task 2 — Add Ownership Proof (Anti-Copy Change)

## Goal

Update the website footer with your deployment details.

### Evidence

#### Screenshot 2 — Nano editor open with the updated footer showing your Full Name, Group, Week, and Date

<img width="865" height="335" alt="Screenshot 2026-10-07 192820" src="https://github.com/user-attachments/assets/5d0758d5-989e-4a5c-8eee-c6760731e80c" />


# Task 3 — Deploy Website via Nginx

## Goal

Deploy the portfolio website to the Nginx web root.

### Evidence

#### Screenshot 3 — Output of `sudo nginx -t` showing configuration test successful

<img width="836" height="105" alt="Screenshot 2026-10-07 192944" src="https://github.com/user-attachments/assets/a6e3831c-b202-4446-9ff7-675e05fa7d1d" />


#### Screenshot 4 — Output of `ls /var/www/html` showing deployed website files

<img width="725" height="105" alt="Screenshot 2026-10-07 193054" src="https://github.com/user-attachments/assets/894441be-5039-47b6-9095-e6f0038ecbe8" />


# Task 4 — Verify Website is Live

## Goal

Verify the deployed website is publicly accessible and the footer contains your details.

### Evidence

#### Screenshot 5 — Output of `curl ifconfig.me` showing the server's public IP address

<img width="775" height="52" alt="Screenshot 2026-10-07 193226" src="https://github.com/user-attachments/assets/be51af0f-930d-4a50-87e1-dff1142a12fb" />


#### Screenshot 6 — Browser showing the live website with your Full Name and deployment details in the footer

<img width="957" height="1015" alt="Screenshot 2026-10-07 213115" src="https://github.com/user-attachments/assets/8d2be248-e063-4e7f-96d3-442fe0ec3154" />


# Task 5 — Mini Real DevOps Operational Check

## Goal

Verify the deployed website and Nginx service are healthy.

### Evidence

#### Screenshot 7 — Output of `systemctl is-enabled nginx`

<img width="927" height="76" alt="Screenshot 2026-10-07 211838" src="https://github.com/user-attachments/assets/3f619f16-d7a7-49d5-a376-786409b285bb" />


#### Screenshot 8 — Output of `curl -I http://localhost` showing 200 OK

<img width="830" height="251" alt="Screenshot 2026-10-07 211958" src="https://github.com/user-attachments/assets/f30bfeb0-4c89-44b5-9f55-d040758525d9" />


# LinkedIn Post (Mandatory)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dUNi2SvB

#### Screenshot — Published LinkedIn post showing the live website with your Full Name in the footer

<img width="1920" height="1080" alt="Screenshot (211)" src="https://github.com/user-attachments/assets/e7d21ec6-c6ea-4237-ba54-169636b4c473" />


# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Ownership proof in the footer is mandatory
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [ ] Screenshot 0: Nginx service status (active/running)
- [ ] Screenshot 1: Website files downloaded and extracted
- [ ] Screenshot 2: Footer updated with Full Name, Group, Week, and Date
- [ ] Screenshot 3: Nginx configuration test successful
- [ ] Screenshot 4: Website files deployed to /var/www/html
- [ ] Screenshot 5: Public IP retrieved
- [ ] Screenshot 6: Live website accessible in browser with footer details
- [ ] Screenshot 7: Nginx enabled on boot
- [ ] Screenshot 8: Local HTTP response returns 200 OK
- [ ] LinkedIn post published and URL submitted
- [ ] Full Name visible in all required screenshots
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
