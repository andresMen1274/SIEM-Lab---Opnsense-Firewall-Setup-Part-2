# SIEM-Lab---Opnsense-Firewall-Setup-Part-2
In this project I will be updating the Opnsense firewall and adding features like Intrusion Detection and Intrusion Prevention System(IPS) to my firewall.

First we have disable the hardware capabilites of the firewall as it is recommended by Opnsense.

<img width="1271" height="920" alt="image" src="https://github.com/user-attachments/assets/c30fc87d-f3f1-4ed8-9f75-88ba288e1449" />

Then we will naviagte to the Intrusion Detection tab and then administration. We will then enable intrusion detection, ips mode(allows us to block traffic), promiscious mode(captures data on physical interfaces), enable syslog alerts(alerts the system), and pattern matching(Hyperscan). We will make the interface our LAN interface and then set the home network to the LAN subnet in this case it is 192.168.1.1/24(This is the defalut assigned IP).

<img width="1272" height="918" alt="image" src="https://github.com/user-attachments/assets/f9934fa2-afab-44c1-a2dd-0b394d9f29a5" />


