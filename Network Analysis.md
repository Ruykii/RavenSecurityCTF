# Network Analysis
Example of network analysis
## Time Thieves 
**Description**:  
At least two users on the network have been wasting time on YouTube. Usually, IT wouldn't pay much mind to this behavior, but it seems these people have created their own web server on the corporate network. So far, Security knows the following about these time thieves:
    - They have set up an Active Directory network.
    - They are constantly watching videos on YouTube.
    - Their IP addresses are somewhere in the range 10.6.12.0/24.

1. Domain name of the user's custom site. 
    ![](https://media.discordapp.net/attachments/1002356492344770703/1003001499049279488/unknown.png)

    **Frank-n-Ted-DC.frank-n-ted.com**

2. IP address of the Domain Controller (DC) of the AD network.

    ![](https://cdn.discordapp.com/attachments/1002356492344770703/1003001955213389855/unknown.png)

    **10.6.12.12**

3. Name of malware that downloaded on to the 10.6.12.203 machine. 

    ![](https://cdn.discordapp.com/attachments/1002356492344770703/1003002147597721741/unknown.png)

4. After uploading to virustotal.com it was classified as Trojan. 

    ![](https://cdn.discordapp.com/attachments/1002356492344770703/1003002359653347418/unknown.png)

## Vulnerable Windows Machine

**Description**: 
The Security team received reports of an infected Windows host on the network. They know the following:
    - Machines in the network live in the range 172.16.4.0/24.
    - The domain mind-hammer.net is associated with the infected computer.
    - The DC for this network lives at 172.16.4.4 and is named Mind-Hammer-DC.
    - The network has standard gateway and broadcast addresses.

## Inspecting traffic and Summary. 

    1. Infected Windows machine: 
        - Host name Rotterdam-PC.mind-hammer.net
        - IP address: 17.16.4.205
        - MAC address: 00:59:07:b0:63:a4
    2. Proof of Windows's user that were infected. 
    ![](https://cdn.discordapp.com/attachments/1002356492344770703/1003004680152023050/unknown.png)

    3. IP addresses that are used in the infection traffic:
        - 17.2.16.4.205
        - 185.243.115.84
