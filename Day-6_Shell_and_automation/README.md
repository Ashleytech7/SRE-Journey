# Day 6 – Shell Scripting and Automation for SRE

## Overview
On Day 6, I learned about shell scripting, which is one of the most important skills for a Site Reliability Engineer. A shell script allows multiple terminal commands to be stored in a file and executed together. This enables automation, consistency, and reliability — instead of manually running commands every time.

SREs use shell scripts for:
- health checks
- backups
- monitoring
- log cleanup
- automated recovery
- scheduled maintenance

Automation reduces human error and helps systems remain reliable.

## What is a Shell Script?
A shell script is simply a text file that contains a list of commands. When the script is executed, the commands run in sequence.

Example script name:
hello.sh

## The Shebang Line
Most scripts begin with:

#!/bin/bash

This is called the **shebang**. It tells the operating system that the script should be executed using the Bash shell.

## Creating a Script

Steps followed:

1. Create a script file  
nano hello.sh  

2. Add this content  
#!/bin/bash  
echo "Hello SRE!"  

3. Make the script executable  
chmod +x hello.sh  

4. Run the script  
./hello.sh  

Output:  
Hello SRE!

This was my first automated command execution.

## System Health Script

I created another script to automatically collect system health information.

Filename:
healthcheck.sh

Content:
#!/bin/bash  
echo "Health Check Running..."  
echo "CPU Load:"  
uptime  
echo "Memory:"  
free -h  
echo "Disk:"  
df -h  

Then:
chmod +x healthcheck.sh  
./healthcheck.sh  

This script prints CPU load, memory usage, and disk space. It works like a simple diagnostic tool.

## File Execution Permissions

Before a script can run, it must be made executable using:
chmod +x filename  

Without this, Linux will not allow the script to execute.

## Exit Codes

Every command returns an exit status:

0 = success  
non-zero = failure  

To view the last exit code:
echo $?  

Example:
ls  
echo $?   → returns 0  

ls abcxyz  
echo $?   → returns a non-zero value  

Exit codes help scripts make decisions.

## Service Auto-Recovery Script

I created a basic script that checks if a service is running and restarts it if needed.

Filename:
check_service.sh

Content:
#!/bin/bash  

systemctl is-active --quiet sre-app  

if [ $? -ne 0 ]  
then  
  echo "Service is DOWN — restarting..."  
  sudo systemctl restart sre-app  
else  
  echo "Service is running fine"  
fi  

Purpose of this script:
- checks if sre-app is active
- if not, restarts it
- otherwise prints status

This is an example of **auto-remediation**, a key SRE practice.

## Why Automation Matters in SRE
Automation reduces:
- manual work
- mistakes
- delays during incidents

And improves:
- reliability
- response time
- consistency

Manual work does not scale — automation does.

## Commands Learned

chmod +x filename  
./scriptname  
echo $?  
nano filename  
systemctl is-active servicename  
systemctl restart servicename  

## Key Takeaways

- A shell script is a file containing commands executed together.
- The shebang (#!/bin/bash) tells Linux to run the script in Bash.
- chmod +x makes a script executable.
- Exit code 0 means success.
- Scripts help automate monitoring and recovery.
- Auto-recovery scripts are a real-world SRE concept.

## Observations

- Running scripts feels more efficient than typing commands repeatedly.
- Automation improves reliability.
- Even small scripts can be powerful.
- Understanding exit codes is important for logic decisions in scripts.

## Next Step
Next, I will learn about **cron jobs**, which allow scripts to run automatically on a schedule. This turns scripts into fully automated maintenance tools.


