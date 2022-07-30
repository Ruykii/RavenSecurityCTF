# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services
    - Scope of IP 192.168.1.1/24 
    - Target 1 IP 192.168.1.110

| Port     | Service      | 
|----------|--------------|
| 22       | SSH          |
| 80       | HTTP         | 
| 111      | RPCbind      | 
| 139      | netbios-ssn  |
| 445      | Microsoft-DS | 

Nmap scan results for each machine reveal the below services and OS details:

```bash
$ nmap -Pn -sV -p 80,111,139,445 192.168.1.110
```

This scan identifies the services below as potential points of entry:
- Target 1
![](https://cdn.discordapp.com/attachments/1002356492344770703/1002356508425728180/unknown.png)



The following vulnerabilities were identified on each target:

CVE (common vulnerability and exposure) score explained:
| Severity | Base Score   | 
|----------|--------------|
| None     | 0            |
| Low      | 0.1-3.9      | 
| Medium   | 4.0-6.9      | 
| High     | 7.0-8.9      |
| Critical | 9.0-10.0     | 

| CVE ID        | Score      |                  Vulerability Description                                            |
|---------------|------------|--------------------------------------------------------------------------------------|
| CVE-2001-0572 | 7.5        | Due to weak password for their user account, easy access by SSH                      |
| CVE-2021-24585| 6.5        | Outputing hashed passwords, username, and email address using wpscan                 |
| CVE-2002-1374 | 7.5        | Brute force common password for MySQL's access to database                           |
| CVE-2019-5629 | 7.8        | Access to privileges by using Python's interpreter in order to gain system privilege |




### Exploitation


The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
- 'flag1.txt':

  ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002367792793800795/unknown.png)
    - **Exploit Used**
      -  Used grep to find the location of flag. 
      - We logged in to michael due to michael lack of a sturdy password. (Password was michael)
      - We also used wpscan to identify data needed to find the username. (Image below)
   ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002368292050178108/unknown.png)   

  - `flag2.txt`: 
  
   ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002368657487298560/unknown.png)
    - **Exploit Used**
      - We identified the flag by using the "find" command in order to find it
       '''
        find -name "*flag*"
       '''
   - 'flag3':
   
   ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002369447786455090/unknown.png) 
    - **Exploit Used** 
       - We identified the password by gaining access to the hash password from Michael's wordpress config file. Password: "R@v3nSecurity" 
       location of file below. 
   ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002380263076151306/unknown.png)    
       - Gaining access of MySQL 
       - Found the hash password for both Michael and Steven through MySQL. (image below)
       ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002381732848349334/unknown.png)

       - Used John the Ripper to break the hash of the passwords in order to gain access to Steven. 
       '''
        john --wordlist=/usr/share/wordlists/rockyou.txt wp.txt
       '''
       Using rockyou wordlist and the name of the hash file is "wp.txt". Password for Steven is "pink84"
   - 'flag 4.txt'
   
   ![](https://cdn.discordapp.com/attachments/1002356492344770703/1002382653045080085/unknown.png)
    - **Exploit Used**
       - Using sudo -l we were able to see that there is access to python 
       - Using a spawn script 
       '''
        sudo python -c 'import pty;pty.spawn("/bin/bash")'
       '''
       - We are able to gain access to root and bash. 
       - Using the same find command as above, we were able to find flag 4. 
