# Windows Command Line and Registry

This page contains my notes on basic Windows Command Prompt usage and the Windows Registry.

---

## Command Prompt

Command Prompt is the traditional Windows command-line interface.

It can be opened by running:

`cmd`

Command Prompt allows users and administrators to interact with Windows using text-based commands.

---

# `hostname`

The `hostname` command displays the name of the computer.

Example:

`hostname`

Possible output:

`DESKTOP-ABC123`

This is useful when identifying which Windows machine I am currently working on.

---

# `whoami`

The `whoami` command displays the currently logged-in user.

Example:

`whoami`

Possible output:

`thm\administrator`

This shows both:

- Domain or computer name
- Username

---

## Why `whoami` Is Useful

It helps confirm:

- Which account is active
- Whether I am using a domain account
- Which security context I am working under

This is especially useful in Windows labs and Active Directory environments.

---

# `ipconfig`

The `ipconfig` command displays network configuration information.

Example:

`ipconfig`

It can show information such as:

- IPv4 address
- Subnet mask
- Default gateway
- Network adapter information

---

## `ipconfig /all`

For more detailed information:

`ipconfig /all`

This can include:

- MAC address
- DHCP information
- DNS servers
- Hostname
- Adapter details

---

# `netstat`

The `netstat` command displays information about network connections.

Example:

`netstat`

It can show active network connections.

---

## `netstat -ano`

A commonly useful form is:

`netstat -ano`

This can display:

- Active connections
- Listening ports
- Local addresses
- Remote addresses
- Process IDs

The process ID can then be compared with running processes.

---

## Why `netstat` Matters in Cybersecurity

It can help identify:

- Unexpected network connections
- Listening services
- Remote connections
- Processes communicating over the network

This can be useful during troubleshooting and security investigations.

---

# `net`

The `net` command is a general Windows administration command.

It contains several subcommands.

Examples include:

`net user`

`net localgroup`

`net share`

The exact capabilities depend on the subcommand used.

---

# `net user`

The command:

`net user`

displays local user accounts.

Example:

`net user`

A specific user can also be queried.

Example:

`net user Administrator`

This may display information related to that account.

---

# Command Help

Windows commands usually provide built-in help.

One common format is:

`command /?`

Example:

`ipconfig /?`

This displays help information for the command.

---

# `net help`

The `net` command has its own help system.

Example:

`net help`

For help about a specific `net` command:

`net help user`

This provides more information about the `net user` command.

---

# Environment Variable `ComSpec`

Windows uses an environment variable called:

`ComSpec`

It normally points to the command-line interpreter.

A common value is:

`C:\Windows\System32\cmd.exe`

It can also be represented using the Windows system directory.

The purpose of `ComSpec` is to tell Windows which command interpreter should be used.

---

# Windows Registry

The Windows Registry is a hierarchical database that stores configuration information used by Windows and installed applications.

It contains settings related to areas such as:

- Users
- Hardware
- Software
- Services
- Operating system configuration
- Application settings

---

# Registry Editor

The graphical tool used to view and modify the Registry is:

`Registry Editor`

It can be opened using:

`regedit`

or:

`regedit.exe`

---

# Registry Structure

The Registry is organized into hierarchical sections.

These main sections are often called:

`Registry Hives`

Important examples include:

- HKEY_LOCAL_MACHINE
- HKEY_CURRENT_USER
- HKEY_CLASSES_ROOT
- HKEY_USERS
- HKEY_CURRENT_CONFIG

---

# HKEY_LOCAL_MACHINE

`HKEY_LOCAL_MACHINE`

contains configuration information related to the local computer.

It may contain information about:

- Installed software
- Hardware
- Services
- System configuration

This hive applies to the entire machine rather than one specific user.

---

# HKEY_CURRENT_USER

`HKEY_CURRENT_USER`

contains settings related to the currently logged-in user.

It can include:

- User preferences
- Application settings
- Desktop settings
- User-specific configuration

---

# Registry Keys and Values

The Registry is structured using:

- Keys
- Subkeys
- Values

A simplified example is:

`Hive`

↓

`Key`

↓

`Subkey`

↓

`Value`

This structure is similar to folders and files in a file system.

---

# Why the Registry Matters

Windows and many applications depend heavily on Registry configuration.

Changes to the Registry can affect:

- System behavior
- Application behavior
- Startup configuration
- User settings
- Services
- Security settings

Because of this, Registry changes should be made carefully.

---

# Registry and Cybersecurity

The Registry is important in cybersecurity because it can contain useful information about system configuration and user activity.

It may also be examined for:

- Persistence mechanisms
- Startup configuration
- Installed applications
- Service configuration
- User settings
- Malware-related changes

Attackers may attempt to modify Registry entries so that malicious software starts automatically.

Because of this, suspicious Registry changes can be important during incident investigation.

---

# Command Line and Registry Together

Windows command-line tools help provide quick information about the current system.

For example:

`hostname`

identifies the machine.

`whoami`

identifies the current user.

`ipconfig`

shows network configuration.

`netstat`

shows network connections.

`net user`

shows user account information.

Registry Editor provides access to deeper Windows configuration data.

---

# Basic Investigation Workflow

A simple Windows investigation might begin with:

1. Identify the system
2. Identify the current user
3. Check network configuration
4. Check active connections
5. Review user accounts
6. Examine system configuration if necessary

Example commands:

`hostname`

`whoami`

`ipconfig`

`netstat -ano`

`net user`

Then, if Registry inspection is required:

`regedit`

---

# Quick Reference

| Command / Term | Purpose |
|---|---|
| `cmd` | Open Command Prompt |
| `hostname` | Display computer name |
| `whoami` | Display current user |
| `ipconfig` | Show network configuration |
| `ipconfig /all` | Show detailed network information |
| `netstat` | Display network connections |
| `netstat -ano` | Show connections, ports, and process IDs |
| `net user` | Display user account information |
| `command /?` | Display command help |
| `net help` | Display help for `net` commands |
| `ComSpec` | Path to Windows command interpreter |
| `regedit` | Open Registry Editor |
| Registry | Windows configuration database |

---

## Key Takeaway

Windows Command Prompt provides fast access to important system information, while the Registry stores detailed configuration data.

A useful basic command set is:

`hostname + whoami + ipconfig + netstat + net user`

For deeper Windows configuration, the Registry can be examined using:

`regedit`
