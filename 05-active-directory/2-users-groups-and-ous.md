# Active Directory Users, Groups, and OUs

This page contains my notes on Active Directory users, computer accounts, security groups, and Organizational Units (OUs).

---

## User Accounts

A user account represents an identity inside the Active Directory domain.

Users can authenticate to the domain and access resources according to their permissions.

A user may represent:

- An employee
- An administrator
- A service account

Example:

`phillip`

---

# Computer Accounts

Computers that join the Active Directory domain also have accounts.

These are called:

`Computer Accounts`

or:

`Machine Accounts`

Machine account names commonly end with:

`$`

Example:

`DC01$`

This allows computers to be identified and authenticated inside the domain.

---

# Security Groups

Security Groups are used to manage access to resources.

Instead of assigning the same permission separately to many users, users can be added to a group.

Permissions can then be assigned to the group.

Example:

`Accounting Group`

↓

`Access to Accounting Folder`

↓

`Users in the group receive access`

A simple way to remember:

`User → Group → Permission`

---

# Why Security Groups Are Useful

Imagine ten employees need access to the same shared folder.

Without groups:

`User 1 → Permission`

`User 2 → Permission`

`User 3 → Permission`

and so on.

With a Security Group:

`10 Users`

↓

`Accounting Security Group`

↓

`Folder Permission`

This makes permission management much easier.

---

# Important Active Directory Groups

Some important groups from my notes include:

## Domain Admins

Members have very high administrative privileges in the domain.

They can perform major administrative tasks across the domain.

---

## Domain Users

Contains domain users.

---

## Domain Computers

Contains computer accounts that belong to the domain.

---

## Domain Controllers

Contains Domain Controller computer accounts.

---

## Backup Operators

Members can have broad access required for backup-related operations.

---

# Organizational Units — OUs

OU stands for:

`Organizational Unit`

An OU is used to organize Active Directory objects.

It can be thought of as an organizational folder inside the domain.

Example structure:

`THM.local`

↓

`THM`

↓

`IT`

`Management`

`Marketing`

`R&D`

`Sales`

Users can be placed into OUs according to departments or administrative needs.

---

# Example Organization

A company may organize its users like this:

`THM`

↓

`Sales OU`

→ Sales employees

`IT OU`

→ IT employees

`Marketing OU`

→ Marketing employees

`Management OU`

→ Management employees

This makes the Active Directory structure easier to manage.

---

# Why OUs Are Important

OUs are especially useful because administrators can apply policies to specific groups of users or computers.

For example:

`Sales OU`

→ Control Panel restricted

→ Specific company policies

while:

`IT OU`

→ Different policies

This allows different departments to receive different configurations.

---

# OU vs Security Group

This distinction is very important.

| OU | Security Group |
|---|---|
| Used to organize objects | Used to manage permissions |
| Often used for applying policies | Often used for resource access |
| Represents administrative structure | Represents access membership |
| A user is organized within the OU structure | A user can belong to multiple groups |

A simple way to remember:

`OU = Which policies apply to this user?`

`Security Group = What can this user access?`

---

# Example

Imagine a user named:

`Sophie`

Sophie works in Sales.

She may be placed inside:

`Sales OU`

This allows Sales-related policies to apply to her account.

At the same time, Sophie could be a member of groups such as:

`Domain Users`

`Sales Shared Folder Users`

`VPN Users`

These groups control access to different resources.

So:

`OU → Organization / Policy`

`Security Group → Access / Permission`

---

# Users Can Belong to Multiple Groups

A user may need access to many different resources.

For example:

`Phillip`

may belong to:

- Domain Users
- Sales Users
- VPN Users
- File Share Users

This allows the user to receive permissions from several different groups.

---

# Organizing Computers

OUs are not only used for users.

Computer accounts can also be organized.

For example:

`Workstations`

`Servers`

`Domain Controllers`

This allows different policies to be applied to different types of computers.

---

# Workstations

User computers can be placed inside a:

`Workstations OU`

This makes it easier to apply workstation-specific policies.

Examples might include:

- Desktop restrictions
- Security settings
- Software configuration

---

# Servers

Servers can be placed inside a:

`Servers OU`

Servers may require different policies from normal user computers.

---

# Domain Controllers OU

Domain Controllers are normally placed inside a dedicated:

`Domain Controllers`

OU.

Because Domain Controllers are critical systems, they usually require stricter and more specialized policies.

---

# Managing the Active Directory Structure

The Active Directory structure should reflect the needs of the organization.

For example:

`Domain`

↓

`Department OUs`

↓

`Users`

and:

`Computer OUs`

↓

`Workstations / Servers`

A clear structure makes administration and policy management easier.

---

# Removing Old OUs

My lab also included reviewing the existing Active Directory structure and comparing it with the organization's current structure.

An extra department OU existed even though the department had been removed from the organization.

The OU therefore needed to be removed from Active Directory.

By default, OUs may be protected against accidental deletion.

This protection helps administrators avoid deleting important organizational structures by mistake.

---

# Protect Object from Accidental Deletion

When accidental deletion protection is enabled, attempting to delete the OU may fail.

To manage this setting in the lab:

1. Open Active Directory Users and Computers
2. Enable `View → Advanced Features`
3. Open the OU properties
4. Open the `Object` tab
5. Review the `Protect object from accidental deletion` setting

This feature provides additional protection for important Active Directory objects.

---

# Why Organization Matters in Cybersecurity

Poorly organized Active Directory environments can make access management difficult.

Clear use of OUs and groups helps administrators:

- Apply security policies correctly
- Control access to resources
- Reduce unnecessary permissions
- Separate administrative responsibilities
- Understand which users and computers belong to which part of the organization

---

# Quick Reference

| Term | Purpose |
|---|---|
| User Account | Represents a user identity |
| Computer Account | Represents a domain-joined computer |
| Machine Account `$` | Computer account naming convention |
| Security Group | Used for permissions and access |
| OU | Organizes Active Directory objects |
| Domain Admins | Highly privileged domain group |
| Domain Users | Domain user group |
| Domain Computers | Domain computer accounts |
| Workstations OU | Organizes user computers |
| Servers OU | Organizes servers |
| Domain Controllers OU | Organizes Domain Controllers |

---

## Key Takeaway

The easiest way to remember the difference is:

`OU = Organization + Policy`

`Security Group = Permission + Access`

A user can be placed inside an OU for management and policy purposes while also belonging to several Security Groups for resource access.
