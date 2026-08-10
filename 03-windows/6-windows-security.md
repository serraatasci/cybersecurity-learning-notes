# Windows Security

This page contains my notes on the built-in Windows security features used to protect the device, applications, network connections, and stored data.

---

## Windows Security

Windows Security is the central place where built-in Windows protection features are managed.

The main protection areas covered in my notes are:

- Virus & threat protection
- Firewall & network protection
- App & browser control
- Device security

Windows Security also displays status indicators.

---

## Security Status Colors

Windows Security can use colors to show the current security status.

- Green → No major issue detected
- Yellow → A security recommendation or issue should be reviewed
- Red → A security issue requires immediate attention

---

# Virus & Threat Protection

Virus & Threat Protection is the Windows Security area related to malware protection.

Microsoft Defender can scan files and monitor the system for malicious activity.

---

## Scan Types

### Quick Scan

Checks locations where threats are commonly found.

This is faster than scanning the entire system.

---

### Full Scan

Checks all files and running programs.

This takes longer but provides a more complete scan.

---

### Custom Scan

Allows the user to choose a specific:

- File
- Folder
- Location

to scan.

---

# Threat History

Windows Security can show information about previously detected threats.

Important areas include:

- Last scan
- Quarantined threats
- Allowed threats

---

## Quarantine

When a threat is quarantined, it is isolated so that it cannot normally continue running.

Conceptually:

`Threat Detected`

↓

`Threat Isolated`

↓

`Execution Prevented`

---

## Allowed Threats

A detected item can sometimes be manually allowed by the user.

This means Windows Defender detected the item but the user chose to allow it.

This should only be done when the file is known to be safe.

---

# Real-Time Protection

Real-time protection continuously monitors files and programs.

Its purpose is to detect and block malware when it attempts to:

- Download
- Install
- Execute
- Modify the system

A simplified idea is:

`File or Program Activity`

↓

`Defender Checks It`

↓

`Allow or Block`

---

# Cloud-Delivered Protection

Cloud-based protection allows Defender to use current threat information from Microsoft.

This can help Windows respond more quickly to newly identified threats.

---

# Automatic Sample Submission

Windows Defender may send suspicious file samples to Microsoft for analysis.

This can help improve malware detection.

---

# Controlled Folder Access

Controlled Folder Access helps protect important folders from unauthorized modification.

It is especially useful against ransomware.

Ransomware often attempts to encrypt files such as:

- Documents
- Pictures
- Work files
- Personal data

Controlled Folder Access can restrict which applications are allowed to modify protected folders.

---

# Exclusions

Defender allows certain files, folders, or processes to be excluded from scanning.

These are called:

`Exclusions`

An excluded item is not checked normally by Defender.

Because exclusions reduce protection, they should be used carefully.

---

# Defender Updates

Microsoft Defender relies on current threat information.

Windows Security provides an option to check for updates.

Keeping Defender updated helps it recognize newer malware.

---

# Scanning a Single File

A file can be scanned directly from Windows Explorer.

Example workflow:

`Right Click File`

↓

`Scan with Microsoft Defender`

This is useful when checking a suspicious downloaded file.

---

# Firewall & Network Protection

A firewall controls network traffic entering and leaving a computer.

Its purpose is to decide which network connections should be:

- Allowed
- Blocked

A simplified concept is:

`Network Traffic`

↓

`Firewall Rules`

↓

`Allow or Block`

---

# Windows Firewall Profiles

Windows Firewall provides three main network profiles.

---

## Domain Profile

Used when the computer is connected to a domain-based corporate network.

Example:

`Company Computer → Corporate Domain`

---

## Private Profile

Used for trusted networks.

Examples:

- Home network
- Trusted office network

---

## Public Profile

Used for untrusted or public networks.

Examples:

- Café Wi-Fi
- Airport Wi-Fi
- Hotel Wi-Fi

Public networks generally require more restrictive protection.

---

# Why Firewall Profiles Exist

The same computer may connect to very different networks.

For example:

`Home Network`

and:

`Airport Wi-Fi`

should not necessarily use exactly the same security rules.

Profiles allow Windows to apply different firewall behavior based on the network type.

---

# App & Browser Control

App & Browser Control protects against threats that may come from applications, files, websites, and downloads.

One important Windows feature in this area is:

`Microsoft Defender SmartScreen`

---

# Microsoft Defender SmartScreen

SmartScreen checks applications, websites, and downloaded files for suspicious or potentially malicious content.

It can help protect against:

- Phishing websites
- Malicious downloads
- Suspicious applications
- Unrecognized software

---

## Example

A user downloads an unknown executable file.

SmartScreen may check its reputation.

Conceptually:

`Downloaded Application`

↓

`SmartScreen Reputation Check`

↓

`Known / Trusted`

or

`Unknown / Suspicious`

↓

`Warning May Be Displayed`

---

# Exploit Protection

Exploit Protection provides defenses against techniques used to exploit software vulnerabilities.

Important protections in my notes include:

- CFG
- DEP
- ASLR

---

# CFG — Control Flow Guard

CFG stands for:

`Control Flow Guard`

It helps protect applications against attacks that try to redirect program execution to unexpected locations.

The goal is to make it harder for malicious code to manipulate the normal control flow of a program.

---

# DEP — Data Execution Prevention

DEP stands for:

`Data Execution Prevention`

DEP helps prevent code from executing in memory regions that are intended to contain data rather than executable instructions.

Simplified concept:

`Data Memory`

should not normally become:

`Executable Code`

This helps reduce certain memory-based attacks.

---

# ASLR — Address Space Layout Randomization

ASLR stands for:

`Address Space Layout Randomization`

It randomizes where certain program components are loaded into memory.

Instead of always loading important components at predictable memory addresses, Windows can change their locations.

This makes exploitation more difficult because attackers cannot easily predict memory locations.

---

# CFG vs DEP vs ASLR

A simple way to remember them:

`CFG`

→ Protects program control flow

`DEP`

→ Prevents execution from data memory

`ASLR`

→ Randomizes memory locations

Together, they make exploitation more difficult.

---

# Device Security

Device Security focuses on hardware-supported and low-level Windows protection mechanisms.

Important concepts include:

- Core Isolation
- Memory Integrity
- TPM

---

# Core Isolation

Core Isolation helps protect critical Windows processes by separating them from the normal operating environment.

This creates a more protected area for sensitive system components.

---

# Memory Integrity

Memory Integrity is part of Core Isolation.

It helps prevent malicious code from being injected into highly protected processes.

Simplified idea:

`Critical Windows Process`

↓

`Protected Environment`

↓

`Malicious Code Injection Becomes More Difficult`

---

# TPM — Trusted Platform Module

TPM stands for:

`Trusted Platform Module`

A TPM is a hardware-based security component.

It is designed to support secure cryptographic operations.

---

## TPM Functions

TPM can help protect:

- Encryption keys
- Cryptographic information
- Authentication-related secrets

Because TPM is hardware-based, sensitive security operations can be separated from normal software.

---

## Why TPM Matters

If important security keys were stored only as normal files, malware could potentially attempt to access them.

TPM provides a more protected hardware-based location for sensitive cryptographic material.

A simple way to remember:

`TPM = Hardware Security for Cryptographic Keys`

---

# Memory Integrity vs TPM

These two features protect different things.

`Memory Integrity`

→ Helps protect critical processes against malicious code injection

`TPM`

→ Provides hardware-based protection for cryptographic operations and keys

---

# BitLocker

BitLocker is the Windows disk encryption feature.

Its purpose is to protect data stored on a drive.

---

## Why BitLocker Is Important

Imagine a laptop is stolen.

Without disk encryption, an attacker might remove the drive and attempt to read the files from another computer.

BitLocker encrypts the data stored on the drive.

Conceptually:

`Physical Access to Disk`

does not automatically mean:

`Access to Data`

---

# BitLocker and TPM

BitLocker can work together with TPM.

TPM can help protect the encryption keys used by BitLocker.

It can also help detect certain unauthorized changes to the system before releasing protected key material.

Simplified relationship:

`BitLocker`

→ Encrypts the drive

`TPM`

→ Helps protect the encryption keys

---

# BitLocker Without TPM

The notes also mention that systems without a compatible TPM may use another startup method.

For example, a removable USB device may contain the startup key.

This allows BitLocker to protect systems that do not use TPM in the normal way.

---

# Volume Shadow Copy Service — VSS

VSS stands for:

`Volume Shadow Copy Service`

VSS can create a snapshot of data at a specific point in time.

This snapshot is also called a:

`Shadow Copy`

---

## What Can VSS Be Used For?

VSS can support:

- Restore points
- System Restore
- Previous versions of files
- Backup operations

Conceptually:

`Current System State`

↓

`Snapshot`

↓

`Possible Recovery Point`

---

# System Volume Information

Shadow copies related to protected drives may be stored in:

`System Volume Information`

This is a protected Windows system location.

---

# VSS and Ransomware

VSS is important in cybersecurity because shadow copies may help recover files after data loss.

However, ransomware may attempt to delete shadow copies to make recovery more difficult.

Conceptually:

`Ransomware`

↓

`Encrypt Files`

+

`Delete Shadow Copies`

↓

`Recovery Becomes Harder`

Because of this, VSS-related activity may be relevant during ransomware investigations.

---

# Windows Security as Defense in Depth

Windows does not rely on only one security feature.

Different controls protect different parts of the system.

Example:

`Microsoft Defender`

→ Malware protection

`Firewall`

→ Network protection

`SmartScreen`

→ Reputation and application/browser protection

`Exploit Protection`

→ Memory exploitation defenses

`Core Isolation`

→ Critical process protection

`TPM`

→ Hardware-based cryptographic security

`BitLocker`

→ Disk encryption

`VSS`

→ Snapshot and recovery support

This is an example of:

`Defense in Depth`

Multiple security layers work together instead of depending on one single control.

---

# Quick Reference

| Feature | Purpose |
|---|---|
| Microsoft Defender | Malware detection and protection |
| Quick Scan | Scan common threat locations |
| Full Scan | Scan the whole system |
| Custom Scan | Scan selected locations |
| Quarantine | Isolate detected threats |
| Real-Time Protection | Monitor files and programs continuously |
| Controlled Folder Access | Protect folders from unauthorized changes |
| Firewall | Control network traffic |
| Domain Profile | Corporate domain network |
| Private Profile | Trusted network |
| Public Profile | Untrusted network |
| SmartScreen | Check suspicious apps, websites, and downloads |
| CFG | Protect program control flow |
| DEP | Prevent execution from data memory |
| ASLR | Randomize memory locations |
| Core Isolation | Isolate critical Windows processes |
| Memory Integrity | Protect critical processes from malicious code injection |
| TPM | Hardware-based cryptographic protection |
| BitLocker | Disk encryption |
| VSS | Create shadow copies / snapshots |

---

## Key Takeaway

Windows security uses several protection layers.

A useful way to remember the overall structure is:

`Malware → Defender`

`Network → Firewall`

`Apps & Downloads → SmartScreen`

`Memory Exploitation → CFG + DEP + ASLR`

`Critical Processes → Core Isolation`

`Cryptographic Keys → TPM`

`Stored Data → BitLocker`

`Recovery → VSS`

Together, these features create multiple layers of protection across the Windows system.
