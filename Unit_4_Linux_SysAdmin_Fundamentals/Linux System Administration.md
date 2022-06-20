## Week 4 Homework Submission File: Linux Systems Administration

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.


### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions:
    ```bash
    $ ls -l /etc/shadow
    ```
    - Command to set permissions (if needed):
    ```bash
    $ sudo chmod 600 /etc/shadow
    ```
2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions:
    ```bash
    $ ls -l /etc/gshadow
    ```
    - Command to set permissions (if needed):
    ```bash
    $ sudo chmod 600 /etc/gshadow
    ```
3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:
    ```bash
    $ ls -l /etc/group
    ```
    - Command to set permissions (if needed):
    ```bash
    $ sudo chmod 604 /etc/group
    ```

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:
    ```bash
    $ ls -l /etc/passwd
    ```
    - Command to set permissions (if needed):
    ```bash
    $ sudo chmod 604 /etc/passwd
    ```
### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users):
    ```bash
    $ sudo useradd sam
    $ sudo useradd joe
    $ sudo useradd amy
    $ sudo useradd sara
    $ sudo useradd admin
    ```
2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group:
    ```bash
    $ sudo usermod -a -G sudo admin
    ```
### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group:
    ```bash
    $ sudo groupadd engineers
    ```
2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):
    ```bash
    $ sudo usermod -a -G engineers sam
    $ sudo usermod -a -G engineers joe
    $ sudo usermod -a -G engineers amy
    $ sudo usermod -a -G engineers sara
    ```
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:
    ```bash
    $ sudo mkdir /home/engineers
    ```
4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:
    ```bash
    $ sudo chown :engineers /home/engineers
    ```
### Step 4: Lynis Auditing

1. Command to install Lynis:
    ```bash
    $ sudo apt-get install lynis
    ```
2. Command to see documentation and instructions:
    ```bash
    $ man lynis
    ```
3. Command to run an audit:
    ```bash
    $ sudo lynis audit system
    ```
4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output: ![](Images/1.png)

### Bonus
1. Command to install chkrootkit:
    ```bash
    $ sudo apt install chkrootkit -y
    ```
2. Command to see documentation and instructions:
    ```bash
    $ man chkrootkit
    ```
3. Command to run expert mode:
    ```bash
    $ sudo chkrootkit -x
    ```
4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output: ![](Images/2.png)

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
