# Linux Package Management

This page contains my notes on software packages, repositories, APT, GPG keys, and package installation on Debian/Ubuntu-based Linux systems.

---

## What Is a Package?

A package is a software bundle that contains the program itself and the files or information needed to install it.

Examples:

- Firefox
- VLC
- Apache
- Python

On Ubuntu and Debian-based systems, packages are commonly distributed as `.deb` files.

---

## What Is a Repository?

A repository is an online software source that contains packages.

It can be thought of like an application store for Linux.

Example idea:

Ubuntu Repository

- Firefox
- Python
- Apache
- VLC
- Other packages

When I run:

`sudo apt install apache2`

APT checks the configured repositories, finds the package, downloads it, and installs it.

---

## APT — Advanced Package Tool

APT is the package management tool used on Debian and Ubuntu-based Linux systems.

It can be used to:

- Search for packages
- Install software
- Update package information
- Upgrade installed packages
- Remove software
- Manage dependencies

---

## `apt update`

`apt update`

refreshes the local package list.

It checks configured repositories and downloads information about available package versions.

Important:

`apt update`

does not upgrade the installed software itself.

It only updates the package index.

---

## `apt upgrade`

`apt upgrade`

upgrades installed packages to newer available versions.

Simple way to remember:

`apt update` → refresh available package information

`apt upgrade` → upgrade installed packages

---

## Installing a Package

Example:

`sudo apt install apache2`

This downloads and installs the Apache package and its required dependencies.

---

## Searching for Packages

Example:

`apt search wireshark`

This searches the configured repositories for packages related to Wireshark.

---

## Removing a Package

Example:

`sudo apt remove sublime-text`

This removes the installed package.

---

# Where Are Repository Addresses Stored?

Linux stores repository configuration in files such as:

`/etc/apt/sources.list`

and:

`/etc/apt/sources.list.d/`

These files tell APT where it should look for packages.

For example, a third-party repository might have its own file:

`/etc/apt/sources.list.d/sublime-text.list`

---

# Third-Party Repositories

Not every application is available in the default Ubuntu repositories.

In that case, a trusted third-party repository can be added.

This tells APT:

"Also check this software provider when searching for packages and updates."

Only trusted repositories should be added because repositories are software sources for the system.

---

# Adding a Repository

One method is:

`add-apt-repository`

Repositories can also be added manually by creating a file under:

`/etc/apt/sources.list.d/`

After adding a new repository, the package list should be refreshed:

`sudo apt update`

Then the package can be installed using:

`sudo apt install package-name`

---

# GPG Keys

GPG keys are used to help verify that software packages come from the expected software provider.

They act like digital signatures.

The system can use them to check whether:

- The package was signed by the expected developer or repository
- The package may have been modified unexpectedly

---

## Example from the Notes

An older repository setup method may use:

`wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -`

This performs two main actions:

1. Downloads the repository's GPG key
2. Sends it to `apt-key`

The `|` symbol is a pipe.

It sends the output of the first command into the second command.

Conceptually:

`wget output → apt-key input`

---

## `apt-key`

The notes use `apt-key` as part of the repository setup example.

The purpose in this workflow is to add a trusted repository signing key.

---

# Example Repository Installation Workflow

A typical workflow from the notes is:

1. Add the software provider's GPG key
2. Add the repository address
3. Refresh the package list
4. Install the software

Example structure:

`Add GPG key`

↓

`Add repository`

↓

`sudo apt update`

↓

`sudo apt install sublime-text`

---

# `dpkg`

`dpkg` can install `.deb` packages directly.

Example:

`sudo dpkg -i program.deb`

This installs the package file that already exists on the system.

---

# APT vs DPKG

The main difference is:

`dpkg` → installs a local `.deb` package directly

`apt` → works with repositories and can manage package dependencies

A dependency is another package that software needs in order to work.

Example:

Program

- Python
- Library A
- Library B

APT can usually find and install required dependencies automatically.

---

# Removing a Repository vs Removing a Package

These are different actions.

Removing a package:

`sudo apt remove package-name`

removes the installed software.

Removing a repository means removing the software source from APT's configuration.

For example, a repository may be removed by deleting its file from:

`/etc/apt/sources.list.d/`

or by using a repository removal command.

---

# Package Management Workflow

The basic process is:

1. Configure repository sources
2. Trust the repository key
3. Run `apt update`
4. Install software using `apt install`
5. Upgrade software using `apt upgrade`
6. Remove software using `apt remove`

---

# Quick Reference

| Command / Path | Purpose |
|---|---|
| `apt update` | Refresh package information |
| `apt upgrade` | Upgrade installed packages |
| `apt install package` | Install a package |
| `apt search package` | Search for packages |
| `apt remove package` | Remove a package |
| `dpkg -i file.deb` | Install a local `.deb` package |
| `/etc/apt/sources.list` | Main repository configuration |
| `/etc/apt/sources.list.d/` | Additional repository configuration |
| `add-apt-repository` | Add a repository |
| `|` | Pipe output from one command to another |

---

## Key Takeaway

Linux package management is built around packages, repositories, and tools such as APT.

The basic idea is:

`Repository → Package List → Install / Upgrade / Remove`

Repositories define where software comes from, while APT manages the software installed on the system.
