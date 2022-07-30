## RavenSecurityCTF
<p align="center">
  <img width="200" src="https://cdn.discordapp.com/attachments/1002356492344770703/1002956300226924604/unknown.png" alt="raven logo">
</p>

**Description**

A CTF for Ravensecurity a older box to display skills of penetration testing and using the capstone and elk in order to monitor and send alert as proof of concept. 

## Table of Content

  - [Offensive](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Offensive.md)
  
  - [Defensive](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Defensive.md)
  
  - [Network Analysis](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Network%20Analysis.md)
 
## Offensive

The task was to find the four flag. Below will be the scope of IP as well as methodology, further information is [here](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Offensive.md).

  **Scope of IP**:
  
  - 192.168.1.1/24
  - Target 1: 192.168.1.110
  - Target 2: 192.168.1.115
  
  **Methodology**:
  
  - Identify the scopes
  - Reconnaissance (Using nmap, wpscan)
  - Plan of attack (Using user's username and password. What am I looking for?)
  - Escalate privilege (Python exploit with sudo on one of the user's account)
  - Record of findings

## Defensive

Identifying current's organization SIEM (Kibana) and configuring alerts as well as maintenance. More information located [here](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Defensive.md).

  **Alerts**
  
  - Excessive HTTP Error (threshold: more than 400 http code within 5 minutes)
  - HTTP Request Size Monitor (threshold: documents over 3500 bytes within a minute)
  - CPU Usage Monitor (threshold: CPU usage over fifty percent within 5 minutes)
  
  **IP Monitoring**
  
  - 192.168.1.1/24
## Network Analysis

A example of network analyzing using Wireshark of a infected scene between Window's user. All explanation provided [here](https://github.com/Ruykii/RavenSecurityCTF/blob/main/Network%20Analysis.md).


**Thank you for reading and for your time**
