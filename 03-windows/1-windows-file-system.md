# Windows File System

This page contains my notes on Windows file systems, NTFS features, Alternate Data Streams, and important Windows system directories.

---

## What Is a File System?

A file system determines how files and folders are stored, organized, and accessed on a disk.

Windows commonly uses:

`NTFS`

which stands for:

`New Technology File System`

Older or removable storage devices may also use:

- FAT16
- FAT32
- HPFS

---

# NTFS

NTFS is the main file system used by modern Windows systems.

It provides several features that older file systems such as FAT32 do not provide.

Important NTFS features include:

- Support for large files
- File and folder permissions
- Journaling
- File compression
- Encryption
- Alternate Data Streams (ADS)

---

# NTFS vs FAT32

| NTFS | FAT32 |
|---|---|
| Supports large files | Individual files are limited to 4 GB |
| Supports detailed permissions | Does not provide the same detailed permission system |
| Supports journaling | No journaling |
| Supports encryption | Does not provide the same encryption features |
| Supports compression | Does not provide the same compression features |
| Common on Windows system drives | Common on removable devices for compatibility |

For example, a file larger than 4 GB cannot normally be stored on a FAT32 file system.

---

# Journaling

NTFS is a journaling file system.

Journaling helps the file system keep track of changes.

If the system crashes or loses power, NTFS can use information stored in its journal to help recover the file system.

This makes NTFS more resilient than older FAT file systems.

---

# NTFS Permissions

NTFS allows permissions to be assigned to files and folders.

Permissions can control which users are allowed to:

- Read files
- Write files
- Modify files
- Execute files
- Delete files
- Access folders

This is important in Windows security because different users should not automatically have access to all files.

---

# File Compression

NTFS supports file and folder compression.

Compression reduces the amount of disk space used by files.

The file system can automatically decompress the data when it is accessed.

---

# EFS — Encrypting File System

NTFS supports encryption through:

`EFS`

which stands for:

`Encrypting File System`

EFS can encrypt files stored on NTFS.

The purpose is to prevent unauthorized users from reading protected files.

---

# Alternate Data Streams — ADS

ADS stands for:

`Alternate Data Streams`

ADS is a feature of NTFS that allows additional data streams to be attached to a file.

Normally, we think of a file as having one main piece of content.

For example:

`file.txt`

With ADS, additional data can be associated with the same file.

Example concept:

`file.txt:hidden`

Here:

- `file.txt` → main file
- `hidden` → alternate data stream

---

## Why ADS Exists

ADS can be used legitimately for storing additional information about a file.

Examples include:

- Metadata
- Application information
- Security information
- Information about where a file originated

---

# Zone.Identifier

When a file is downloaded from the Internet, Windows may attach information using an ADS called:

`Zone.Identifier`

This can identify that the file came from an external source such as the Internet.

This information can be used by Windows security features when deciding whether a warning should be shown.

---

# ADS and Cybersecurity

ADS is important in cybersecurity because the additional stream may not be obvious when viewing files normally.

It has been abused to hide:

- Text
- Scripts
- Commands
- Malicious content

Because of this, ADS may be examined during security investigations and digital forensics.

Important:

ADS itself is not malicious.

It is a legitimate NTFS feature that can also be abused.

---

# Windows Directory

The main Windows operating system directory is commonly:

`C:\Windows`

This directory contains many important Windows files and folders.

Although Windows is commonly installed under `C:\Windows`, the operating system directory does not technically have to be on the C drive.

---

# Environment Variable `%windir%`

Windows provides an environment variable for the Windows directory:

`%windir%`

Instead of manually assuming:

`C:\Windows`

the environment variable can be used.

Example:

`%windir%`

usually points to the Windows installation directory.

---

# Environment Variables

Environment variables store information about the Windows environment.

They can contain information such as:

- Operating system paths
- Temporary directory locations
- System directories
- Processor information

They allow applications and scripts to refer to system locations without hardcoding a specific path.

Example:

`%windir%`

represents the Windows directory.

---

# System32

One of the most important directories inside the Windows folder is:

`C:\Windows\System32`

System32 contains critical files used by the Windows operating system.

Many Windows utilities and system tools are stored here.

---

## Why System32 Is Important

System32 contains files required for Windows to operate.

These can include:

- System utilities
- Executable files
- Libraries
- Administrative tools
- Operating system components

Incorrectly deleting or modifying files inside System32 can cause Windows to stop working correctly.

Because of this, System32 should be treated as a critical system directory.

---

# File Systems and Cybersecurity

Understanding the Windows file system helps with several security topics.

Examples include:

- File permissions
- Access control
- Malware analysis
- Digital forensics
- Hidden data
- System file protection
- Privilege management

NTFS features such as permissions and ADS are especially relevant when investigating Windows systems.

---

# Quick Reference

| Term | Meaning |
|---|---|
| NTFS | New Technology File System |
| FAT32 | Older file system often used for removable storage |
| Journaling | Records file system changes to help recovery |
| EFS | Encrypting File System |
| ADS | Alternate Data Streams |
| `Zone.Identifier` | ADS used to store information about file origin |
| `C:\Windows` | Main Windows system directory |
| `%windir%` | Environment variable pointing to Windows directory |
| `C:\Windows\System32` | Critical Windows system directory |

---

## Key Takeaway

NTFS provides features that are important for both system management and cybersecurity.

The main concepts are:

`NTFS → Permissions + Journaling + Compression + Encryption + ADS`

Windows also depends heavily on critical system directories such as:

`C:\Windows`

and:

`C:\Windows\System32`
