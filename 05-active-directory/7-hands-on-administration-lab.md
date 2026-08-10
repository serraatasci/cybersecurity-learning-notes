# Active Directory Hands-On Administration Lab

This page documents a hands-on Active Directory administration lab that I completed in a controlled TryHackMe environment.

The goal of the lab was to reorganize an existing Active Directory structure, delegate a limited administrative task, and validate that the delegated permission worked correctly.

---

## Lab Objectives

The main objectives were:

- Review the existing Active Directory structure
- Remove an outdated Organizational Unit
- Delegate a specific administrative permission
- Apply the Principle of Least Privilege
- Test the delegated permission with the assigned user
- Reset a user's password using PowerShell
- Observe domain password policy enforcement
- Validate the result by logging in as the target user

---

# 1. Reviewing the Active Directory Structure

The first task was to compare the existing Active Directory structure with the organization's current structure.

An outdated department called:

`Research and Development`

still existed as an OU.

Because the department was no longer part of the organization, the OU needed to be removed.

---

# 2. Removing the Outdated OU

When I first attempted to delete the OU, Active Directory blocked the operation.

This happened because the OU was protected against accidental deletion.

The required workflow was:

`Active Directory Users and Computers`

↓

`View`

↓

`Advanced Features`

↓

`OU Properties`

↓

`Object`

↓

`Protect object from accidental deletion`

After disabling the protection, the outdated OU could be removed.

---

## What I Learned

Important Active Directory objects may be protected from accidental deletion.

This reduces the risk of an administrator unintentionally deleting an important OU.

---

# 3. Delegating Password Reset Permission

The next task involved an IT Support user named:

`Phillip`

Phillip needed to reset passwords for users inside the:

`Sales OU`

However, giving Phillip full Domain Administrator privileges would have been unnecessary.

Instead, I used:

`Delegation`

The workflow was:

`Sales OU`

↓

`Right Click`

↓

`Delegate Control`

↓

`Select Phillip`

↓

`Assign password reset permission`

---

# Principle of Least Privilege

This task demonstrated the:

`Principle of Least Privilege`

Phillip received only the permission required for his support task.

He did not receive full control of the domain.

The permission model was:

`Phillip`

↓

`Sales OU`

↓

`Password Reset Permission`

Instead of:

`Phillip`

↓

`Domain Admin`

---

# 4. Testing with Phillip's Account

After completing the delegation, I needed to verify that the permission actually worked.

Testing the operation while logged in as a Domain Administrator would not prove this, because Domain Administrators already have the required privileges.

Therefore, I connected using Phillip's domain account.

The domain login format was:

`THM\phillip`

This allowed me to perform the next steps using Phillip's actual delegated privileges.

---

# 5. Resetting Sophie's Password with PowerShell

Phillip did not have sufficient privileges to perform the task through Active Directory Users and Computers.

Therefore, PowerShell was used.

The password reset command used in the lab was:

`Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose`

Important parts:

`Set-ADAccountPassword`

→ Active Directory PowerShell command used to change or reset a password

`sophie`

→ Target user

`-Reset`

→ Resets the password without requiring the current password

`Read-Host -AsSecureString`

→ Allows the new password to be entered securely

---

# 6. Troubleshooting Access Denied

During the first attempt, PowerShell returned:

`Access is denied`

This showed that Phillip did not yet have the correct delegated permission.

I returned to the Active Directory delegation settings and corrected the permission assignment.

After the delegation was configured correctly, the password reset operation was allowed.

---

## What I Learned

Active Directory enforces delegated permissions.

If a user does not have the required permission, the operation is blocked even if the correct PowerShell command is used.

This helped demonstrate the relationship between:

`Command`

and:

`Authorization`

Knowing the command is not enough.

The account must also have permission to perform the action.

---

# 7. Domain Password Policy

During the password reset process, one attempted password was rejected.

Windows returned an error similar to:

`The password does not meet the length, complexity, or history requirement`

This demonstrated that the domain had a:

`Password Policy`

The password needed to satisfy the domain's configured requirements.

The lab demonstrated rules related to:

- Password length
- Password complexity
- Password history

After entering a stronger password that met the policy, the reset succeeded.

---

# 8. Change Password at Next Logon

After resetting Sophie's password, I configured the account so that Sophie would need to change the temporary password after logging in.

The command used was:

`Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose`

The intended workflow was:

`IT Support resets password`

↓

`Temporary password is given to user`

↓

`User logs in`

↓

`User creates a new private password`

This reduces the amount of time that the support employee knows the user's password.

---

# 9. RDP and NLA Issue

During the controlled lab, enabling:

`ChangePasswordAtLogon = True`

caused an issue with the RDP login process and Network Level Authentication.

To continue testing the lab, the setting was temporarily changed to:

`Set-ADUser -ChangePasswordAtLogon $false -Identity sophie -Verbose`

This allowed the final login test to continue.

---

# 10. Final Validation

The final step was to log in using Sophie's domain account.

The login format was:

`THM\sophie`

Successful authentication confirmed that:

- Phillip's delegation worked
- The password reset succeeded
- The new password satisfied the domain policy
- Sophie could authenticate using the updated credentials

---

# Full Lab Workflow

The complete lab can be summarized as:

`Review AD structure`

↓

`Remove outdated OU`

↓

`Delegate password reset permission to Phillip`

↓

`Log in as Phillip`

↓

`Attempt password reset`

↓

`Troubleshoot Access Denied`

↓

`Correct delegation`

↓

`Reset Sophie's password`

↓

`Password policy enforced`

↓

`Configure password change behavior`

↓

`Log in as Sophie`

↓

`Validate success`

---

# Key Security Concepts Demonstrated

This lab combined several important Active Directory security concepts.

---

## Organizational Units

OUs were used to represent the organizational structure and define the scope of delegated administration.

---

## Delegation

A specific task was assigned to another user without giving full administrative privileges.

---

## Least Privilege

Phillip only received the permissions required for his job.

---

## Authorization

The `Access is denied` error demonstrated that administrative actions depend on the account's permissions.

---

## Password Policy

The Domain Controller enforced password security requirements even during an administrator-assisted password reset.

---

## PowerShell Administration

Active Directory PowerShell commands were used to perform account-management tasks.

---

## Validation

The final login test verified that the administrative operation had actually succeeded.

---

# Troubleshooting Summary

| Problem | Cause / Lesson |
|---|---|
| OU could not be deleted | Accidental deletion protection was enabled |
| `Access is denied` | Delegation permission was not correctly assigned |
| Password rejected | Domain password policy was enforced |
| RDP login issue | Change-password-at-logon interacted with NLA in the lab |
| Need to verify delegation | Test using Phillip instead of Domain Administrator |

---

# Commands Used

Password reset:

`Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose`

Require password change:

`Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose`

Temporary lab adjustment:

`Set-ADUser -ChangePasswordAtLogon $false -Identity sophie -Verbose`

---

# Skills Practiced

Through this lab, I practiced:

- Active Directory Users and Computers
- OU management
- Delegation of Control
- Principle of Least Privilege
- Domain user authentication
- PowerShell for Active Directory
- Password policy troubleshooting
- RDP-based validation
- Permission troubleshooting

---

## Key Takeaway

The most important lesson from this lab was:

`Administrative access should be scoped to the exact task required.`

Instead of giving Phillip broad Domain Administrator privileges, I delegated only the password-reset permission required for the Sales OU and verified that the permission worked using his own account.

This demonstrated how Active Directory can distribute administrative responsibilities while maintaining access control.
