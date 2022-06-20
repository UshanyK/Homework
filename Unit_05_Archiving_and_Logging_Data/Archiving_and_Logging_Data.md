## Week 5 Homework Submission File: Archiving and Logging Data

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.

---

### Step 1: Create, Extract, Compress, and Manage tar Backup Archives

1. Command to **extract** the `TarDocs.tar` archive to the current directory:
    ```bash
    $ tar -xvf TarDocs.tar
    ```
2. Command to **create** the `Javaless_Doc.tar` archive from the `TarDocs/` directory, while excluding the `TarDocs/Documents/Java` directory:
    ```bash
    $ tar -cvf Javaless_Doc.tar --exclude=Java TarDocs
    ```
3. Command to ensure `Java/` is not in the new `Javaless_Docs.tar` archive:
    ```bash
    $ tar -tvvf Javaless_Doc.tar
    ```
**Bonus** 
- Command to create an incremental archive called `logs_backup.tar.gz` with only changed files to `snapshot.file` for the `/var/log` directory:
    ```bash
    $ sudo tar --listed-incremental =snapshot.file -cvzf logs_backup_tar.gz /var/log
    ```
#### Critical Analysis Question

- Why wouldn't you use the options `-x` and `-c` at the same time with `tar`?
    ***The -x option extracts an archive while -c option creates an archive so by using them together you will be undoing whichever option was used first.***
---

### Step 2: Create, Manage, and Automate Cron Jobs

1. Cron job for backing up the `/var/log/auth.log` file:
    ```bash
    $ crontab -e 
    #(navigate to the bottom to add the command)
    0 6 * * 3 tar -czf /auth_backup.tgz /var/log/auth.log
    ```
---

### Step 3: Write Basic Bash Scripts

1. Brace expansion command to create the four subdirectories:
    ```bash
    $ sudo mkdir -p ~/backups/{freemem, diskuse, openlist, freeedisk}
    ```
2. Paste your `system.sh` script edits below:

    ```bash
    #!/bin/bash
    free -h > ~/backups/freemem/free_mem.txt
    du -h > ~/backups/diskuse/disk_usage.txt
    lsof > ~/backups/openlist/open_list.txt
    df -h > ~/backups/freedisk/free_disk.txt
    ```

3. Command to make the `system.sh` script executable:
    ```bash
    $ chmod +x system.sh
    ```
**Optional**
- Commands to test the script and confirm its execution:
    ```bash
    $ sudo ./system.sh

    ```
**Bonus**
- Command to copy `system` to system-wide cron directory:
    ```bash
    $ sudo cp system.sh /etc/cron.weekly
    ```
---

### Step 4. Manage Log File Sizes
 
1. Run `sudo nano /etc/logrotate.conf` to edit the `logrotate` configuration file. 

    Configure a log rotation scheme that backs up authentication messages to the `/var/log/auth.log`.

    - Add your config file edits below:

    ```bash
    /var/log/auth.log {
	weekly
	rotate 7
	notifempty
	delaycompression
	missingok
    }

    ```
---

### Bonus: Check for Policy and File Violations

1. Command to verify `auditd` is active:

2. Command to set number of retained logs and maximum log file size:

    - Add the edits made to the configuration file below:

    ```bash
    [Your solution edits here]
    ```

3. Command using `auditd` to set rules for `/etc/shadow`, `/etc/passwd` and `/var/log/auth.log`:


    - Add the edits made to the `rules` file below:

    ```bash
    [Your solution edits here]
    ```

4. Command to restart `auditd`:
    ```bash
    $
    ```
5. Command to list all `auditd` rules:
    ```bash
    $
    ```
6. Command to produce an audit report:
    ```bash
    $
    ```
7. Create a user with `sudo useradd attacker` and produce an audit report that lists account modifications:

8. Command to use `auditd` to watch `/var/log/cron`:
    ```bash
    $
    ```
9. Command to verify `auditd` rules:
    ```bash
    $
    ```
---

### Bonus (Research Activity): Perform Various Log Filtering Techniques

1. Command to return `journalctl` messages with priorities from emergency to error:
    ```bash
    $
    ```
1. Command to check the disk usage of the system journal unit since the most recent boot:
    ```bash
    $
    ```
1. Comand to remove all archived journal files except the most recent two:
    ```bash
    $
    ```

1. Command to filter all log messages with priority levels between zero and two, and save output to `/home/sysadmin/Priority_High.txt`:
    ```bash
    $
    ```
1. Command to automate the last command in a daily cronjob. Add the edits made to the crontab file below:

    ```bash
    [Your solution cron edits here]
    ```

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
