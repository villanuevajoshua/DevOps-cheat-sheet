# Basic Cron Setup on Linux
This guide shows how to run a Node.js command with cron every minute and how to check whether it is working

### Prerequisites
- Your Node.js app is already deployed.
- You know the full path to npm when using nvm.
- The log directory exists and is writable by the cron user.


### Step 1: Prepare your script
Make sure the script or command you want to run works manually first. If you are using nvm, confirm the correct npm path with which npm in your shell.

### Step 2: Open crontab
Edit the cron entries for your user:
```bash
crontab -e
```

### Step 3: Confirm the paths
Check the full path of npm
```bash
which npm
```

### Step 4: Add the cron job
Add this line to run the command every minute:
```bash
* * * * * cd /opt/hrgains-dev &&
/home/javillanueva/.nvm/versions/node/v24.13.0/bin/npm run eAttestation >>
/opt/hrgains-dev/logs/eAttestation-cron.log 2>&1
```

This:
- runs every minute,
- changes into your project directory first,
- executes npm run eAttestation,
- writes all output and errors to a log file.

### Step 5: Create the log folder
Before cron runs, make sure the folder exists:
```bash
mkdir -p /opt/hrgains-dev/logs
```
> If the folder does not exist, cron cannot create the log file and the job will fail

### Step 6: Check cron logs
On most Linux systems, cron logs are stored in different places depending on the distribution.

**Ubuntu / Debian**
```bash
grep CRON /var/log/syslog | tail -50
```

**CentOS / RHEL**
```bash
tail -50 /var/log/cron
```

### Step 7: Check your job output
To see the output from your Node command:
```bash
tail -50 /opt/hrgains-dev/logs/eAttestation-cron.log
```
> This log file contains the output from your cron job, while the system cron log only shows that the cron daemon executed the command.

---

## Rule of cron

| Position | Time unit | Allowed Values | What `*` means here
| -------- | --------- | -------------- | ------------------ |
| 1st | Minute | `0 - 59` | Run on every minute |
| 2nd | Hour | `0 - 23` | Run during every hour of the day |
| 3rd | Day of Month | `1 - 31` | Run on every day of the month |
| 4th | Month | `1 - 12` | Run in every month of the year |
| 5th | Day of Week | `0 - 6` (0 = Sunday) | Run on every day of the week |

