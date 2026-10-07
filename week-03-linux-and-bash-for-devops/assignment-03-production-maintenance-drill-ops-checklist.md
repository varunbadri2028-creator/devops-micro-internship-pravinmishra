# Assignment 3 — Production Maintenance Drill (OPS Checklist)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In this assignment, you will treat your already deployed React application (on Ubuntu VM with Nginx) as a live production system. You will perform structured operational checks covering network validation, service health, log analysis, resource monitoring, configuration verification, and incident simulation with recovery — mirroring real on-call DevOps responsibilities.

---

# Task 1 — Server Access & Networking Validation

## Goal

Verify that the deployed React application is reachable from the browser and confirm basic network connectivity of the Ubuntu VM.

### Evidence

#### Screenshot 1 — Browser showing the React app with your Full Name visible on the UI

<img width="772" height="565" alt="Screenshot 2026-10-06 221208" src="https://github.com/user-attachments/assets/e791ba88-132c-4e01-b94d-e264d49bda7b" />


#### Screenshot 2 — Output of `ip a`

<img width="870" height="340" alt="Screenshot 2026-10-06 223141" src="https://github.com/user-attachments/assets/d4a1e46f-65b9-407e-8e67-0443c7b0d07c" />


#### Screenshot 3 — Output of `sudo ss -tulpen`

<img width="1917" height="475" alt="Screenshot 2026-10-06 223309" src="https://github.com/user-attachments/assets/5a47d66c-046e-4c22-9d19-aa99285608e7" />


#### Screenshot 4 — Output of `sudo ufw status`

<img width="615" height="67" alt="Screenshot 2026-10-06 223544" src="https://github.com/user-attachments/assets/a24627ec-44e8-4b48-b7e6-5da6026d261f" />


### Notes

Answer the following in your own words:

**1. What proves Nginx is listening on 0.0.0.0:80?**

The sudo ss -tulpen output shows 0.0.0.0:80 in the LISTEN state, and the process is identified as nginx. This proves Nginx is listening for HTTP connections on port 80 on all IPv4 interfaces.

**2. What proves SSH is active on port 22?**

In my current WSL environment, there is no listener on port 22 in the sudo ss -tulpen output. Therefore, SSH is not running/listening on port 22 in this environment.

**3. Did you find any unexpected open ports? Explain briefly.**

No unexpected application ports were found. Nginx is listening on port 80, while the other ports shown are related to system DNS and time synchronization services. Since this is a local WSL environment, SSH on port 22 is not enabled.

# Task 2 — Service Health & Systemd Validation (Nginx)

## Goal

Verify that Nginx is properly installed, running, enabled at boot, and safely configured.

### Evidence

#### Screenshot 1 — Output of `systemctl status nginx --no-pager`

<img width="863" height="555" alt="Screenshot 2026-10-06 223752" src="https://github.com/user-attachments/assets/0c0b3355-4b5a-42cd-a8ed-9c5818771ae6" />


#### Screenshot 2 — Output of `sudo nginx -t`

<img width="638" height="106" alt="Screenshot 2026-10-06 223907" src="https://github.com/user-attachments/assets/7d6f274d-c7f4-44e0-b371-807fff1053b0" />


#### Screenshot 3 — Output of `sudo ss -lptn '( sport = :80 )'`

<img width="1627" height="193" alt="Screenshot 2026-10-06 224027" src="https://github.com/user-attachments/assets/1a9077ea-734c-49f9-8aa6-81a8be18aa51" />


### Notes

Answer the following in your own words:

**1. What happens if Nginx fails to restart in production?**

If Nginx fails to restart, the website may become unavailable because Nginx is responsible for serving the application. I would check the service status and configuration test, identify the problem, fix it, and restart Nginx safely.

**2. What's your basic rollback plan?**

My basic rollback plan is to keep a known-working configuration and application build as a backup. If a new deployment causes a problem, I would restore the previous working configuration or build, test Nginx with nginx -t, and restart the service.

# Task 3 — Logs & Request Trace

## Goal

Verify real traffic flow and analyze logs to understand system behavior and errors.

### Evidence

#### Screenshot 1 — Output of `sudo tail -n 30 /var/log/nginx/access.log`

<img width="1920" height="1080" alt="Screenshot (209)" src="https://github.com/user-attachments/assets/b723e7e7-ce55-4352-8c23-8af88bedf8bb" />


#### Screenshot 2 — Output of `sudo tail -n 30 /var/log/nginx/error.log`

<img width="757" height="65" alt="Screenshot 2026-10-06 224358" src="https://github.com/user-attachments/assets/c14df2a0-4d30-42d5-a67d-e0c034c78aa8" />


#### Screenshot 3 — Output of `sudo journalctl -u nginx --no-pager -n 50`

<img width="1920" height="1080" alt="Screenshot (210)" src="https://github.com/user-attachments/assets/39f37f46-30df-43e8-ac32-925851b8cb95" />


### Notes

Answer the following in your own words:

**1. Were there any errors in the logs?**

- If yes, mention 1–2 example error lines from the logs and explain what each one means in simple terms.
- If no, explain what it means if the error log is empty or shows no recent errors during your check.

No recent Nginx errors were found. The error log only contains a normal notice about inherited sockets, which is not an application or configuration error.

**2. If there were no errors, what does that indicate about the system?**

It indicates that Nginx is operating normally and there are no recent logged errors affecting the web server during this check.

**3. Based on the access logs, were your curl requests visible in the log entries? What does that prove about traffic flow?**

Yes. The Nginx access log contains multiple curl requests such as GET / and HEAD / with HTTP status 200. This proves that the requests reached Nginx and Nginx successfully served the application response.

# Task 4 — System Resource Health Check (Capacity Red Flags)

## Goal

Assess server capacity and detect potential performance or failure risks.

### Evidence

#### Screenshot 1 — Output of `uptime`

<img width="635" height="65" alt="Screenshot 2026-10-06 224733" src="https://github.com/user-attachments/assets/2f61eb7b-e01e-4418-8c76-6bf0ca49a8e4" />


#### Screenshot 2 — Output of `free -h`

<img width="735" height="123" alt="Screenshot 2026-10-06 224834" src="https://github.com/user-attachments/assets/caa84ad7-6599-48c5-8e79-9479711180d8" />


#### Screenshot 3 — Output of `df -h`

<img width="836" height="360" alt="Screenshot 2026-10-06 224931" src="https://github.com/user-attachments/assets/fef007fa-0438-447d-a88e-8a5ae6d3859a" />


#### Screenshot 4 — Output of `sudo du -sh /var/* | sort -h`

<img width="708" height="342" alt="Screenshot 2026-10-06 225036" src="https://github.com/user-attachments/assets/86fb8860-cdf5-4f9b-92ac-6f9297d96256" />

### Notes

Answer the following in your own words:

**1. Which resource looks most critical right now? (CPU/load, memory, or disk) Explain why.**

Disk usage looks the most critical resource to monitor because disk space is used for the operating system, application files, logs, and temporary files. If disk usage gets too high, it can affect system and application operations. The CPU load and memory usage are currently not showing a critical condition.

**2. What happens if disk becomes 100% full in a production server?**

If the disk becomes 100% full, the server may not be able to create or write new files. Logs may stop being written, deployments can fail, applications may become unstable, and some services can stop working properly. Therefore, disk usage should be monitored and unnecessary files or old logs should be cleaned up before the disk reaches full capacity.

# Task 5 — Configuration & Deployment Verification

## Goal

Ensure the correct React build is deployed and Nginx is serving it properly.

### Evidence

#### Screenshot 1 — Output of `ls -lah /var/www/html | head -n 20`

<img width="673" height="320" alt="Screenshot 2026-10-07 182756" src="https://github.com/user-attachments/assets/b4c035c8-a2ff-412c-9bfd-63c37f2673d1" />


#### Screenshot 2 — Output of `grep -R "Deployed by" -n /var/www/html 2>/dev/null | head`

<img width="1917" height="598" alt="Screenshot 2026-10-07 183251" src="https://github.com/user-attachments/assets/c8404483-eef3-47a9-b1b6-dbee1f710a2b" />


#### Screenshot 3 — Output of `grep -n "try_files" /etc/nginx/sites-available/default`

<img width="845" height="77" alt="Screenshot 2026-10-07 183443" src="https://github.com/user-attachments/assets/4f888fbb-d51b-4efd-a823-56598dd7f573" />


### Notes

Answer the following in your own words:

**1. How do you confirm that the correct version of the application is deployed?**

I confirm that the correct version of the application is deployed by checking the files in `/var/www/html`, verifying the expected application content such as my name and deployment date, and checking the Nginx configuration. The `try_files $uri $uri/ /index.html;` rule also confirms that Nginx is serving the deployed React application correctly.


# Task 6 — Nginx Configuration Failure Simulation

## Goal

Simulate a real-world Nginx misconfiguration and recover the service safely.

### Evidence

#### Screenshot 1 — Output of `sudo nginx -t` showing the syntax error (broken config)

<img width="912" height="102" alt="Screenshot 2026-10-07 184743" src="https://github.com/user-attachments/assets/ad1ca5a2-4f43-4879-b4e8-c2dc6b6e7e7b" />


#### Screenshot 2 — Output of `sudo nginx -t` showing syntax ok (fixed config)

<img width="668" height="80" alt="Screenshot 2026-10-07 184922" src="https://github.com/user-attachments/assets/56111613-24b8-4877-b00f-47922b69ed1e" />


#### Screenshot 3 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

<img width="615" height="233" alt="Screenshot 2026-10-07 185028" src="https://github.com/user-attachments/assets/cbbbb46f-b9f2-4457-b427-765b93b4e8bb" />


### Notes

Answer the following in your own words:

**1. What caused the configuration failure?**

The failure was caused by adding an invalid Nginx directive, invalid_directive;, to the configuration file. Nginx reported it as an unknown directive and the configuration test failed.

**2. How did you fix the issue?**

I restored the previous working Nginx configuration from the backup, then ran sudo nginx -t to verify that the configuration syntax was correct. After the test passed, I reloaded Nginx and confirmed recovery with curl -I http://localhost, which returned HTTP/1.1 200 OK.

**3. How can you avoid this kind of issue in real production systems?**

In production, configuration changes should be tested with nginx -t before reloading or restarting Nginx. Keeping backups or using version control, testing changes in a staging environment, and having a rollback plan can also prevent configuration errors from causing downtime.

# Task 7 — Web Application Failure Simulation

## Goal

Simulate missing deployment content and recover the application safely.

### Evidence

#### Screenshot 1 — Output of `curl -I http://<public-ip>` showing failure (non-200 response)

<img width="545" height="181" alt="Screenshot 2026-10-07 185524" src="https://github.com/user-attachments/assets/46a38b1f-2b9e-4706-b0cc-bd9970b96010" />


#### Screenshot 2 — Output of `curl -I http://<public-ip>` confirming recovery (200 OK)

<img width="638" height="240" alt="Screenshot 2026-10-07 185655" src="https://github.com/user-attachments/assets/04575e68-4f5f-4f3c-8c60-d355551db221" />


### Notes

Answer the following in your own words:

**1. What caused the application to break in this scenario?**

The application broke because the index.html file was temporarily moved from /var/www/html. Since Nginx could not find the required file, it returned a 403 Forbidden response.

**2. How did you fix the issue and restore the application?**

I restored the index.html file to /var/www/html using the backup file. I then tested the application with curl -I http://localhost and confirmed that it returned HTTP/1.1 200 OK.

**3. What steps would you take to prevent this kind of issue in real production systems?**

I would use backups and version-controlled deployments, test deployments before releasing them, use health checks and monitoring, and avoid manually deleting or moving important application files on the production server. A rollback plan should also be available if a deployment fails.

# Task 8 — Security & Reliability Review

## Goal

Review and reflect on the security and reliability practices applied during this assignment.

### Security & Reliability Notes

Answer the following in your own words:

**1. Why is SSH key-based authentication more secure than sharing passwords?**

SSH key-based authentication uses a private key and a public key instead of a shared password. The private key stays with the user, making it harder for attackers to guess or brute-force compared with passwords.

**2. Why should only required ports be open on a production server?**

Only required ports should be open to reduce the server's attack surface. Closing unnecessary ports prevents unwanted services from being accessed and reduces potential security risks.

**3. Why is it important for Nginx to be enabled on boot?**

Nginx should be enabled on boot so that it starts automatically after a server restart. This helps ensure that the web application becomes available without requiring someone to start Nginx manually.

**4. What are the risks of sharing secrets, keys, or credentials publicly?**

Publicly sharing secrets, keys, or credentials can allow unauthorized users to access servers, applications, databases, or cloud accounts. This can lead to data theft, account compromise, service disruption, and unexpected costs.

**5. Why should cloud resources be stopped or terminated when they are no longer needed?**

Unused cloud resources should be stopped or terminated to avoid unnecessary charges and reduce security exposure. Removing unused resources also helps keep the cloud environment clean and easier to manage.

# LinkedIn Post (Required)

## Evidence

#### LinkedIn Post URL

Paste your LinkedIn post URL here:

`Add your URL here`

---

#### Screenshot — Published LinkedIn post

Add your screenshot here.

---

# Submission Instructions

- Add all required screenshots in your submission
- Full name must be visible in required screenshots
- Do not expose sensitive information (keys, passwords, account IDs)

---

# Completion Checklist

- [ ] Task 1: Screenshots (browser, ip a, ss -tulpen, ufw status) + Notes answered
- [ ] Task 2: Screenshots (nginx status, nginx -t, ss port 80) + Notes answered
- [ ] Task 3: Screenshots (access log, error log, journalctl) + Notes answered
- [ ] Task 4: Screenshots (uptime, free -h, df -h, du -sh) + Notes answered
- [ ] Task 5: Screenshots (ls html, grep deployed by, grep try_files) + Notes answered
- [ ] Task 6: Screenshots (nginx -t fail, nginx -t pass, curl recovery) + Notes answered
- [ ] Task 7: Screenshots (curl failure, curl recovery) + Notes answered
- [ ] Task 8: Security & Reliability Notes answered
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
