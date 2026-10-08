# Assignment 6 — Build an AI-Assisted Linux Health Check (AI-Assisted Linux Incident Triage)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will build a read-only Bash triage script that checks the health of your Ubuntu server and Nginx application, connect it to Claude Code as a reusable `/linux-triage` skill, simulate a controlled Nginx incident, use the skill to gather and analyze evidence, recover the service manually, and verify recovery. The workflow follows the Agentic Loop: Gather → Analyze → Human Act → Verify.

---

# Task 1 — Confirm the Healthy Baseline and Create the Workspace

## Goal

Confirm that Nginx and the React application are healthy before building the automation.

### Evidence

#### Screenshot 1 — Output of `systemctl is-active nginx`, `ss -ltn | grep ':80'`, and `curl -I http://localhost`

<img width="912" height="430" alt="Screenshot 2026-10-09 000239" src="https://github.com/user-attachments/assets/961a2879-6a27-4e1b-9fea-99feeedffbaf" />


#### Screenshot 2 — Output of `pwd` and `find . -maxdepth 4 -type d | sort` showing the workspace folder structure

<img width="912" height="235" alt="Screenshot 2026-10-09 000353" src="https://github.com/user-attachments/assets/86e2f95a-c3d8-4ee0-b3ce-eea07bd96ca7" />


### Notes

Answer the following in your own words:

**1. What proves that Nginx is running?**

The command systemctl is-active nginx returned active, which proves that Nginx is running.

**2. What proves that the server is listening for HTTP traffic?**

The ss -ltn | grep ':80' command showed LISTEN on port 80, proving that the server is listening for HTTP traffic.

**3. Why must you capture a healthy baseline before simulating an incident?**

A healthy baseline gives us a reference point for comparison. After simulating an incident, we can compare the new results with the baseline to identify what changed and confirm that the system has recovered

# Task 2 — Create Project Context and Safety Rules in CLAUDE.md

## Goal

Tell Claude exactly what this project does and what it is not allowed to do.

### Evidence

#### Screenshot 3 — CLAUDE.md open in VS Code showing all four sections (Project Overview, Incident Workflow, Safety Rules, Output Rules)

<img width="1917" height="1015" alt="Screenshot 2026-10-09 001010" src="https://github.com/user-attachments/assets/a7522e43-c911-4589-868f-586ab1407d4d" />


### Notes

Answer the following in your own words:

**1. Why should Claude receive project-specific operational rules?**

Project-specific rules tell Claude what the project does, what it should check, and what actions it must avoid. This helps Claude work safely and consistently.

**2. Why is the human required to execute the recovery command?**

The human must execute the recovery command because recovery can change the system or affect services. Keeping this step with the human prevents the AI from making an unsafe automatic change.

**3. Which rule prevents Claude from making an unsupported diagnosis?**

The rule “Do not make unsupported diagnoses” prevents Claude from making conclusions that are not supported by the collected evidence. It must base conclusions only on the evidence collected.

# Task 3 — Use Agentic AI to Plan Before Writing the Script

## Goal

Use Claude Code to inspect the environment and produce a read-only plan before creating any Bash code.

### Evidence

#### Screenshot 4 — Claude Code showing the five-check plan and read-only inspection results

<img width="928" height="612" alt="Screenshot 2026-10-09 001732" src="https://github.com/user-attachments/assets/4faa768d-58a3-405b-bf20-971d97436a7a" />


### Notes

Answer the following in your own words:

**1. Which part of this task represents the Gather phase?**

The read-only inspection of the Ubuntu server and Nginx represents the Gather phase. It collected evidence about the Nginx status, port 80, HTTP response, configuration, and error logs.

**2. Did Claude follow the instruction not to create files? How did you verify this?**

Yes. No files were created or modified during the inspection. I verified this by checking that the inspection only used read-only commands and that linux-triage.sh had not been created yet.

**3. Why is planning before coding useful in DevOps automation?**

Planning helps identify the required checks, commands, and expected results before writing the script. This reduces mistakes and makes the automation more organized and reliable.

# Task 4 — Build the Linux Triage Bash Script

## Goal

Create one Bash script that gathers consistent Linux and Nginx health evidence.

### Evidence

#### Screenshot 5 — Top section of `linux-triage.sh` showing variables, thresholds, and the checks array

<img width="941" height="915" alt="Screenshot 2026-10-09 002150" src="https://github.com/user-attachments/assets/f2296e25-d8ce-4e7a-9a70-8030bc72f256" />


#### Screenshot 6 — Middle section showing check functions and conditionals

<img width="956" height="1008" alt="Screenshot 2026-10-09 002255" src="https://github.com/user-attachments/assets/ab1ac4df-ca73-4a1f-bc75-e7d7580692de" />


#### Screenshot 7 — Bottom section showing the loop, summary function, and exit behavior

<img width="905" height="870" alt="Screenshot 2026-10-09 002347" src="https://github.com/user-attachments/assets/7ed8a711-90a7-4f4f-a3f1-87e1d0a44583" />


#### Screenshot 8 — Output of `bash -n scripts/linux-triage.sh` (no syntax errors) and `ls -l scripts/linux-triage.sh` showing executable permission

<img width="922" height="121" alt="Screenshot 2026-10-09 002441" src="https://github.com/user-attachments/assets/5da552a1-840d-43f2-9715-43d7a84cde48" />


### Notes

Answer the following in your own words:

**1. What is stored in the checks array?**

The checks array stores the five health check names: Nginx status, port 80, HTTP response, Nginx configuration, and error logs.

**2. How does the `for` loop use that array?**

The for loop goes through each item in the checks array one by one and uses the case statement to run the corresponding health-check function.

**3. Why are the health checks separated into functions?**

Separating the checks into functions makes the script organized, easier to understand, and easier to maintain or update.

**4. What is the purpose of `$(...)` in this script?**

$(...) is used for command substitution. It runs a command and stores its output in a variable. For example, the script uses it to store the HTTP status code and count recent Nginx errors.

**5. Why does the script use different exit codes for HEALTHY, WARN, and FAIL?**

Different exit codes allow other tools or scripts to quickly identify the result:

0 → HEALTHY
1 → WARN
2 → FAIL

This makes the script useful for automation and monitoring.

# Task 5 — Run and Understand the Healthy-State Report

## Goal

Run the Bash script against the healthy server and verify that it creates a report.

### Evidence

#### Screenshot 9 — Output of `./scripts/linux-triage.sh` showing your Full Name and all five check results

<img width="930" height="421" alt="Screenshot 2026-10-09 002807" src="https://github.com/user-attachments/assets/74333e15-7eb9-4118-9c72-1ae4dddf96f3" />


#### Screenshot 10 — Output showing the captured exit code and final summary

<img width="903" height="490" alt="Screenshot 2026-10-09 002902" src="https://github.com/user-attachments/assets/9316c752-6264-459d-be29-b6fe5c62e385" />


### Notes

Answer the following in your own words:

**1. What is the overall status of your healthy baseline?**

The overall status of my healthy baseline is WARN. All five checks completed, with 4 checks passing and 1 warning due to a recent Nginx error-log entry. There were no failures.

**2. Which exact Linux evidence proves the application is serving traffic?**

The exact evidence is Port 80 is listening and HTTP response: 200. The ss check confirms Nginx is listening on port 80, and curl receiving HTTP 200 confirms the application is responding to requests.

**3. Did your script return exit code 0 or 1? Explain why.**

The script returned exit code 1 because there was a warning from 1 recent Nginx error-log entry. There were no failed checks, so the script used exit code 1 for the warning state.

**4. What is the difference between a warning and a failure in this script?**

A warning means something needs attention, but the application is still working. A failure means a critical health check has failed, such as Nginx being inactive, port 80 not listening, or the HTTP request failing. Warnings return exit code 1, while failures return exit code 2.

# Task 6 — Create and Run the /linux-triage Skill

## Goal

Turn the Bash script into a reusable, manually invoked Agentic AI workflow.

### Evidence

#### Screenshot 11 — `SKILL.md` showing the frontmatter, allowed tool restrictions, and safety rules

<img width="958" height="1007" alt="Screenshot 2026-10-09 003153" src="https://github.com/user-attachments/assets/ebb61156-45b0-44d1-bb03-f39573a2456b" />


#### Screenshot 12 — `/linux-triage` output for the healthy server

<img width="1536" height="1024" alt="assign5" src="https://github.com/user-attachments/assets/ffd2f0a9-998f-4def-bec2-e6d3d8ca1fa7" />


### Notes

Answer the following in your own words:

**1. Why does this skill have Bash, Read, and Grep, but not Write?**

The skill uses Bash, Read, and Grep for read-only inspection and evidence collection. Write is not included because the skill should not modify files or system configuration during triage.

**2. Why is `disable-model-invocation: true` useful for this skill?**

It prevents Claude from automatically invoking the skill on its own. The human operator must explicitly run /linux-triage, giving the human control over when the diagnostic process starts.

**3. What part is performed by Bash, and what part is performed by Claude?**

Bash performs the actual Linux checks and collects evidence, such as Nginx status, port 80, HTTP response, configuration, and logs. Claude reads and analyzes that evidence, explains the results, and suggests the next step without performing the recovery action.

**4. Why is this better than asking Claude "Is my server healthy?" without giving it evidence?**

Because Claude can base its answer on actual Linux evidence instead of guessing. The evidence-based approach makes the diagnosis more reliable, shows exactly what was checked, and helps prevent unsupported conclusions.

# Task 7 — Simulate an Nginx Incident and Let the Skill Diagnose It

## Goal

Create a controlled service failure, gather evidence through Bash, and let Claude analyze the evidence without taking recovery action.

### Evidence

#### Screenshot 13 — Output showing Nginx is inactive and the HTTP request fails

<img width="932" height="163" alt="Screenshot 2026-10-09 003821" src="https://github.com/user-attachments/assets/a601813a-3d47-4603-a347-d0459506422d" />


#### Screenshot 14 — `/linux-triage` output showing failed evidence, most likely cause, and a suggested recovery command

<img width="1536" height="1024" alt="assign5-2" src="https://github.com/user-attachments/assets/42ebfec3-f47d-42ed-a888-0f5275e040e8" />


#### Screenshot 15 — `incident-failure-report.txt` showing the failed checks and your Full Name

<img width="930" height="430" alt="Screenshot 2026-10-09 004148" src="https://github.com/user-attachments/assets/664007b6-96aa-40fe-98bc-5ce3558aac79" />


### Notes

Answer the following in your own words:

**1. Which three checks failed?**

The three failed checks were the Nginx service status, port 80 listening check, and HTTP response check.

**2. What evidence supports the conclusion that Nginx is unavailable?**

The evidence shows that the Nginx service is inactive, port 80 is not listening, and the HTTP request to localhost fails. Together, these show that Nginx is unavailable and cannot serve the application.

**3. Did Claude execute the recovery command? Why is that important?**

No. Claude only suggested the recovery command. The human operator must execute it because recovery actions can change the system and may have unintended effects.

**4. Which phase of the Agentic Loop is represented by the Bash report?**

The Bash report represents the Gather phase because it collects the actual Linux and Nginx evidence.

**5. Which phase is represented by Claude's explanation?**

Claude's explanation represents the Analyze phase because it interprets the collected evidence, identifies the most likely cause, and suggests the next step.

# Task 8 — Recover Manually, Verify Again, and Write the Incident Summary

## Goal

Recover the service as the human operator and prove that the system is healthy again.

### Evidence

#### Screenshot 16 — Output showing Nginx is active and `curl -I http://localhost` returns 200 OK

<img width="917" height="360" alt="Screenshot 2026-10-09 004735" src="https://github.com/user-attachments/assets/6b96ba00-6ac8-49f0-b6c7-0dea2207ce2f" />


#### Screenshot 17 — Second `/linux-triage` output showing successful recovery with no FAIL results

<img width="1536" height="1024" alt="assign6" src="https://github.com/user-attachments/assets/efefc30a-4413-49fe-86a3-dc6e8e4eefef" />


#### Screenshot 18 — Output of `ls -lah reports` showing both `incident-failure-report.txt` and `recovery-report.txt`

<img width="892" height="175" alt="Screenshot 2026-10-09 004856" src="https://github.com/user-attachments/assets/d4f8be3f-6bd0-4e71-b6e2-1392ef1dc8d1" />


#### Screenshot 19 — `incident-summary.md` showing all required sections and your Full Name

<img width="970" height="1015" alt="Screenshot 2026-10-09 004956" src="https://github.com/user-attachments/assets/734e4454-46c5-4ccf-b28b-6d92d2a2b8b0" />


### Notes

Answer the following in your own words:

**1. What action did you execute manually?**

I manually executed sudo systemctl start nginx to restart the Nginx service after reviewing the triage results.

**2. What evidence proves that the service recovered?**

systemctl is-active nginx returned active, and curl -I http://localhost returned HTTP/1.1 200 OK, proving that Nginx was running and serving HTTP traffic again.

**3. Why is the second triage run necessary?**

The second triage run verifies that the recovery was successful and checks the system again for any remaining failures.

**4. What could go wrong if an AI agent automatically restarted every failed service?**

It could restart a service unnecessarily, interrupt an important application, cause downtime, or hide the real cause of the failure.

**5. In one sentence, explain the difference between using AI as a chatbot and using AI in this agentic workflow.**

A chatbot mainly gives answers, while this agentic workflow uses AI to analyze real system evidence, suggest an action, and verify the result while keeping the actual recovery action under human control.

# Incident Summary

Fill in all seven sections below in your own words.

**Full Name:** B. Varun Kumar


**Date:** 09/10/2026


**1. Reported Symptom**

The Nginx web application became unavailable during the controlled incident simulation. The website stopped responding to HTTP requests.

**2. Evidence Collected**

Nginx service status showed inactive.
Port 80 was not listening.
curl -I http://localhost failed to connect.
The Nginx configuration test was successful.
The triage script reported three failed checks: Nginx service status, port 80, and HTTP response.

**3. Most Likely Cause**

The Nginx service was stopped during the controlled incident simulation. As a result, port 80 stopped listening and HTTP requests failed, although the Nginx configuration remained valid.

**4. Human-Approved Recovery Action**

After reviewing the evidence, I manually executed the following command to start Nginx again:

sudo systemctl start nginx

The AI suggested the recovery command, but I executed it manually.

**5. Verification**

After recovery, systemctl is-active nginx returned active, and curl -I http://localhost returned HTTP/1.1 200 OK. These results confirmed that Nginx was running and responding to HTTP requests again. I then ran the triage checks again to verify the service status.

**6. Safety Decision**

The AI was allowed to analyze evidence and recommend a recovery action, but it did not execute the command. Keeping recovery under human control helps prevent unintended changes, unnecessary service interruptions, and unsafe actions.

**7. Agentic Loop Mapping**

Gather: The Bash script collected Nginx status, port 80, HTTP response, configuration, and error-log evidence.
Analyze: The AI interpreted the results and identified the stopped Nginx service as the likely cause.
Human Act: I manually executed sudo systemctl start nginx.
Verify: I checked the service status, confirmed the HTTP 200 response, and ran the triage checks again.

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

https://lnkd.in/p/dY7aYiJh

#### Screenshot — Published LinkedIn post

<img width="1917" height="727" alt="Screenshot 2026-10-09 005910" src="https://github.com/user-attachments/assets/b30b32aa-1b3b-4781-a240-b3f99c48c725" />


# GitHub Repository URL

Paste the URL of your GitHub folder or repository containing the assignment files here:

https://github.com/varunbadri2028-creator/devops-micro-internship-pravinmishra/edit/main/week-03-linux-and-bash-for-devops/assignment-06-ai-assisted-linux-health-check.md

# Submission Instructions

- Add all required screenshots in your submission
- Full Name must be visible in required screenshots and the Bash report
- All written answers must be in your own words
- Do not expose sensitive information (keys, passwords, AWS account IDs, tokens)
- GitHub URL must be included in this document

---

# Completion Checklist

- [ ] Task 1: Healthy baseline confirmed, workspace created (Screenshots 1–2, Notes answered)
- [ ] Task 2: CLAUDE.md created with all four sections (Screenshot 3, Notes answered)
- [ ] Task 3: Five-check plan produced by Claude using read-only tools (Screenshot 4, Notes answered)
- [ ] Task 4: `linux-triage.sh` created, syntax validated, executable permission set (Screenshots 5–8, Notes answered)
- [ ] Task 5: Healthy-state report generated with no FAIL result (Screenshots 9–10, Notes answered)
- [ ] Task 6: `/linux-triage` skill created and run successfully on healthy server (Screenshots 11–12, Notes answered)
- [ ] Task 7: Nginx incident simulated, failed evidence captured, Claude did not execute recovery (Screenshots 13–15, Notes answered)
- [ ] Task 8: Nginx recovered manually, recovery verified, reports saved, incident summary complete (Screenshots 16–19, Notes answered)
- [ ] Incident summary contains all seven required sections
- [ ] LinkedIn post published and URL submitted
- [ ] Full Name visible in all required screenshots and the Bash report
- [ ] Skill does not have Write permission
- [ ] Skill did not execute any recovery commands
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
