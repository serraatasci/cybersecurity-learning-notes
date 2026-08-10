# Windows Users, Profiles, and UAC

This page contains my notes on Windows user accounts, user profiles, local users and groups, permissions, and User Account Control (UAC).

---

## Windows User Account Types

On a typical local Windows system, user accounts generally fall into two main categories:

- Administrator
- Standard User

The account type determines what actions the user can perform on the system.

---

# Administrator Account

An Administrator account has elevated privileges.

An administrator can perform actions such as:

- Add users
- Remove users
- Change user account types
- Modify groups
- Install applications
- Change system settings
- Perform administrative tasks

Administrator privileges should be used carefully because changes can affect the entire system.

---

# Standard User

A Standard User has more limited permissions.

A standard user can usually:

- Access their own files
- Modify files they have permission to access
- Use installed applications
- Change some personal settings

A standard user normally cannot perform system-level actions such as:

- Installing system-wide software
- Creating or deleting other users
- Changing important system settings

This separation helps reduce the risk of unauthorized or accidental system changes.

---

# Viewing Other Users

Windows provides several ways to view user accounts.

One method is through:

`Settings > Accounts > Other users`

An administrator may see options such as:

- Add another user
- Change account type
- Remove account

Standard users normally have fewer administrative options.

---

# Local Users and Groups

Windows provides a management console called:

`lusrmgr.msc`

which stands for:

`Local Users and Groups`

It can be opened through the Run dialog.

Press:

`Win + R`

Then enter:

`lusrmgr.msc`

---

## What Can Be Managed with `lusrmgr.msc`?

The tool contains two main sections:

- Users
- Groups

The Users section displays local user accounts.

The Groups section displays local security groups.

---

# Local Users

A local user account exists on a specific Windows computer.

It can have properties such as:

- Username
- Password
- Group membership
- Account status
- Password settings

Examples of local accounts may include:

- Administrator
- Guest
- Normal user accounts

---

# Local Groups

Groups make permission management easier.

Instead of assigning permissions separately to every user, users can be added to a group.

Permissions can then be assigned to that group.

Example concept:

`User → Group → Permissions`

---

## Administrators Group

Users who belong to the local:

`Administrators`

group have elevated privileges on that Windows machine.

---

## Users Group

Normal local users are commonly members of the:

`Users`

group.

They have more restricted access than administrators.

---

# User Profiles

When a user logs into Windows, the operating system creates or uses a user profile.

User profiles are commonly stored under:

`C:\Users`

Example:

`C:\Users\Serra`

A user profile can contain folders such as:

- Desktop
- Documents
- Downloads
- Pictures

It also stores user-specific settings and application data.

---

# Permissions

Different users may have different permissions on files and folders.

Permissions determine whether a user can perform actions such as:

- Read
- Write
- Modify
- Execute
- Delete

Windows uses user and group permissions to control access to resources.

---

# Principle of Least Privilege

A useful security principle is:

`Principle of Least Privilege`

This means a user should only receive the permissions required to perform their task.

For example:

A normal user who only needs to browse the web and edit documents does not normally need Administrator privileges.

Reducing unnecessary privileges limits the amount of damage that can occur if an account or application is compromised.

---

# UAC — User Account Control

UAC stands for:

`User Account Control`

UAC helps control when applications or users attempt to perform actions that require elevated privileges.

An Administrator account does not automatically run every application with full administrative privileges.

When a higher level of privilege is required, Windows can display a UAC prompt.

---

## Why UAC Exists

UAC helps prevent applications from silently making important system changes.

For example, an application may require elevated privileges to:

- Install software
- Modify protected system files
- Change system-wide settings

Windows can ask the user for confirmation before allowing the action.

---

# UAC Prompt for an Administrator

When an administrator attempts an action requiring higher privileges, UAC may ask for confirmation.

The user can choose whether to allow the operation.

Conceptually:

`Application requests elevated privilege`

↓

`UAC prompt`

↓

`User approves or denies`

↓

`Action continues or stops`

---

# UAC Prompt for a Standard User

A Standard User does not have administrative privileges.

If an application requires administrator access, Windows may request credentials for an administrator account.

Without valid administrative credentials, the action cannot continue.

For example, attempting to install certain applications may trigger this prompt.

---

# UAC Shield Icon

Some Windows applications or settings display a shield icon.

The shield indicates that the action may require elevated administrative privileges.

It is a visual indicator that UAC may appear when the action is started.

---

# UAC Notification Levels

Windows provides four main UAC notification levels.

---

## 1. Always Notify

This is the highest notification level.

Windows notifies the user when:

- Applications attempt to make system changes
- The user attempts to change Windows settings

The desktop is dimmed and the UAC prompt appears on the Secure Desktop.

---

## 2. Notify Only When Apps Try to Make Changes

This is generally the default UAC level.

Windows notifies the user when applications attempt to make system changes.

When the user personally changes certain Windows settings, a prompt may not appear.

The desktop is dimmed when the UAC prompt appears.

---

## 3. Notify for Apps but Do Not Dim the Desktop

This is similar to the previous level, but the desktop is not dimmed.

The UAC prompt appears on the normal desktop.

This is less secure than using the Secure Desktop because other running applications exist in the same desktop environment.

---

## 4. Never Notify

UAC notifications are disabled.

Windows does not prompt when applications or the user make system changes.

This is the least secure option of the four.

---

# UAC Security Level Overview

From more secure to less secure:

`Always Notify`

↓

`Notify for Applications + Secure Desktop`

↓

`Notify for Applications Without Secure Desktop`

↓

`Never Notify`

---

# Secure Desktop

When a UAC prompt appears and the rest of the screen becomes darker, Windows has switched to:

`Secure Desktop`

The Secure Desktop creates a more protected environment for the UAC decision.

Its purpose includes making it more difficult for other applications to interfere with the UAC prompt.

---

## Why Secure Desktop Matters

The Secure Desktop helps reduce risks such as:

- Fake UAC prompts
- Other applications attempting to interact with the prompt
- Applications capturing user interaction with the approval window

The user can then make the approval decision in a more isolated environment.

---

# UAC and Malware

UAC does not replace antivirus or other security controls.

However, it provides an additional security layer.

If malware attempts to perform an action that requires elevated privileges, UAC may prevent the action from occurring silently.

This can reduce the ability of malicious software to modify important parts of the system without user approval.

---

# UAC and Built-in Administrator

The Windows notes also highlight that UAC behavior can differ for the built-in local Administrator account.

In the lab environment, UAC was not applied to the built-in local Administrator account in the same way as normal Administrator-type user accounts.

This is one reason why the built-in Administrator account should be treated carefully.

---

# Users, Groups, and UAC Together

These concepts work together to control access.

A simplified model is:

`User Account`

↓

`Group Membership`

↓

`Permissions`

↓

`UAC when elevation is required`

For example:

A Standard User may have permission to open an application.

However, if that application needs to modify protected Windows settings, administrative elevation may still be required.

---

# Why This Matters in Cybersecurity

User accounts and privilege management are important because attackers often try to gain higher privileges after obtaining access to a system.

Understanding:

- Administrator accounts
- Standard users
- Groups
- Permissions
- UAC

helps explain how Windows limits access and how privilege escalation relates to system security.

---

# Quick Reference

| Term | Meaning |
|---|---|
| Administrator | User with elevated system privileges |
| Standard User | User with limited system privileges |
| `lusrmgr.msc` | Local Users and Groups management console |
| `C:\Users` | Default location for user profiles |
| UAC | User Account Control |
| Secure Desktop | Protected environment used for UAC prompts |
| Administrators | Local group with administrative privileges |
| Users | Common group for standard users |
| Least Privilege | Give users only the permissions they need |

---

## Key Takeaway

Windows access control can be simplified as:

`Users + Groups + Permissions + UAC`

Administrator accounts can make system-level changes, while Standard Users operate with more restricted permissions.

UAC adds another layer by requiring approval or administrative credentials when elevated privileges are needed.
