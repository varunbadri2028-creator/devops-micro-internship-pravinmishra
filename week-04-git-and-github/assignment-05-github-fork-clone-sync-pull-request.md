# Assignment 5 — Open-Source Collaboration: Fork, Clone, Sync & Pull Request

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will contribute one small documentation change to a shared repository using a standard open-source collaboration workflow: fork, clone, configure remotes, branch, commit, sync with upstream, push, and open a Pull Request. This is a different, separate practice repository from the one you submit your DMI work in.

---

# Task 0 — Fork the Upstream Repository

## Goal

Fork `pravinmishraaws/devops-micro-internship-interviews` into your own GitHub account.

### Evidence

#### Screenshot 1 — Your fork page with your username and `devops-micro-internship-interviews` visible in the browser URL

<img width="688" height="643" alt="Screenshot 2026-10-15 at 12 35 33" src="https://github.com/user-attachments/assets/dc8b4115-7a24-40b5-b39b-768f655403aa" />


---

# Task 1 — Authenticate GitHub from the Terminal

## Goal

Configure one authentication method — HTTPS with a Personal Access Token, or SSH — so you can push to your fork. Use only one method.

### Evidence

#### Screenshot 2 — Output of `git config --global --get credential.helper` (HTTPS) or `ssh -T git@github.com` (SSH) showing successful authentication — never show your token or private key

<img width="691" height="157" alt="Screenshot 2026-10-15 at 13 07 13" src="https://github.com/user-attachments/assets/e73cb0fd-6d7a-4589-af00-f41ea45e35f2" />


---

# Task 2 — Clone Your Fork and Configure Remotes

## Goal

Clone your fork locally, then add the original repository as `upstream`.

### Evidence

#### Screenshot 3 — Output of `git remote -v` showing `origin` pointing to your fork and `upstream` pointing to `pravinmishraaws/devops-micro-internship-interviews`

<img width="704" height="304" alt="Screenshot 2026-10-15 at 13 09 36" src="https://github.com/user-attachments/assets/c63acd9a-dba7-4e17-a990-20b0783631b7" />


---

# Task 3 — Create a Feature Branch and Make Your Change

## Goal

Create the branch `feature-readme-update`, add only your own entry (`Full Name — Group <Group Name/Number>`) to the Student List at the end of `pull_request.md`, and commit it with the message `docs: add my name to student list`.

### Evidence

#### Screenshot 4 — Output of `git status` showing `pull_request.md` modified before staging

<img width="669" height="295" alt="Screenshot 2026-10-15 at 13 20 47" src="https://github.com/user-attachments/assets/f900e87b-e8d3-4d7e-a24a-b45f0aba8fba" />


---

#### Screenshot 5 — Output of `git commit`

<img width="852" height="97" alt="Screenshot 2026-10-24 at 16 00 56" src="https://github.com/user-attachments/assets/1e16ef6f-a7d0-4153-8f84-6d49c0789f52" />


---

# Task 4 — Synchronize with Upstream and Push to Your Fork

## Goal

Fetch and merge `upstream/main` into your local default branch, rebase your feature branch onto it, then push `feature-readme-update` to your fork.

### Evidence

#### Screenshot 6 — Output of `git push -u origin feature-readme-update` showing a successful push

<img width="669" height="295" alt="Screenshot 2026-10-15 at 13 20 47" src="https://github.com/user-attachments/assets/95b219a1-c525-47ee-b5e1-503f69340e06" />


---

#### Screenshot 7 — Your fork on GitHub showing `feature-readme-update` in the branch selector or a "Compare & pull request" banner

<img width="733" height="849" alt="Screenshot 2026-10-15 at 13 26 03" src="https://github.com/user-attachments/assets/78065f3a-202b-48de-b36a-01919e56d958" />
---

# Task 5 — Create a Pull Request to Upstream

## Goal

Open a Pull Request from `feature-readme-update` on your fork to `main` on the upstream repository, using the title `docs: add my name to student list`.

### Evidence

#### Screenshot 8 — Pull Request creation page showing the correct base repository, base branch, head repository, compare branch, and title
<img width="627" height="721" alt="Screenshot 2026-10-15 at 13 27 49" src="https://github.com/user-attachments/assets/08aec89c-f9ea-44a3-bea1-2f436d10b562" />


---

#### Screenshot 9 — Successfully created Pull Request page with the PR number visible
<img width="878" height="796" alt="Screenshot 2026-10-15 at 13 28 57" src="https://github.com/user-attachments/assets/0ab6e55f-7b16-4d7c-adbe-f51ca215b3c5" />


---

#### Pull Request URL

Paste your Pull Request URL here:

https://github.com/pravinmishraaws/devops-micro-internship-interviews/pull/496

---

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dDKkznFp

---

#### Screenshot — LinkedIn post showing your successfully created Pull Request

<img width="847" height="751" alt="Screenshot 2026-10-15 at 13 38 12" src="https://github.com/user-attachments/assets/cdc0f71f-9251-434c-b6b1-42ba2b03a27e" />


---

# Submission Instructions

- Add all required screenshots in your submission
- Do not expose a Personal Access Token, SSH private key, password, or authentication secret
- Only your own entry in `pull_request.md` may be added — do not edit or delete another student's entry
- Include your fork URL and Pull Request URL

---

## Fork URL

Paste your fork URL here:

https://github.com/varunbadri2028-creator/devops-micro-internship-interviews

---

# Completion Checklist

- [✅] Upstream repository forked to your GitHub account (Screenshot 1)
- [✅] GitHub authentication configured securely (Screenshot 2)
- [✅] Fork cloned locally with `origin` and `upstream` configured (Screenshot 3)
- [✅] Only `pull_request.md` modified, with your own entry added (Screenshots 4–5)
- [✅] Local default branch synchronized with `upstream/main`, feature branch rebased and pushed (Screenshots 6–7)
- [✅] Pull Request opened against the correct upstream repository and branch (Screenshots 8–9)
- [✅] Fork URL and Pull Request URL included
- [✅] LinkedIn post published and URL submitted
- [✅] No PAT, password, private key, or authentication secret exposed

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
