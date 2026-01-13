# Day 7 – Scheduling and Automation with Cron (SRE Foundations)

## Overview
On Day 7, I learned how Site Reliability Engineers automate tasks to run automatically at specific times or intervals using **cron**. While shell scripts define *what* actions to perform, cron defines *when* those actions should run.

Cron is a core SRE tool because it removes dependency on humans and ensures important operational tasks are executed consistently and reliably.

## What is Cron?
Cron is a time-based job scheduler in Linux. It allows commands or scripts to be executed automatically according to a predefined schedule.

A scheduled task in cron is called a **cron job**.

Examples of cron usage:
- running health checks every few minutes
- performing daily backups
- cleaning up old logs
- executing maintenance tasks at night

## Cron Daemon
Cron works using a background service called the **cron daemon**.

- It runs continuously in the background
- It wakes up every minute
- It checks whether any scheduled jobs need to run
- It executes jobs at the correct time

Cron jobs run even if no user is logged in.

## Checking Cron Status
To verify that cron is running, I used:

systemctl status cron

This confirmed that the cron service was active.

## Viewing Existing Cron Jobs
To check whether I already had cron jobs configured, I used:

crontab -l

Since this was my first time using cron, it showed that no crontab was defined for my user.

## Editing Cron Jobs
To create or edit cron jobs, I used:

crontab -e

This opens the cron table editor, where scheduled jobs are defined.

## Cron Job Format
A cron job consists of five time fields followed by the command to run.

Format:

minute hour day_of_month month day_of_week command

Each field controls when the job is executed.

## Understanding the Time Fields

minute        0–59  
hour          0–23  
day_of_month  1–31  
month         1–12  
day_of_week   0–7 (0 and 7 represent Sunday)

## Example Cron Expression
Example:

*/2 * * * * command

Meaning:
- run every 2 minutes
- every hour
- every day
- every month
- every day of the week

## Hands-on Cron Test
I created a safe test cron job to verify that cron was working.

Cron entry added:

*/2 * * * * echo "cron is working" >> /tmp/cron_test.log

This job:
- runs every 2 minutes
- appends output to a log file
- does not affect the system

After waiting a few minutes, the log file showed repeated entries, confirming that cron was executing the job automatically.

## Why Logging is Important in Cron
Cron jobs do not display output in the terminal. If a job fails silently, it can go unnoticed.

By redirecting output to a log file, we can:
- verify execution
- debug failures
- confirm automation is working as expected

Logging is critical for observability.

## Why Cron is Important for SRE
Cron helps SREs by:
- eliminating manual repetitive work
- ensuring tasks always run on schedule
- preventing missed operations
- improving system reliability

Cron is more reliable than humans because it never forgets or skips tasks.

## Common Cron Mistakes
- using relative paths instead of absolute paths
- forgetting to make scripts executable
- assuming environment variables exist
- not logging output

These mistakes often cause cron jobs to fail silently.

## Commands Practiced

systemctl status cron  
crontab -l  
crontab -e  

## Key Takeaways

- Cron is used for time-based automation
- Cron jobs run independently of user sessions
- The cron daemon executes scheduled jobs
- Logging cron output is essential
- Cron ensures reliability by removing human dependency

## What This Means for SRE
Cron turns scripts into fully automated, self-running tasks. This allows SREs to build systems that maintain themselves, perform regular checks, and reduce operational risk.

## Next Step
Next, I will learn **core reliability concepts used in SRE**, including SLIs, SLOs, SLAs, and error budgets.
