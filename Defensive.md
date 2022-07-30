# Blue Team: Summary of Operations
<p align="center">
  <img width="460" height="300" src="https://cdn.discordapp.com/attachments/1002356492344770703/1002995836755640450/unknown.png">
</p>
## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology


The following machines were identified on the network:
- Target 1
  - **Operating System**: Debian GNU/Linux
  - **Purpose**: Server 1/ Target 1
  - **IP Address**: 192.168.1.110
- Target 2
  - **Operating System**: Debian GNU/Linux
  - **Purpose**: Server 2/Target 2
  - **IP Address**: 192.168.1.115
- Kali
  - **Operating System**: Kali/Linux
  - **Purpose**: To attack box "Target 1" and "Target 2"
  - **IP Address**: 192.168.1.90/24
- ELK
  - **Operating System**: Linux
  - **Purpose**: Container to monitor both Target 1 and 2
  - **IP Address**: 192.168.1.100/24
- Capstone
  - **Operating System**: Linux
  - **Purpose**: Alert
  - **IP Address**: 192.168.1.105/24

### Description of Targets


The target of this attack was: `Target 1` (IP: 192.168.1.110).

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Excessive HTTP Error 


Alert 1 is implemented as follows:
  - **Metric**: HTTP codes
  - **Threshold**: Above 400 within 5 minutes
  - **Vulnerability Mitigated**: Mitigating network scanning for a server or forms of bruteforce (Hydra, john the ripper,dirbuster)
  - **Reliability**: Alert does send in a lot of false negatives and medium effiency. 

#### HTTP Request Size Monitor 
Alert 2 is implemented as follows:
  - **Metric**: Bytes
  - **Threshold**: Document size over 3500 within a minute. 
  - **Vulnerability Mitigated**: prevent wpscan 
  - **Reliability**: Has medium success rate. 

#### CPU Usage Monitor 
Alert 3 is implemented as follows:
  - **Metric**: Percentage
  - **Threshold**: Documents over 0.5 within 5 minutes. 
  - **Vulnerability Mitigated**: Prevent background process or malware
  - **Reliability**: This is low efficiency due to user's usage. 



### Suggestions for Going Further 


The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:
- Network Scanning
  - **Patch**: Preventing specific traffic, or adding limitation on how often a IP can deliver TCP.
  - **Why It Works**: Preventing attacks to view information of a server will prevent possible attacks, with each information gathered like open ports the easier it is to form a plan for a attack. 
- WPScan
  - **Patch**: Preventing useres to gain access to specific text files or changing the directory of the wordpress content. 
  - **Why It Works**: This will prevent the scan to fully gather data of users and other information due to the scan unable to gather said information. 
- Python Escalation 
  - **Patch**: Update the system. 
  - **Why It Works**: Most of recent vulnerabilities or exploits can be easily solved by updating those patches. 
