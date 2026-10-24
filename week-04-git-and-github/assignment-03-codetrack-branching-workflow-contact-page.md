# Assignment 3 — CodeTrack: Branching Workflow (Add & Verify a Contact Page)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will add a new Contact page to CodeTrack using a clean feature-branch workflow. You will keep each change in a separate commit, prove that your default branch remains unchanged before the merge, and validate the result after merging.

---

# Task 1 — Confirm Repository State and Default Branch

## Goal

Start from a clean default branch (`main` or `master`) and confirm the repository status.

### Evidence

#### Screenshot 1 — Output of `git status` and `git branch` showing a clean status and the default branch checked out

<img width="326" height="207" alt="Screenshot 2026-10-15 at 12 12 46" src="https://github.com/user-attachments/assets/7e291779-e89a-4ed0-abbf-e583fef0d8fc" />


---

# Task 2 — Create and Switch to a Feature Branch

## Goal

Create a branch named exactly `feature/contact-page` and switch to it.

### Evidence

#### Screenshot 2 — Output of `git checkout -b feature/contact-page` and `git branch` showing `* feature/contact-page`

<img width="407" height="155" alt="Screenshot 2026-10-15 at 12 13 25" src="https://github.com/user-attachments/assets/aea31faf-ad0c-458c-89c8-fbd0d3785c3f" />


---

# Task 3 — Add contact.html on the Feature Branch

## Goal

Create `contact.html` with the provided content and commit it alone using the message `feat(contact): add Contact page`.

### Evidence

#### Screenshot 3 — Output of `ls` showing `contact.html`

<img width="505" height="482" alt="Screenshot 2026-10-15 at 12 14 00" src="https://github.com/user-attachments/assets/2d5cb8dd-ecc3-4206-86ee-fe5d4f3bbe8b" />


---

#### Screenshot 4 — Output of `git commit`

<img width="492" height="105" alt="Screenshot 2026-10-15 at 12 15 12" src="https://github.com/user-attachments/assets/5db5da1c-508a-4176-a464-fec18b2b5883" />


---

#### Screenshot 5 — Output of `git log --oneline -3` showing the new commit

<img width="538" height="174" alt="Screenshot 2026-10-15 at 12 15 23" src="https://github.com/user-attachments/assets/2e33e8fd-8ab3-45be-9739-8aca2d977828" />


---

# Task 4 — Add the Contact Link to index.html

## Goal

Add the provided Contact Page link to `index.html` and commit it separately using the message `feat(nav): add Contact Page link`.

### Evidence

#### Screenshot 6 — Output of `git status` showing `index.html` as modified before staging

<img width="540" height="165" alt="Screenshot 2026-10-15 at 12 16 25" src="https://github.com/user-attachments/assets/ccc18b89-d72d-4030-b0d4-9db2393c21cf" />


---

#### Screenshot 7 — Output of `git commit`

<img width="494" height="98" alt="Screenshot 2026-10-15 at 12 16 47" src="https://github.com/user-attachments/assets/a025fbc4-3135-448e-99a5-b6cd71382a27" />


---

#### Screenshot 8 — Browser showing the Contact Page link on the homepage while on `feature/contact-page`

<img width="716" height="704" alt="Screenshot 2026-10-15 at 12 20 44" src="https://github.com/user-attachments/assets/727c64df-a1c3-4c5d-9940-f216dc1209e0" />


---

# Task 5 — Verify Isolation (Prove the Default Branch Is Unchanged)

## Goal

Switch back to the default branch and confirm that `contact.html` and the Contact Page link do not exist there yet.

### Evidence

#### Screenshot 9 — Terminal showing the checkout and `ls` output, proving `contact.html` is absent

<img width="782" height="374" alt="Screenshot 2026-10-24 at 15 53 16" src="https://github.com/user-attachments/assets/ecbcec9c-34e2-4da9-b6a8-f67e93dcb225" />


---

#### Screenshot 10 — Browser showing the homepage on the default branch with no Contact Page link

<img width="363" height="98" alt="Screenshot 2026-10-15 at 12 17 31" src="https://github.com/user-attachments/assets/dcdab46b-f457-4b76-a6ae-67aedf3a3305" />


---

# Task 6 — Merge the Feature Branch into the Default Branch

## Goal

Merge `feature/contact-page` into your default branch and confirm the Contact page works.

### Evidence

#### Screenshot 11 — Output of `git merge feature/contact-page`

<img width="406" height="154" alt="Screenshot 2026-10-15 at 12 20 04" src="https://github.com/user-attachments/assets/6dffdce3-059d-4ddc-a870-4b405caf58fa" />


---

#### Screenshot 12 — Output of `ls` showing `contact.html` after the merge

<img width="693" height="303" alt="Screenshot 2026-10-15 at 12 21 39" src="https://github.com/user-attachments/assets/cd109aaa-edb0-4043-a91e-fd570b4eef06" />


---

#### Screenshot 13 — Browser showing the Contact page opened from the homepage link on the default branch

<img width="716" height="704" alt="Screenshot 2026-10-15 at 12 20 44" src="https://github.com/user-attachments/assets/651c773c-263a-4813-b298-bcd5d10935e1" />


---

# Task 7 — Inspect History (Graph View)

## Goal

Display the repository history as a graph and locate both feature commits.

### Evidence

#### Screenshot 14 — Full output of `git log --oneline --graph --decorate --all`
<img width="693" height="303" alt="Screenshot 2026-10-15 at 12 21 39" src="https://github.com/user-attachments/assets/0dbb84f7-12a2-4a62-9b36-bbba9516bfc8" />


---

# Task 8 — Optional Cleanup (Delete the Feature Branch)

## Goal

Delete the merged `feature/contact-page` branch to keep your branch list clean.

### Evidence

#### Screenshot 15 (Optional) — Output showing `feature/contact-page` deleted and no longer listed
<img width="384" height="104" alt="Screenshot 2026-10-15 at 12 22 01" src="https://github.com/user-attachments/assets/a8b0d35f-d832-4251-a43a-cb8dfe66dc33" />


---

# Submission Instructions

- Tasks 1–7 are required; Task 8 is optional
- Add all required screenshots in your submission
- Evidence must show `contact.html` and the homepage link were absent before merging, and working after merging
- Do not expose passwords, access tokens, or private keys

---

# Completion Checklist

- [ ] Repository confirmed clean on the default branch (Screenshot 1)
- [ ] `feature/contact-page` created and checked out (Screenshot 2)
- [ ] `contact.html` added in its own commit (Screenshots 3–5)
- [ ] Homepage Contact link added in a separate commit (Screenshots 6–8)
- [ ] Default branch proven unchanged before merge (Screenshots 9–10)
- [ ] Feature branch merged and Contact page verified (Screenshots 11–13)
- [ ] Graph history reviewed (Screenshot 14)
- [ ] Optional cleanup completed (Screenshot 15)
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
