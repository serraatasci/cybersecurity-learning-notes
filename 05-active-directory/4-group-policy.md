# Group Policy Objects (GPO)

This page contains my notes and hands-on practice on Group Policy Objects (GPOs) in Active Directory.

---

## What Is a Group Policy Object?

A Group Policy Object, or:

`GPO`

is a collection of settings that can be applied to users or computers in an Active Directory environment.

GPOs allow administrators to centrally control Windows behavior across many systems.

Examples include:

- Restricting Control Panel access
- Enforcing password policies
- Configuring security settings
- Automatically locking computers
- Applying settings to specific departments

---

# Where Can GPOs Be Linked?

A GPO can be linked to:

- An Organizational Unit (OU)
- The domain

Example:

`Sales OU`

→ Sales-specific user policies

`Workstations OU`

→ Workstation-specific computer policies

`thm.local`

→ Policies that can affect the domain and child OUs

---

# GPO and OU Relationship

A simple way to remember the relationship is:

`OU = Which users or computers are grouped together?`

`GPO = Which rules should be applied?`

`Link = Where is the GPO attached?`

Example:

`Sales OU`

↓

`Restrict Control Panel Access GPO`

↓

`Sales users receive the policy`

---

# GPO Inheritance

A GPO linked to a parent OU or domain can also apply to child OUs.

Example:

`thm.local`

↓

`Workstations`

`Servers`

`Domain Controllers`

If a policy is linked to:

`thm.local`

the child OUs can inherit that policy.

This makes it possible to apply common rules across the organization.

---

# Main GPO Configuration Areas

A GPO contains two main configuration sections:

- Computer Configuration
- User Configuration

---

# Computer Configuration

`Computer Configuration`

contains settings that apply to computers.

The policy is applied based on the computer object rather than the user who logs in.

Examples include:

- Computer security settings
- Machine inactivity settings
- System configuration
- Password-related policies

---

# User Configuration

`User Configuration`

contains settings that apply to user accounts.

The policy follows the user based on where the user is located in Active Directory.

Examples include:

- Control Panel restrictions
- Desktop settings
- User interface restrictions

---

# User Configuration vs Computer Configuration

A simple way to remember:

`User Configuration`

→ What should happen to this user?

`Computer Configuration`

→ What should happen to this computer?

---

# Password Policy Example

One policy path from my notes is:

`Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy`

From this area, administrators can configure settings such as:

- Minimum password length
- Password requirements

---

# Security Filtering

Security Filtering allows a GPO to be applied to only specific users or computers.

Without filtering, the policy may affect all relevant objects under the linked location.

A common default entry is:

`Authenticated Users`

Security Filtering can therefore be used to narrow the scope of the policy.

---

# Why Security Filtering Is Useful

Imagine a GPO is linked to an OU containing many users.

Only one specific group should receive the policy.

Instead of creating a completely separate Active Directory structure, Security Filtering can restrict which accounts receive the GPO.

Conceptually:

`GPO linked to OU`

↓

`Security Filtering`

↓

`Only selected users/computers receive policy`

---

# SYSVOL

GPO information is distributed through the Domain Controller's:

`SYSVOL`

share.

The path mentioned in my notes is:

`C:\Windows\SYSVOL\sysvol`

SYSVOL allows domain systems to access Group Policy information.

---

# Applying GPO Changes

Group Policy changes may not appear immediately on a computer.

To force a Group Policy update:

`gpupdate /force`

This requests that Group Policy settings be refreshed immediately.

---

# Hands-On Lab 1: Restrict Control Panel Access

One of my Active Directory labs involved creating a GPO that prevented selected departments from opening the Windows Control Panel.

The GPO was named:

`Restrict Control Panel Access`

---

## Policy Location

The policy was configured under:

`User Configuration`

The selected setting was:

`Prohibit access to Control Panel and PC settings`

Because this is a user-based restriction, it belongs under User Configuration.

---

## OU Links

The GPO was linked to:

- Marketing
- Management
- Sales

It was not linked to:

- IT

This meant users in the IT department were not affected by this restriction.

---

## Lab Logic

The goal was:

`Marketing / Management / Sales`

↓

`Control Panel blocked`

while:

`IT`

↓

`Control Panel still available`

This demonstrates how different departments can receive different Windows configurations using GPOs.

---

# Hands-On Lab 2: Automatic Screen Lock

The second GPO was used to automatically lock computers after a period of inactivity.

The GPO was named:

`Auto Lock Screen`

---

## Why This Is a Computer Policy

The automatic lock setting was configured as:

`Computer Configuration`

because the setting applies to the computer rather than a specific user's personal configuration.

---

## Inactivity Time

The inactivity period used in the lab was:

`5 minutes`

which equals:

`300 seconds`

The configured setting was:

`Interactive logon: Machine inactivity limit`

with:

`300`

seconds.

---

# Linking the Auto Lock GPO

The Auto Lock Screen GPO was linked directly to:

`thm.local`

This allowed child computer OUs to inherit the policy.

Examples included:

- Workstations
- Servers
- Domain Controllers

The simplified structure was:

`thm.local`

↓

`Auto Lock Screen`

↓

`Child OUs inherit policy`

---

# Why Automatic Locking Matters

An unlocked computer can create a security risk if the user leaves the workstation unattended.

Automatic locking helps reduce the chance that another person can access the active session.

Example:

`User leaves computer`

↓

`5 minutes inactivity`

↓

`Windows locks session`

↓

`Authentication required again`

---

# GPO Distribution Workflow

A simplified Group Policy workflow is:

1. Create the GPO
2. Configure the policy settings
3. Link the GPO to an OU or domain
4. Determine which users or computers should receive it
5. Use Security Filtering if necessary
6. Allow Group Policy to update
7. Use `gpupdate /force` when immediate testing is required
8. Verify the policy on the target system

---

# GPO Troubleshooting Mindset

If a Group Policy does not appear to work, useful questions include:

- Is the GPO linked to the correct OU or domain?
- Is the target user or computer inside that scope?
- Is this a User Configuration or Computer Configuration policy?
- Is Security Filtering preventing the policy?
- Has Group Policy refreshed yet?

For immediate testing:

`gpupdate /force`

can be used.

---

# GPO and Least Privilege

Group Policy also supports security by centrally enforcing rules instead of relying on each user to configure their own computer correctly.

For example:

`Company Security Requirement`

↓

`GPO`

↓

`Automatically applied to target systems`

This reduces inconsistent or insecure configurations.

---

# Why Group Policy Matters in Cybersecurity

GPOs can centrally enforce security controls across many Windows systems.

They can be used to manage areas such as:

- Password policies
- User restrictions
- Security options
- Computer behavior
- Access to Windows settings
- Automatic screen locking

Because of this, incorrect or overly broad GPO configuration can also have a large impact on an organization.

---

# Quick Reference

| Term | Meaning |
|---|---|
| GPO | Group Policy Object |
| User Configuration | Policies applied to users |
| Computer Configuration | Policies applied to computers |
| OU Link | Connects a GPO to an OU |
| Domain Link | Applies a GPO from the domain level |
| Inheritance | Child OUs receive parent-linked policies |
| Security Filtering | Limits which users/computers receive a GPO |
| SYSVOL | Domain share used to distribute Group Policy information |
| `gpupdate /force` | Force Group Policy refresh |
| Machine inactivity limit | Automatically lock an inactive computer |

---

## Key Takeaway

The easiest way to remember Group Policy is:

`OU = Who?`

`GPO = What rule?`

`Link = Where should the rule apply?`

`Security Filtering = Exactly who should receive it?`

`SYSVOL = How is the policy distributed?`

`gpupdate /force = Refresh it now`

My hands-on labs demonstrated both user-based and computer-based policies:

`Restrict Control Panel Access → User Configuration`

`Auto Lock Screen → Computer Configuration`
