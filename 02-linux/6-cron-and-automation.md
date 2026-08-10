# Cron and Automation

This page contains my notes on task scheduling and automation in Linux using cron.

---

## What Is Cron?

Cron is a Linux service used to run commands or scripts automatically at scheduled times.

It is useful for repetitive tasks such as:

- Running backups
- Cleaning temporary files
- Executing scripts
- Generating reports
- Performing scheduled maintenance

Instead of running a command manually every time, cron can execute it automatically.

---

## What Is Crontab?

`crontab` means cron table.

It is the file or configuration that contains scheduled cron jobs for a user.

To view the current user's cron jobs:

`crontab -l`

To edit them:

`crontab -e`

---

## Cron Time Format

A standard cron entry uses five time fields.

The format is:

`MINUTE HOUR DAY MONTH WEEKDAY COMMAND`

Example:

`30 2 * * * /home/user/backup.sh`

This means:

Run `/home/user/backup.sh` every day at 02:30.

---

## Understanding the Five Fields

| Field | Meaning |
|---|---|
| Minute | 0-59 |
| Hour | 0-23 |
| Day | Day of the month |
| Month | Month of the year |
| Weekday | Day of the week |

After these fields comes the command that should be executed.

---

## The `*` Character

The `*` wildcard means:

"every possible value"

Example:

`* * * * * command`

means the command is scheduled for every minute.

Another example:

`0 * * * * command`

means:

Run at minute 0 of every hour.

---

## Example: Daily Task

`0 8 * * * /home/user/script.sh`

This means:

Run `script.sh` every day at 08:00.

---

## Example: Weekly Task

`0 10 * * 1 /home/user/weekly.sh`

This means:

Run `weekly.sh` every Monday at 10:00.

---

## Example: Backup Job

A backup script could be scheduled like this:

`0 2 * * * /home/user/backup.sh`

This runs the backup script every day at 02:00.

The basic workflow is:

1. Create the script
2. Make sure it has the required permissions
3. Add it to crontab
4. Cron executes it automatically

---

# `@reboot`

Cron also supports special scheduling keywords.

One useful example is:

`@reboot`

This runs a command after the system starts.

Example:

`@reboot /home/user/startup.sh`

This means:

Run `startup.sh` when the system boots.

---

## Why `@reboot` Is Useful

It can be used for tasks such as:

- Starting a custom script
- Launching a service
- Running initialization commands
- Performing startup checks

---

# Editing Cron Jobs

To edit cron jobs:

`crontab -e`

A text editor opens.

A new cron entry can then be added.

Example:

`0 6 * * * /home/user/daily-task.sh`

After saving the file, cron uses the new schedule.

---

# Viewing Cron Jobs

To display current scheduled tasks:

`crontab -l`

This allows me to check which cron jobs are configured for the current user.

---

# Cron and File Paths

When using cron, it is useful to use full file paths.

For example:

`/home/user/scripts/backup.sh`

instead of only:

`backup.sh`

This helps avoid problems caused by different working directories or environment variables.

---

# Cron and Permissions

The user running the cron job must have permission to execute the command or script.

For example, if a script needs execute permission, the permissions must allow it.

A script might be made executable with:

`chmod +x script.sh`

---

# Automation Workflow

A simple automation workflow is:

1. Create a script
2. Test the script manually
3. Give it the correct permissions
4. Open crontab using `crontab -e`
5. Add the schedule
6. Save the file
7. Verify with `crontab -l`

---

# Why Cron Matters in Cybersecurity

Cron is important because scheduled tasks can be used for legitimate system administration and automation.

From a cybersecurity perspective, cron jobs are also worth checking during system analysis because they can reveal:

- Automated maintenance tasks
- Backup processes
- Startup scripts
- Unexpected scheduled commands
- Persistence mechanisms

This makes cron useful both for system administration and security investigation.

---

# Quick Reference

| Command / Syntax | Purpose |
|---|---|
| `crontab -e` | Edit cron jobs |
| `crontab -l` | List cron jobs |
| `* * * * *` | Cron time format |
| `@reboot` | Run a command at system startup |
| `chmod +x file` | Make a script executable |

---

## Key Takeaway

Cron allows Linux tasks to run automatically based on a schedule.

The basic structure is:

`Time Schedule → Command or Script`

This is useful for backups, maintenance, scripts, and other repetitive tasks.
