# Incident-Response (NIST 800-61) Brute Force Success

![NIST](https://i.imgur.com/aAAATFM.png)

## Introduction

In this project, I follow the NIST 800-61 guide to respond to an incident thoroughly and effectively. Using the same virtual machines and logs and basically the entire setup from my honeynet project, I am now going to start responding and handling the incidents that accured on those systems. In this case I'll be focusing on the Brute force Success incident. 

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)


## List of all incidents that accured in the past 7 days on the systems.
![Arc](https://i.imgur.com/IlpcYPy.png)

## Assining the incident to myself and letting it be known im actively working on it.
![Architecture Diagram](https://i.imgur.com/6J17BIQ.png)

## Getting a broader scope of the incident.
![Architecture Diagram](https://i.imgur.com/VhLii9g.png)
At this point I will start making my personal notes for the incident and getting deeper in the "analysis" phase. 

## Viewing the entity.
![Architecture Diagram](https://i.imgur.com/GNUlPMk.png)

## Beginning hte investigation.
![Architecture Diagram](https://i.imgur.com/MqN3Wly.png)


## Veiwing the attacker machine in depth.
![Architecture Diagram](https://i.imgur.com/jGmsx5n.png)
So as we can see here, this attacker has been in several other alerts / incidents, and this windows machinet has been involed in lot more alerts/incidents(which is expected for the machine because it had no security of any kind before I hardened it). Of course in the real world I will need to investigate this specific host in depth on its own, but for now for the project, I'll continue to just focus on this one specific alaert.

## Viewing the logs for the attackers IP address.
![Architecture Diagram](https://i.imgur.com/QWptm0j.png)
In the red is the powershell script that were used to run and find and catch any malicious traffic from the machines. The purple is the powershell script used to locate and find any successful logins from the specific attackers IP address. In the green is the infomation that was ran from the powershell script for the attackers IP address. As you can see, the associated IP address has multiple successful logins to the windows machine with the account name "NT..."

## Getting info on the account name.
![Architecture Diagram](https://i.imgur.com/3vFy0A1.png)
So after reading this article, it was stated that this account is an service account and not an actual attacker. 

## Ending my notes and closing out this incident.
![Architecture Diagram](https://i.imgur.com/7yx9j11.png)
In this case, the incident waas a false positve due to it not being a legit attacker but the service machince should not have been able to breach the system and successfully login. Now the system has to be hardened.


## Viewing the network rules.
![Architecture Diagram](https://i.imgur.com/UoJVsZZ.png)
The main reason the system was hacked and attacked from many other machine nd hackers is because the inbound rule was set to "any allowed in". Whcih should NEVER be done in the real world. 

Congiguring the NSG to be hardened by adding inbound rule.
![Architecture Diagram](https://i.imgur.com/uMW7Odu.png)
After adding an inbound rule to only allow incoming trafic to remotely connect to the machine from my specific IP address, it mitigates the risk from other attackers from getting into the system. 




















