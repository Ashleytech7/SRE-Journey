# Day 10 – SRE in the Cloud (AWS Mental Models)

## Overview
Day 10 focused on connecting all the SRE fundamentals learned so far to **real-world cloud environments**, especially AWS. The goal of this day was not to learn AWS services in depth, but to understand that **cloud platforms are built on the same core principles** of Linux, networking, monitoring, automation, and reliability.

This day helped remove the fear that AWS is something completely new or unrelated to SRE fundamentals.

## Key Realization
AWS does not introduce new fundamentals.

AWS provides **managed versions** of:
- servers
- networking
- monitoring
- logging
- automation
- scaling

The same SRE mindset and concepts still apply.

## Mapping SRE Fundamentals to AWS

### Servers
- Linux VM → EC2
- Same Linux OS
- Same CPU, memory, disk, and networking concepts
- Same types of failures

If you understand Linux, you already understand the core of EC2.

### Services and Processes
- systemd services → applications/processes running on EC2
- Docker containers → containers running on ECS or EKS
- restart policies → auto-restart and auto-scaling mechanisms

The reliability logic remains the same.

### Logs
- journalctl and application logs → CloudWatch Logs

Logs in AWS answer the same questions:
- what failed?
- when did it fail?
- how often is it failing?

AWS centralizes logs instead of keeping them on one server.

### Metrics
- top, free -h, df -h → CloudWatch Metrics

CloudWatch visualizes:
- CPU usage
- memory pressure
- disk usage
- latency
- error rates

These are the same metrics SREs monitor on a single server, but at cloud scale.

### Monitoring and Alerts
- manual checks → CloudWatch Alarms
- thresholds → alerts
- alerts → incident response

This is how production systems are monitored in the cloud.

### Networking
- DNS → Route 53
- ports and firewalls → Security Groups
- local testing → load balancers and health checks

Networking fundamentals do not change, only the tooling does.

### Scheduling and Automation
- cron jobs → EventBridge or scheduled tasks
- backups
- health checks
- maintenance jobs

Automation remains a core SRE principle in the cloud.

### Containers
- Docker → ECS or EKS
- image → deployment artifact
- container → running workload

Container fundamentals remain the same; orchestration is added on top.

## Cloud Incidents and SRE Response
A typical cloud incident might involve:
- increased latency
- failed requests
- unhealthy services

An SRE responds by:
- checking metrics
- reviewing logs
- validating health checks
- identifying recent deployments
- deciding whether to rollback, scale, or fix issues

This uses the same skills learned earlier in the course.

## Error Budgets in the Cloud
Error budgets play a critical role in cloud deployments.

If error budget is healthy:
- deploy new features faster
- allow innovation

If error budget is exhausted:
- pause risky deployments
- focus on reliability improvements

Error budgets prevent emotional decision-making and promote data-driven reliability.

## What SREs Actually Do in the Cloud
SREs do not spend all day configuring cloud services.

Their real work includes:
- monitoring dashboards
- responding to alerts
- debugging incidents
- improving automation
- collaborating with developers
- ensuring reliability targets are met

The tools change, but the responsibilities remain the same.

## Important Takeaway
Understanding SRE fundamentals first makes cloud platforms easier to learn.

AWS becomes a collection of managed tools that implement ideas you already understand:
- servers
- logs
- metrics
- automation
- reliability

This is why fundamentals are more important than memorizing services.

## Key Takeaways
- AWS builds on Linux and SRE fundamentals
- Cloud services are managed abstractions, not new concepts
- Logs and metrics work the same way, just at scale
- Error budgets guide deployment decisions
- SRE mindset stays constant across environments

## What This Means for My Journey
After Day 10, I now have a strong foundation to:
- start AWS hands-on learning confidently
- prepare for AWS certifications
- understand cloud-based SRE roles
- explain SRE concepts clearly in interviews

## Next Step
Next, I will decide to:
- go deeper into AWS hands-on learning
- prepare for AWS certification
