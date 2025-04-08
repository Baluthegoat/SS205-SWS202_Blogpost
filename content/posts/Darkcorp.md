---
title: DarkCorp
description: Assignment 1
publishedDate: 2024-04-09
tags:
  - Assignment writeups
---

Machine IP address: 10.10.11.54

# Ping

Before doing any scan for the given IP address I wanted to see if the machine is transmitting data packets to a specific IP address.

![alt text](/src/assets/Images/Dark-corp/ping.png)

After the ping was successfully done, i could found out that the given IP address has the connectivity. 

# Recon

I ran the basic nmap scan to see if their is any port open for the given IP address.

![alt text](/src/assets/Images/Dark-corp/Screenshot_2025-02-13_00-03-06.png)

The scan result shows two ports were open : 22 tcp ssh and 80 tcp http. 


To see the services running on each port, I ran the following `nmap` command:

```bash
nmap -sCV <ip address>

```
![alt text](/src/assets/Images/Dark-corp/-sV-scan.png)

The scan result shows that the port 22 is running on openSSH 9.2p1 Debian. The port 80 is running nginx 1.22.1. So upon checking both service in the exploit DB the vulnerability was not listed. 

Now to check the web running on port 80 I added the ip address in the etc/hosts to create a local DNS mapping.

![alt text](/src/assets/Images/Dark-corp/nano.png)

After creating the local DNS mapping the website was successfully loaded. 

![alt text](/src/assets/Images/Dark-corp/website.png)

To check if their is any hidden directory inside the website I ran directory brute forcing using the SecLists.

![alt text](/src/assets/Images/Dark-corp/ffuf.png)

The scan result shows that the website has four hidden directory, so I tried to register the in the drip.mail. But their is nothing inside after registering. 

![alt text](/src/assets/Images/Dark-corp/account.png)

So, after registering I couldn’t go further to exploit the website due to the time limit for the machine.