## Week 16 Homework Submission File: Penetration Testing 1
#### Step 1: Google Dorking
- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is: Karl Fitzgerald Chairman
- How can this information be helpful to an attacker: The attacker can target the CEO with phishing attacks and ransomwares

#### Step 2: DNS and Domain Discovery
Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results:

  1. Where is the company located: Sunnyvale, CA, US, 94085

  2. What is the NetRange IP address: 65.61.137.64 - 65.61.137.127

  3. What is the company they use to store their infrastructure: Rackspace Backbone Engineering

  4. What is the IP address of the DNS server: 65.61.137.117	

#### Step 3: Shodan
- What open ports and running services did Shodan find: PORTS - 80, 443, 8080  SERVICES - Apache Tomcat/Coyote JSP engine 1.1

#### Step 4: Recon-ng

- Install the Recon module `xssed`. 
- Set the source to `demo.testfire.net`. 
- Run the module. 

Is Altoro Mutual vulnerable to XSS: yes (1 vulnerability)

### Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

- Command for Zenmap to run a service scan against the Metasploitable machine: nmap -T4 -A -v 192.168.0.10
 
- Bonus command to output results into a new text file named `zenmapscan.txt`: nmap -T4 -A -v -oN zenmapscan.txt 192.168.0.10

- Zenmap vulnerability script command: nmap --script smb-enum-shares 192.168.0.10

- Once you have identified this vulnerability, answer the following questions for your client:
  1. What is the vulnerability: Anyone outside of the company employees are able to Read and Write on some of the files

  2. Why is it dangerous: A threat actor can modify the vulnerable files to suit their needs

  3. What mitigation strategies can you recommendations for the client to protect their server: The client should change all privileges to under Anonymous to none so that unauthorized personnels cannot access or modify the files
---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  

