# Active Directory

This section contains my Active Directory learning notes and hands-on practice in a Windows domain environment.

---

## Topics

- Active Directory fundamentals
- Domain Controllers
- Users and computer accounts
- Security groups
- Organizational Units (OUs)
- User and OU management
- Delegation of administrative tasks
- Principle of Least Privilege
- Group Policy Objects (GPOs)
- Kerberos authentication
- NetNTLM authentication
- Trees and forests
- Trust relationships
- Hands-on Active Directory administration labs

---

## What Is Active Directory?

Active Directory is a directory service used to centrally manage users, computers, groups, and policies in Windows domain environments.

Instead of managing every computer separately, administrators can use Active Directory to centrally control the environment.

A simplified structure is:

`Domain`

↓

`Domain Controller`

↓

`Active Directory`

↓

`Users + Computers + Groups + OUs`

---

## Why Active Directory Matters in Cybersecurity

Active Directory is widely used in enterprise Windows environments.

It controls important areas such as:

- Authentication
- User accounts
- Computer accounts
- Permissions
- Administrative privileges
- Security policies
- Access to organizational resources

Because of this, Active Directory security is an important part of enterprise cybersecurity.

---

## Learning Approach

These notes are based on my hands-on work in controlled cybersecurity lab environments.

My goal is to understand both:

- How Active Directory is administered
- How its security model works

The hands-on exercises in this section include managing Organizational Units, delegating permissions, applying Group Policies, and testing user access in a domain environment.
