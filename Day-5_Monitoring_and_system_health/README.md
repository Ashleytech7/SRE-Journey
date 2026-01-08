# Day 5 – Monitoring, Metrics and System Health

## Overview
On Day 5, I learned how Site Reliability Engineers determine whether a system is healthy, not just running. This day focused on metrics, which show how a system behaves over time (CPU load, memory usage, disk usage, etc).

Logs tell us what happened.  
Metrics tell us how the system is performing right now.

Understanding metrics helps detect performance problems and prevent outages.

## Logs vs Metrics

### Logs answer:
- What happened?
- When did it happen?
- Why did it happen?

### Metrics answer:
- Is the system healthy right now?
- Is it overloaded?
- Is performance getting worse?
- Are we close to a failure?

Both are important in production systems.

## CPU Load using uptime

Command:
uptime

Example output:
14:20:15 up  2:10,  1 user,  load average: 0.35, 0.24, 0.20

Load average values show CPU demand over the last:
- 1 minute
- 5 minutes
- 15 minutes

### Important concept
Compare load to the number of CPU cores.

Example:
- On a 2-core system, load above 2.0 means CPU is overloaded.
- On a 4-core system, load above 4.0 means overload.

High load causes delays and slow responses.

## Live Monitoring using top

Command:
top

This shows real-time information about:
- CPU usage
- memory usage
- running processes

CPU fields:
- %us = user CPU time
- %sy = system/kernel CPU time
- %wa = time waiting on disk I/O
- %id = idle CPU time

High %wa usually means disk bottlenecks.

Exit key:
q

## Memory Monitoring using free -h

Command:
free -h

This shows:
- total RAM
- used RAM
- free RAM
- swap usage

### Key idea
If swap usage increases, RAM is full and the OS is using disk as slow backup memory. This usually makes the system lag.

## Disk Usage using df -h

Command:
df -h

This shows:
- filesystem
- total size
- used space
- available space
- percent used

### Important rule
If disk reaches 100%:
- services may crash
- logs cannot be written
- updates fail
- the system may become unstable

Best practice: keep disk usage below 80–85%.

## Service Running vs Service Healthy

A running service is not always a healthy service.

A service may be running but still unhealthy if:
- CPU usage is very high
- memory is exhausted
- disk is full
- the process is frozen
- requests are failing or slow

Running does not always mean working properly.

Healthy means the service is responding normally.

## Why Metrics Matter in SRE

Metrics help detect:

| Metric | Meaning |
|--------|--------|
| High CPU load | System slowdown |
| High RAM usage | Memory pressure |
| Swap usage increasing | RAM exhausted |
| Disk near 100% | Application failure risk |
| High network usage | Traffic spike or overload |
| Restart count increasing | Crash loop |
| Latency increasing | Application slow |

Metrics allow proactive action before outages happen.

## Commands Practiced

uptime  
top  
free -h  
df -h  
systemctl status sre-app  

## Key Takeaways

- Metrics complement logs
- Load average indicates CPU demand over time
- Swap usage indicates RAM pressure
- Full disks can break systems
- A running service may still be unhealthy
- Monitoring helps prevent failures

## Observations

- free -h and df -h are simple and powerful tools
- Load average helps detect overload early
- Health checks are better than only checking whether a service is running
- Monitoring enables early problem detection

## Next Step

Next, I will learn shell scripting for SRE automation and write simple scripts to help monitor and manage systems.
