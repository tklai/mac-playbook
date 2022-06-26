---
title: Ansible - Infrastructure as Code
author: TK Lai @tklai
date: 2022-04-25
---

# Ansible

> Ansible is automation powered by people.

## Have you ever...

- Wipe and setup your machine?
- Setup new OS or new clusters?
- Find multiple servers installed different version of software?

## Back in Time

- Setup Individually
- Must stand in front of the server
- Later time
    - Sever Managemnet Technology (KVM over IP, Dell iDRAC, HPE iLO)
    - Remote Install

```
 Model A                     Model A
 Server / PC A               Server / PC B
+---------------------+     +---------------------+
|+-------------------+|     |+-------------------+|
||      Software     ||     ||      Software     ||
|+-------------------+|     |+-------------------+|
||      Drivers      ||     ||      Drivers      ||
|+-------------------+|     |+-------------------+|
||      System       ||     ||      System       ||
|+-------------------+|     |+-------------------+|
+---------------------+     +---------------------+

 Model B                     Model B
 Server / PC C               Server / PC D
+---------------------+     +---------------------+
|+-------------------+|     |+-------------------+|
||      Software     ||     ||      Software     ||
|+-------------------+|     |+-------------------+|
||      Drivers      ||     ||      Drivers      ||
|+-------------------+|     |+-------------------+|
||      System       ||     ||      System       ||
|+-------------------+|     |+-------------------+|
+---------------------+     +---------------------+
```

## Back in Time

- Cloning
- Installed all software you need in one computer and freeze the status
- CloneZilla / Norton Ghost

```
 Model A                      Model A                      Model A
 Server / PC A                HDD Clone                    Server / PC B
+---------------------+      +---------------------+      +---------------------+
|                     |      |+-------------------+|      |                     |
|                     |      ||      Software     ||      |                     |
|                     |      |+-------------------+|      |                     |
|       Target        |  <-  ||      Drivers      ||  ->  |       Target        |
|                     |      |+-------------------+|      |                     |
|                     |      ||      System       ||      |                     |
|                     |      |+-------------------+|      |                     |
+---------------------+      +---------------------+      +---------------------+
                                       ^
                                       |
                      ------------------
                      |
          Model A                         Model B
          +---------------------+         +---------------------+
          |+-------------------+|         |+-------------------+|
          ||      Software     ||         ||      Software     ||
          |+-------------------+|         |+-------------------+|
          ||      Drivers      ||         ||      Drivers      ||
          |+-------------------+|         |+-------------------+|
          ||      System       ||         ||      System       ||
          |+-------------------+|         |+-------------------+|
          +---------------------+         +---------------------+
                                                    |
                                        -------------
                                        |
                                        v
 Model B                      Model B                      Model B
 Server / PC C                HDD Clone                    Server / PC D
+---------------------+      +---------------------+      +---------------------+
|                     |      |+-------------------+|      |                     |
|                     |      ||      Softwares    ||      |                     |
|                     |      |+-------------------+|      |                     |
|       Target        |  <-  ||      Drivers      ||  ->  |       Target        |
|                     |      |+-------------------+|      |                     |
|                     |      ||      System       ||      |                     |
|                     |      |+-------------------+|      |                     |
+---------------------+      +---------------------+      +---------------------+
```

## Back in Time

- Virtualisation Templating
- Virtual Appliance Template

```
                      VM Template
                     +---------------------+
                     |+-------------------+|
                     ||      Software     ||
                     |+-------------------+|
                     ||      Drivers      ||
                     |+-------------------+|
                     ||      System       ||
                     |+-------------------+|
                     +---------------------+
                                |
            --------------------------------------
            |                                    |
            v                                    v
Model A                             Model B
Cluster A                           Cluster B
Virtualisation Technology           Virtualisation Technology
+---------------------------+      +---------------------------+
|   VM A                    |      |   VM B                    |
|  +---------------------+  |      |  +---------------------+  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      Software     ||  |      |  ||      Software     ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      Drivers      ||  |      |  ||      Drivers      ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      System       ||  |      |  ||      System       ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  +---------------------+  |      |  +---------------------+  |
|                           |      |                           |
|   VM C                    |      |   VM D                    |
|  +---------------------+  |      |  +---------------------+  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      Software     ||  |      |  ||      Software     ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      Drivers      ||  |      |  ||      Drivers      ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  ||      System       ||  |      |  ||      System       ||  |
|  |+-------------------+|  |      |  |+-------------------+|  |
|  +---------------------+  |      |  +---------------------+  |
|                           |      |                           |
+---------------------------+      +---------------------------+
```

## What is Ansible

- Automation
- Repeatable and Reliable
- Provision

## Advantage

- Declarative
  - Focus on What you want
  -  How to get there
  - How to install
  - (If playbooks / roles available)
- Agent-less
  - Run tasks via SSH instead of specific programs
    - MDM
    - Some Legacy and Endpoint Systems (NOD32 Endpoint Security)
- Idempotent
    - 1st run result: asdf
    - nth run result: asdf
- Community
  - Ansible Galaxy

## Terms

- Inventory - Phone Book (Mapping)
- Playbook
    - Ordered list of plays
    - Bunch of tasks
    - Bunch of roles
    - Role Type
        - By application
            - Multiple operation systems
                - Linux Distros (Debian, Fedora, ArchLinux)
                - APT `apt install` :)
                - RPM `dnf install` :)
                - Pacman `pacman -Sy` ;P
        - By job duties
            - Install a set of tools to a machine
- Role
    - Applications or configurations you want to set up in the host
    - Install web server
    - Install database
    - Install AIO
- Play
    - Task

## Demo

## Terraform vs Ansible

- Terraform - `Orchestration`
- Ansible - `Configuration Management`

- K8s - `Orchestration`
- Docker

- Ansible Automation controller - `Orchestration`

## References

- Ansible is Simple IT Automation
  `https://www.ansible.com/`

- What is Ansible - IBM Technology
  `https://www.youtube.com/watch?v=fHO1X93e4WA`
