# Active Directory Basics

This page contains my notes on Windows domains, Domain Controllers, Active Directory Domain Services (AD DS), and the basic objects stored inside Active Directory.

---

## What Is a Windows Domain?

A Windows domain is a centrally managed network of users and computers.

Instead of managing every computer separately, organizations can manage users, computers, permissions, and policies from a central system.

A simple way to think about it is:

`Domain = Centrally managed users and computers`

For example, in a university or company environment, a user may be able to sign in to different computers using the same username and password.

The account is not managed separately on every computer.

It is managed centrally through the domain environment.

---

# What Is Active Directory?

Active Directory is the central directory and management system used in a Windows domain environment.

The full service name is:

`Active Directory Domain Services (AD DS)`

Active Directory stores information about objects in the domain.

These objects can include:

- Users
- Computers
- Groups
- Organizational Units

A simple way to remember:

`Domain → Managed network`

`Active Directory → Central management system`

---

# What Is a Domain Controller?

A Domain Controller, or:

`DC`

is a Windows Server that runs Active Directory Domain Services.

It is responsible for important domain operations such as:

- Authenticating users
- Authenticating computers
- Managing directory information
- Applying domain policies
- Providing access to Active Directory data

A simple relationship is:

`Domain`

↓

`Domain Controller`

↓

`Active Directory`

↓

`Users + Computers + Groups + OUs`

---

# Authentication in a Domain

When a user enters a domain username and password, the credentials are checked through the domain environment.

Example concept:

`User enters credentials`

↓

`Domain Controller validates the account`

↓

`Authentication succeeds or fails`

This allows the same domain identity to be used across multiple domain-joined computers.

---

# Centralized Management

One of the main advantages of Active Directory is centralized administration.

An organization can centrally manage areas such as:

- User accounts
- Computer accounts
- Permissions
- Security groups
- Organizational Units
- Group Policies

For example, an organization may centrally prevent users from accessing certain Windows settings.

---

# Active Directory Objects

Active Directory stores different types of objects.

The main objects covered in my notes are:

- User
- Machine / Computer
- Security Group
- Organizational Unit

---

# User Object

A User object represents an account that can be authenticated in the domain.

A user may represent:

- A real employee
- An administrator
- A service account

Example:

`phillip`

A user account can be given permissions to access organizational resources.

---

## Service Accounts

Not every Active Directory user represents a real person.

An account can also be created for a service.

Examples mentioned in the notes include services such as:

- IIS
- MSSQL

These accounts are called:

`Service Accounts`

They allow services to operate using a specific identity and set of permissions.

---

# Computer / Machine Object

When a computer joins the domain, Active Directory creates an account for that computer.

A computer is therefore also treated as an identity inside the domain.

Machine accounts commonly end with:

`$`

Example:

`DC01`

may have an Active Directory machine account named:

`DC01$`

This helps Active Directory authenticate and manage domain-joined computers.

---

# Security Group

A Security Group is used to group accounts together so that permissions can be managed more easily.

Instead of giving the same permission separately to many users, an administrator can assign the permission to a group.

Example concept:

`Accounting Group`

↓

`Permission to access Accounting Folder`

Then users who are members of that group receive the group's access.

Simplified model:

`User → Security Group → Resource Permission`

---

# Important Active Directory Groups

Examples from my notes include:

## Domain Admins

Members have very high administrative privileges within the domain.

---

## Domain Users

Contains users belonging to the domain.

---

## Domain Computers

Contains domain computer accounts.

---

## Domain Controllers

Contains Domain Controller computer accounts.

---

## Backup Operators

Members can have broad permissions related to backup operations and accessing files for backup purposes.

---

# Organizational Unit — OU

An Organizational Unit is used to organize objects inside Active Directory.

OU stands for:

`Organizational Unit`

It can be thought of like an organizational folder inside the domain.

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

Employees and computers can be organized according to departments or administrative needs.

---

# Why OUs Are Useful

OUs are useful because administrators can apply different policies to different parts of the organization.

Example:

`Sales OU`

→ Specific Windows restrictions

`IT OU`

→ Different administrative or system policies

This allows the organization to manage different departments differently.

---

# Security Group vs OU

Security Groups and OUs have different purposes.

| Organizational Unit | Security Group |
|---|---|
| Organizes AD objects | Groups users or computers |
| Commonly used for policy application | Commonly used for permissions |
| Represents administrative structure | Represents access membership |

A simple way to remember:

`OU = Which policies apply?`

`Security Group = What can this account access?`

---

# Active Directory Structure

The basic structure from my notes can be represented as:

`Domain`

↓

`Domain Controller`

↓

`Active Directory`

↓

`Users / Computers / Groups`

↓

`Organizational Units`

This is the foundation for later topics such as:

- Delegation
- Group Policy
- Authentication
- Domain relationships

---

# Why Active Directory Matters in Cybersecurity

Active Directory controls many important parts of an enterprise Windows environment.

Examples include:

- Authentication
- User accounts
- Administrative privileges
- Computer accounts
- Permissions
- Organizational policies
- Access to resources

Because of this, understanding Active Directory is important for both:

- System administration
- Cybersecurity

---

# Quick Reference

| Term | Meaning |
|---|---|
| Domain | Centrally managed Windows network |
| Active Directory | Central directory and management system |
| AD DS | Active Directory Domain Services |
| Domain Controller | Server running AD DS |
| User Object | Domain user identity |
| Service Account | Account used by a service |
| Machine Account | Computer identity in Active Directory |
| `$` | Common ending for machine account names |
| Security Group | Group used for permission management |
| OU | Organizational Unit |
| Domain Admins | Highly privileged domain administrators |

---

## Key Takeaway

The most important relationship to remember is:

`Domain → Domain Controller → Active Directory → Users / Computers / Groups / OUs`

Active Directory provides centralized identity, organization, and management for Windows domain environments.
