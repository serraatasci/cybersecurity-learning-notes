# Delegation and Principle of Least Privilege

This page contains my notes and hands-on practice on Active Directory delegation, password reset permissions, and the Principle of Least Privilege.

---

## What Is Delegation?

Delegation means giving a user permission to perform a specific administrative task without making that user a full Domain Administrator.

In Active Directory, this allows administrative responsibilities to be distributed safely.

Example:

An IT Support employee may need to reset user passwords.

Instead of making the employee a Domain Admin, I can give that user permission to reset passwords only inside a specific Organizational Unit.

This is called:

`Delegation`

---

# Why Delegation Is Important

Without delegation, organizations might give users more privileges than they actually need.

For example:

`IT Support User`

does not necessarily need:

`Full Domain Admin Access`

Instead, the user may only need:

`Reset Password Permission`

for:

`Sales OU`

This reduces unnecessary administrative privilege.

---

# Principle of Least Privilege

The Principle of Least Privilege means:

A user should only receive the minimum permissions required to perform their job.

A simplified idea is:

`Required Task`

↓

`Minimum Necessary Permission`

↓

`No Additional Administrative Rights`

---

## Example

In my lab, Phillip was an IT Support user.

Phillip needed to reset passwords for users inside the Sales department.

I did not make Phillip a member of:

`Domain Admins`

Instead, I delegated only the required permission.

The result was:

`Phillip`

↓

`Sales OU`

↓

`Reset Password Permission`

Phillip could perform the required support task without gaining control over the entire domain.

---

# Delegating Password Reset Permission

In the lab, the delegation workflow was:

`Sales OU`

↓

`Right Click`

↓

`Delegate Control`

↓

`Select Phillip`

↓

`Choose password reset permission`

This allowed Phillip to reset passwords for users inside the Sales OU.

---

## Selecting the User

When selecting the delegated user, I entered:

`phillip`

and used:

`Check Names`

Windows then resolved the username to the correct Active Directory account.

Using the correct account name is important when assigning delegation.

---

# Testing the Delegation

After delegating the permission, I did not continue using the Domain Administrator account.

Instead, I connected using Phillip's own domain account.

The purpose was to verify that the delegated permission actually worked.

The login format used in the lab was:

`THM\phillip`

This identifies Phillip as a user in the THM domain.

---

# Why Test as Phillip?

If I reset Sophie's password while still logged in as Domain Administrator, the test would not prove that delegation was working.

A Domain Administrator already has enough privilege to perform the task.

Therefore, I needed to:

1. Log in as Phillip
2. Perform the password reset
3. Verify that Phillip could complete only the delegated task

This demonstrates that the permission was correctly assigned.

---

# Using PowerShell

Phillip did not have the privileges required to use Active Directory Users and Computers for administrative actions.

Therefore, I used PowerShell to perform the password reset.

The command structure used in the lab was:

`Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose`

The important parts are:

`Set-ADAccountPassword`

→ Active Directory PowerShell command used to change or reset an account password

`sophie`

→ Target user

`-Reset`

→ Resets the password without requiring the current password

`-NewPassword`

→ Specifies the new password

`Read-Host -AsSecureString`

→ Allows the password to be entered without displaying it as normal text

---

# Access Denied During Testing

During the first attempt, I received:

`Access is denied`

This happened because Phillip's delegation permission had not been configured correctly.

After correcting the delegation settings, the password reset command worked.

This was useful because it demonstrated that Active Directory actually enforces the delegated permission.

Without the correct permission, Phillip could not perform the operation.

---

# Password Policy

During the password reset, one password was rejected with an error similar to:

`The password does not meet the length, complexity, or history requirement`

This showed that the domain had a:

`Password Policy`

The new password had to satisfy the rules configured in the domain.

These rules included requirements related to:

- Password length
- Complexity
- Password history

After using a password that met the policy, the reset succeeded.

---

# Force Password Change at Next Logon

After resetting Sophie's password, the next step was to require Sophie to change it when she logged in.

The command used was:

`Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose`

This sets:

`ChangePasswordAtLogon = True`

The idea is:

`IT Support creates temporary password`

↓

`User logs in`

↓

`User creates their own password`

This is more secure because the support employee does not continue to know the user's permanent password.

---

# RDP / NLA Issue in the Lab

In the lab environment, forcing the password change at next logon caused an issue with RDP and Network Level Authentication.

Because of this, the setting was temporarily changed to:

`Set-ADUser -ChangePasswordAtLogon $false -Identity sophie -Verbose`

This was done only to continue the controlled lab and verify the account login.

---

# Final Validation

The final step was to log in using Sophie's domain account:

`THM\sophie`

This confirmed that the password reset had succeeded.

The complete lab workflow was:

`Domain Administrator`

↓

`Delegated password reset permission to Phillip`

↓

`Phillip logged in using his own account`

↓

`Phillip reset Sophie's password`

↓

`Domain password policy was enforced`

↓

`Sophie logged in using the new password`

---

# What This Lab Demonstrated

This lab demonstrated several important Active Directory concepts together:

- Organizational Units
- Delegation
- Password reset permissions
- Domain accounts
- PowerShell administration
- Password policy enforcement
- RDP authentication
- Principle of Least Privilege
- Permission testing

---

# Why Least Privilege Matters in Cybersecurity

Giving every support employee Domain Admin access would create unnecessary risk.

If one of those accounts were compromised, an attacker could potentially gain very broad control over the domain.

Delegation reduces this risk by limiting permissions.

Instead of:

`User → Full Administrative Access`

the safer model is:

`User → Specific Task → Specific OU`

---

# Delegation vs Domain Admin

| Delegated User | Domain Admin |
|---|---|
| Receives specific permissions | Has very broad domain permissions |
| Scope can be limited to an OU | Can manage the entire domain |
| Better for support tasks | Used for high-level administration |
| Supports Least Privilege | High-value privileged account |

---

# Troubleshooting Lessons from the Lab

The lab also showed several useful troubleshooting lessons.

## 1. Access Denied

If the delegated permission is not configured correctly, the operation fails.

This confirms that permissions are actually being enforced.

---

## 2. Password Policy Error

Even an authorized password reset must follow the domain's password policy.

Permission to reset a password does not mean the new password can ignore security requirements.

---

## 3. Test with the Delegated Account

Always test delegated permissions using the account that received the permission.

Testing with Domain Administrator would not verify the delegation.

---

## 4. Validate the Final User Login

A password reset is not fully validated until the target user can successfully authenticate using the new password.

---

# Quick Reference

| Term | Meaning |
|---|---|
| Delegation | Giving a user a specific administrative permission |
| Least Privilege | Giving only the minimum required permissions |
| Domain Admin | Highly privileged domain administrator |
| `Delegate Control` | Active Directory delegation wizard |
| `Set-ADAccountPassword` | PowerShell command for password reset |
| `-Reset` | Reset password without knowing the current password |
| `Set-ADUser` | PowerShell command for modifying AD users |
| `ChangePasswordAtLogon` | Force user to change password at next login |
| Password Policy | Rules controlling acceptable passwords |
| `Access is denied` | Operation blocked because required permission is missing |

---

## Key Takeaway

The main idea of this lab was:

`Do not give full administrative access when a smaller permission is enough.`

Instead:

`Delegate the exact task to the exact user for the exact scope required.`

This is the practical meaning of the Principle of Least Privilege in Active Directory.
