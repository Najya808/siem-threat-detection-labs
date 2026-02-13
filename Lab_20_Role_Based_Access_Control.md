# Lab 20: Role-Based Access Control

## Objectives
- Understand the concepts of Role-Based Access Control (RBAC).
- Learn how to create and manage different user roles.
- Implement read-only access restrictions for specific roles.
- Test and validate the role-switching mechanism.

## Prerequisites
- Basic understanding of user roles and permissions.
- Familiarity with Linux command-line interface.
- Administrative access on a Linux system.

## Tools Required
- Ubuntu or any Linux-based OS
- PAM (Pluggable Authentication Modules)
- sudo and user management tools

---

## Task 1: Setup the Environment

### Update System
```bash
sudo apt update && sudo apt upgrade -y
Install Required Packages
sudo apt install sudo libpam0g-dev -y
Task 2: Create User Roles
Create Analyst Role
sudo groupadd analyst
sudo useradd -m -s /bin/bash -g analyst analyst_user
Create Admin Role
sudo groupadd admin
sudo useradd -m -s /bin/bash -g admin admin_user
Task 3: Implement Access Controls
Create Restricted Directory
sudo mkdir /var/restricted
sudo chown root:analyst /var/restricted
sudo chmod 750 /var/restricted
Test Analyst Permissions
su - analyst_user
echo "Test" > /var/restricted/test_file.txt
Expected: Permission denied.

Grant Admin Full Access
sudo chown admin_user:admin /var/restricted
sudo chmod 770 /var/restricted
Task 4: Test Role Switching
Test Admin Access
su - admin_user
echo "Admin Test" > /var/restricted/admin_test.txt
ls -l /var/restricted
Test Analyst Read Access
su - analyst_user
cat /var/restricted/admin_test.txt
Expected:

Analyst can read files.

Analyst cannot modify files.

Conclusion
This lab demonstrated how to implement Role-Based Access Control using Linux groups and permissions. Different roles were assigned specific privileges, ensuring secure access management and operational separation between users.
