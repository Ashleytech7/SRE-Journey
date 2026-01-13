# Day 8 – Reliability Concepts: SLI, SLO, SLA and Error Budgets (SRE Foundations)

## Overview
On Day 8, I learned the core reliability concepts that define Site Reliability Engineering. This day focused on how SREs **measure, define, and manage reliability** instead of aiming for unrealistic 100% uptime.

SREs do not try to eliminate all failures. Instead, they define acceptable levels of reliability that balance:
- system stability
- development speed
- operational cost
- business impact

The key concepts learned were SLI, SLO, SLA, and error budgets.

## The Core SRE Question
The main question SREs try to answer is:

“How reliable is reliable enough?”

Absolute reliability is impossible and extremely expensive. SREs therefore define clear targets and acceptable failure limits.

## Service Level Indicator (SLI)
An SLI (Service Level Indicator) is a **metric used to measure reliability**.

SLIs answer the question:
“How do we measure whether the service is working correctly?”

Examples of SLIs:
- uptime percentage
- request success rate
- error rate
- latency
- availability

Example:
- 99.9% of requests return a successful response
- 95% of requests respond within 300 milliseconds

SLIs are purely measurements. They do not include promises or targets.

## Service Level Objective (SLO)
An SLO (Service Level Objective) is the **target value** set for an SLI.

SLOs answer the question:
“How reliable does the service need to be?”

Example:
- SLI: request success rate
- SLO: 99.9% success rate per month

This means:
- small failures are acceptable
- limited downtime is allowed
- reliability is defined, not assumed

SLOs help teams balance reliability with development speed and cost.

## Service Level Agreement (SLA)
An SLA (Service Level Agreement) is a **formal promise made to customers**.

SLAs answer the question:
“What happens if reliability is not met?”

Examples:
- 99.9% monthly uptime guaranteed
- service credits or refunds if violated

Important points about SLAs:
- SLAs are customer-facing
- breaking an SLA has financial consequences
- SLAs are usually looser than internal SLOs

SRE best practice:
Always keep SLOs stricter than SLAs.

## Relationship Between SLI, SLO, and SLA
The relationship can be summarized as:

- SLI: what we measure
- SLO: what we aim for
- SLA: what we promise customers

Example:
- SLI: uptime
- SLO: 99.95%
- SLA: 99.9%

This creates a safety buffer for engineering teams.

## Error Budget
An error budget represents the **amount of failure that is allowed**.

It is calculated from the SLO.

Example:
- SLO: 99.9% uptime per month
- Total minutes in a month: ~43,200
- Allowed downtime: ~43 minutes

That allowed downtime is the error budget.

## Why Error Budgets Matter
Error budgets help teams make objective decisions.

If error budget is healthy:
- teams can deploy faster
- new features can be released

If error budget is exhausted:
- risky deployments are paused
- focus shifts to fixing reliability issues

This replaces arguments with data-driven decisions.

## SRE Mindset vs Traditional Operations
Traditional operations mindset:
- aim for zero downtime
- avoid all changes
- react to incidents

SRE mindset:
- accept limited failure
- measure reliability
- balance innovation with stability
- use data instead of opinions

This mindset is what makes SRE different from traditional ops roles.

## Real-World Example
For an API service:
- SLI: request success rate
- SLO: 99.9% per month
- SLA: 99.5% per month

If failures consume most of the error budget early in the month:
- deployments are slowed or paused
- root causes are fixed
- remaining budget is protected

## Why This Matters for SRE Roles
These concepts show that SREs:
- understand trade-offs
- think in terms of business impact
- use metrics to guide decisions
- design systems for sustainable reliability

Interviewers often test these concepts to see if candidates truly understand SRE principles.

## Key Takeaways
- 100% reliability is not realistic
- Reliability must be measured
- SLIs define what is measured
- SLOs define targets
- SLAs define customer promises
- Error budgets define acceptable failure
- Error budgets guide engineering decisions

## Next Step
Next, I will learn about **containers and Docker**, and why SREs use containers to build reliable and portable systems.
