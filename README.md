# SIEM-Lab---Opnsense-Firewall-Setup-Part-2
In this project I will be updating the Opnsense firewall and adding features like Intrusion Detection and Intrusion Prevention System(IPS) to my firewall.

First we have disable the hardware capabilites of the firewall as it is recommended by Opnsense.

<img width="1271" height="920" alt="image" src="https://github.com/user-attachments/assets/c30fc87d-f3f1-4ed8-9f75-88ba288e1449" />

Then we will naviagte to the Intrusion Detection tab and then administration. We will then enable intrusion detection, ips mode(allows us to block traffic), promiscious mode(captures data on physical interfaces), enable syslog alerts(alerts the system), and pattern matching(Hyperscan). We will make the interface our LAN interface and then set the home network to the LAN subnet in this case it is 192.168.1.1/24(This is the defalut assigned subnet).

<img width="1272" height="918" alt="image" src="https://github.com/user-attachments/assets/f9934fa2-afab-44c1-a2dd-0b394d9f29a5" />

Next we will write our own custom rule. The rule will alert any TCP traffic that comes from the home network, and on any port that is routed to 192.168.1.1/24 it will generate the message possible NMAP scan detected. We will use NMAP which is a reconissence tool/port scanning tool that is used by penetration testers, or hackers. This is generally the first test that a penetration tester, or hacker will do to probe the machine.

<img width="854" height="553" alt="image" src="https://github.com/user-attachments/assets/f8e43940-4d7b-4d17-9595-bc787fe156f4" />

By defalut opnsense doesn't allow us to make any ssh connections to it, but there is a way to override this. We go to the system settings then administration and then enable the secure shell, root login, and authentication method. Then we will only listen to connections from our LAN interface. 

<img width="987" height="573" alt="image" src="https://github.com/user-attachments/assets/40e2ca04-66a5-4488-a465-ced27b33d51b" />

To get to the file system of opnsense we will do this by downloading filezilla. To do this we must use sudo su to become the root user. Then we will use the sudo -apt update command to update kali linux. finally we use to sudo apt-get install filezilla to install filezilla and exit root user. 

<img width="657" height="522" alt="image" src="https://github.com/user-attachments/assets/5cef39bc-6e5e-48c3-9da6-451c41e691f9" />

Then we will open filezilla and make a sftp connection to 192.168.1.1, use our usernmae of root, password, and we will connect in port 22.

<img width="1136" height="776" alt="image" src="https://github.com/user-attachments/assets/fc4dbce0-2b70-44b2-9ee4-d2e8142f957d" />

This allows us to gain access to the opnsense root directory.

<img width="951" height="782" alt="image" src="https://github.com/user-attachments/assets/b2b59c56-4e28-4514-9e48-4382522f90b1" />

We will create two files one that is called customnmap.rules which is the file that contains the rules and then another file called customnmap.xml which shows the computer where to set up the http server. We then have to go to the opnsense rules folder and then we transfer our customnmap.xml to opnsense rules folder. 

<img width="952" height="797" alt="image" src="https://github.com/user-attachments/assets/0a2e9ce7-3acc-4e54-978a-5df391ad1920" />

Then we will set up a python tccp server.

<img width="643" height="527" alt="image" src="https://github.com/user-attachments/assets/137cb918-890c-49f9-baf4-9e12040ef483" />

Now we go back to the opnsense website and we refresh the downloads page for intrusion detection and our customnmap rules are now in the downloads section. 

<img width="996" height="577" alt="image" src="https://github.com/user-attachments/assets/1432a9e2-dec6-4944-98d9-9bf66ff71f9e" />

Now we download and update the rule and we know it has been successfully done by checking the date of the update. 

<img width="997" height="577" alt="image" src="https://github.com/user-attachments/assets/274be134-abe5-44fb-b429-f217c17e74e6" />

Now we are able to see out new custom rule in the Rules tab in Opnsense.

<img width="1233" height="658" alt="image" src="https://github.com/user-attachments/assets/f79806b5-7007-445e-9c7b-1fe2916e1763" />

To test that the custom rule is working we will use nmap to scan the ports. Therefore, we will use a stealth scan to check the ports.

<img width="660" height="522" alt="image" src="https://github.com/user-attachments/assets/9035aa6c-1ed4-416a-8195-e81e3f7c01cb" />

Now we will go back to opnsense and check the alerts tab to see if the custome ruleset is properly working.

<img width="1233" height="665" alt="image" src="https://github.com/user-attachments/assets/5bc012be-fbf5-4da7-b84e-2516fbd3bb3b" />

It just works! This is the end of the second part of the firewall configuration.
