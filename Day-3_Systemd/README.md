# Day 3 – systemd & Services (SRE Basics)

## What I Learned
- Difference between processes and services
- How systemd manages services
- How to create a custom systemd service
- Why services should not run as root
- Auto-restart and reliability concepts

## Commands Used
- systemctl status
- systemctl list-units --type=service
- systemctl start sre-app
- systemctl daemon-reload
# Day 3 – systemd & Service Management (SRE Foundations)

## Overview
On Day 3, I learned how real production services are run and managed on Linux systems using **systemd**.  
Instead of manually running commands in a terminal, I learned how Site Reliability Engineers ensure that services:
- Start automatically
- Restart on failure
- Run securely
- Remain available without human intervention

This day focused on **reliability, process management, and security basics**, which are core SRE responsibilities.

---

## Key Concepts Learned

### 1. Process vs Service
- A **process** is a running instance of a program.
  - Example: `python3 -m http.server 8000`
  - If the terminal closes, the process stops.
- A **service** is a managed process controlled by the operating system using `systemd`.
  - Services run in the background.
  - They can automatically restart if they crash.
  - They are not tied to a terminal session.

**SRE Insight:**  
Production systems use services, not manual commands, to ensure reliability.

---

### 2. What is systemd?
- `systemd` is the **service manager** in modern Linux systems.
- It is responsible for:
  - Starting services at boot
  - Restarting failed services
  - Tracking service health
  - Managing logs

Every Linux system has:
- **PID 1** → `systemd`  
If systemd stops, the system stops.

---

### 3. systemctl (Service Control Tool)
`systemctl` is used to interact with systemd.

Common commands learned:
- `systemctl status` → Check system health
- `systemctl list-units --type=service` → List running services
- `systemctl start <service>` → Start a service
- `systemctl stop <service>` → Stop a service

**SRE Usage:**  
During outages, SREs first check service status using `systemctl`.

---

### 4. Understanding Service States
Each service has multiple states:

- **LOAD**
  - Indicates whether systemd knows about the service
  - Example: `loaded`
- **ACTIVE**
  - Indicates whether the service is healthy
- **SUB**
  - More detailed state like:
    - `running` → continuously running service
    - `exited` → one-time task completed successfully
    - `failed` → service error (critical for SREs)

**Important:**  
`active (exited)` is normal for one-time system services.

---

### 5. Creating a Custom systemd Service
I created a custom service (`sre-app.service`) to run a Python HTTP server as a managed service.

This service:
- Runs in the background
- Is monitored by systemd
- Automatically restarts on failure

---

### 6. Explanation of Service File Sections

#### [Unit]
- Defines metadata and dependencies
- `After=network.target` ensures the service starts after networking is available

#### [Service]
- `ExecStart` → Command to start the service
- `WorkingDirectory` → Directory from which the service runs
- `Restart=always` → Automatically restarts the service on failure
- `User=<username>` → Runs the service as a non-root user (security best practice)

#### [Install]
- `WantedBy=multi-user.target` → Enables auto-start at system boot

---

### 7. Why Services Should Not Run as Root
Running services as `root` is dangerous because:
- A bug or exploit can compromise the entire system
- Root has unrestricted access to files, users, and system configuration

**Security Principle Learned:**  
**Least Privilege** — give services only the permissions they need.

---

### 8. Reliability & Auto-Restart
Using:
```ini
Restart=always
RestartSec=3
```

ensures:

- The service is automatically restarted if it crashes
- Downtime is minimized
- No human intervention is required

#### SRE Term Learned:
`Crash Loop` — when a service repeatedly crashes and restarts, indicating a deeper issue.

### What This Means for SRE

This day introduced real-world SRE practices:

- Service reliability
- Process supervision
- Security through least privilege
- Infrastructure managed by the OS, not humans

This is how production systems stay online 24/7.
