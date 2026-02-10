# Lab 03 — Preparing the Lab Environment

## Lab Overview
This lab focused on preparing a virtual environment for SIEM deployment.  
The goal was to install virtualization software, create a virtual machine, configure networking, and document system details required for future SIEM labs.

---

## Objectives
- Understand virtualization concepts
- Install VirtualBox or VMware
- Create and configure a SIEM virtual machine
- Configure networking using NAT
- Document IP addresses and network settings

---

## Tools & Technologies
- VirtualBox / VMware
- Ubuntu Linux
- Linux CLI
- Virtual Machines
- Networking (NAT Configuration)

---

## Task 1 — Install Virtualization Software

### Install VirtualBox
- Download VirtualBox from official website
- Install based on OS:
  - Windows: Run installer
  - Linux:
    ```bash
    sudo apt update
    sudo apt install virtualbox
    ```
  - macOS: Install using package installer

### Alternative — VMware
- Download VMware Player
- Follow installation steps

---

## Task 2 — Create SIEM Virtual Machine

### VM Configuration
- Name: SIEM-VM
- Type: Linux
- Version: Ubuntu 64-bit
- RAM: Minimum 2048 MB
- Disk Type: VDI
- Disk Allocation: Dynamically Allocated
- Disk Size: Minimum 20 GB

### Network Setup
- Adapter Type: NAT
- Enabled internet connectivity

---

## Task 3 — Document Network Configuration

### Start VM
- Boot VM
- Install Ubuntu OS

### Check IP Address
```bash
ip addr show
Recorded Information
IP Address

Subnet Mask

Network Configuration

Key Concepts Learned
Virtualization Setup

VM Creation

Network Configuration

Environment Preparation for SIEM Deployment

System Documentation
