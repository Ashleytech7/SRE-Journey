# Day 2 - Networking, Ports & Process Control

## Findings
- Multiple IPs exist due to different interfaces
- Main interface: eth0 with private IP (172.x.x.x)
- Loopback: 127.0.0.1 for local testing

## Open Ports Observed
- 53 - DNS Service
- 323 - Time Synchronization

## Actions Taken
- Identified running server on port 8000
- Found process using ps
- Killed process with kill <PID>
- Verified port 8000 is closed

## What I Learned
1. Difference between localhost, private and main IP
2. How to identify listening ports
3. How to stop a service like an SRE

