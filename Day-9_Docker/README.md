# Day 9 – Containers and Docker (SRE Foundations)

## Overview
On Day 9, I learned about **containers** and **Docker**, and why they are heavily used by Site Reliability Engineers. The focus of this day was not on mastering Docker commands, but on understanding the **problem containers solve** and how they improve reliability, consistency, and deployment speed.

Containers help eliminate the common issue of “it works on my machine” by ensuring applications run the same way everywhere.

## The Problem Containers Solve
Before containers, applications often failed when moved between environments due to:
- different operating systems
- different library versions
- missing dependencies
- configuration differences

These inconsistencies caused frequent production issues and increased operational complexity.

Containers solve this by packaging everything an application needs to run.

## What is a Container?
A container is a lightweight, isolated environment that includes:
- the application
- required libraries
- dependencies
- runtime configuration

Containers share the host OS kernel, making them faster and more lightweight than virtual machines.

## Image vs Container
An **image** is a read-only template used to create containers.  
A **container** is a running instance of an image.

Analogy:
- Image = class (template)
- Container = object (instance)

Images do not change, while containers can start, stop, and fail.

## Why SREs Use Containers
From an SRE perspective, containers provide:
- consistent environments across systems
- faster deployments
- easier restarts and rollbacks
- better isolation between services
- predictable behavior

This reduces unknown variables and improves system reliability.

## Installing and Verifying Docker
Docker was installed on the system and verified using:

docker --version

Docker functionality was confirmed by running a test container.

## Running the First Container
The first container executed was:

docker run hello-world

This command:
- pulled the hello-world image
- created a container
- ran it
- printed output
- exited successfully

This confirmed Docker was working correctly.

## Running a Web Server in a Container
A real service was run using Docker:

docker run -d -p 8080:80 nginx

Explanation:
- -d runs the container in detached mode
- -p 8080:80 maps host port 8080 to container port 80
- nginx is the web server image

The service was accessed using:
http://localhost:8080

The NGINX welcome page confirmed the container was running and accessible.

## Port Mapping Concept
Port mapping allows traffic from the host machine to reach services running inside containers.

In the example:
- host port 8080 forwards traffic to
- container port 80

This enables containerized services to be accessed like normal applications.

## Viewing Running Containers
To observe running containers, the following command was used:

docker ps

This displayed container ID, image name, status, and port mappings.

## Why Containers Improve Reliability
Containers improve reliability by:
- bundling dependencies with the application
- ensuring identical runtime behavior
- reducing environment-specific bugs
- making deployments repeatable and predictable

This aligns well with SRE goals of stability and consistency.

## Commands Practiced

docker --version  
docker run hello-world  
docker run -d -p 8080:80 nginx  
docker ps  

## Key Takeaways
- Containers package applications with their dependencies
- Docker is a tool to build and run containers
- Images are templates; containers are running instances
- Port mapping enables access to containerized services
- Containers reduce environment-related failures
- SREs use containers to improve reliability and consistency

## What This Means for SRE
Containers allow SREs to deploy and operate services in a predictable and repeatable way. By reducing environmental differences, containers help teams focus on reliability, performance, and real system issues instead of configuration problems.

## Next Step
Next, I will move to day 10 of this SRE learning plan, which focuses on **connecting SRE concepts to cloud environments (AWS)** and understanding how these fundamentals apply in real-world cloud systems.
