# Day 4: Logs, Failures & Crash Loop Handling
## 🛠 SRE Fundamentals

On Day 4, the focus was on how Site Reliability Engineers debug production issues using logs and handle service failures safely. This module bridges the gap between running a service and maintaining its reliability.

---

## 📋 Overview
Logs are the primary source of truth during incidents. This day introduced how to move away from guesswork and toward systematic debugging.

* **Understanding Logs:** Using timestamped records to diagnose events.
* **Systemd Journaling:** Mastering `journalctl` to read system logs.
* **Failure Analysis:** Observing service behavior during crashes.
* **Incident Control:** Identifying and stopping dangerous **Crash Loops**.

---

## 🔍 Key Concepts

### What Are Logs?
Logs help SREs answer three critical questions:
1. **What** happened?
2. **When** did it happen?
3. **Why** did it happen?

### The "Crash Loop"
A crash loop occurs when a service crashes, `systemd` restarts it automatically, and the service immediately crashes again.
* **The Danger:** It consumes system resources and can hide the root cause.
* **The Fix:** SREs often stop the service entirely to "stop the bleeding" before investigating the configuration.

### Why Auto-Restart is a Double-Edged Sword
While essential for high availability, auto-restarts can destabilize a system if the service is fundamentally broken. SREs must monitor restart counters to ensure a service isn't stuck in an infinite failure cycle.

---

## 💻 Commands Practiced

| Command | Description |
| :--- | :--- |
| `journalctl` | Displays logs for the entire system. |
| `journalctl -u sre-app` | Shows historical logs for a specific service. |
| `journalctl -u sre-app -f` | **Follows** logs in real-time (live debugging). |
| `systemctl status sre-app` | Checks the current state and restart count. |
| `systemctl stop sre-app` | Stops a service to interrupt a crash loop. |
| `systemctl daemon-reload` | Reloads systemd after fixing a configuration file. |

---

## 🛠 Troubleshooting Workflow
To practice real-world incident handling, I followed these steps:
1. **Identify:** Noticed repeated failures in `journalctl -u sre-app -f`.
2. **Contain:** Stopped the service to prevent resource exhaustion.
3. **Repair:** Fixed the misconfiguration in the service file.
4. **Restore:** Reloaded the daemon and restarted the service.
5. **Verify:** Confirmed stability by monitoring logs post-fix.

---

## 🚀 SRE Takeaways
* **Evidence-Based Debugging:** Always use logs as the primary source of truth.
* **System Stability First:** During an incident, prioritize stopping the damage before applying a permanent fix.
* **Tool Mastery:** Knowing how to filter and follow logs is essential for reducing Mean Time to Recovery (MTTR).
