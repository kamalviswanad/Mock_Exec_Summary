**Executive summary**
Red&Blue’s Corporate Server was compromised yesterday by a ransomware attack and the R&D server, which resulted in a 10-hour service disruption for our defense systems research because we could not access research data. This impacted on the company’s ability to access all of our data to do research. All the systems were quickly isolated, preventing lateral movement to the infrastructure, and no other systems were affected. 
The law enforcement has been notified of this attack. As this incident did not suffer a data breach and customer PII (personal identifiable information) was affected, the risk of regulatory fines being imposed on the company is very low.

**Details of the Incident and Actions Taken**
The attack exploited a zero-day vulnerability (CVSS 10.0) in the ConnectWise ScreenConnect remote management software , that is used to remotely connect and manage our servers. There is no current patch from the vendor to prevent it. Due to the advanced structure of the ransomware, our security monitoring system was not able to prevent the encryption of files. The adversary bypassed authentication mechanisms to gain administrative privileges and deployed a malicious payload, which made it possible for the attacker to encrypt the company’s research data and files. But our Next-Generation Firewall successfully flagged blocked data exfiltration attempts to a remote command and control (C2) server run by the malicious actor, preventing a double extortion scenario.
After we identified the affected servers, we have isolated them, imaged them using forensic tools and terminated the servers. We have restored the lost information from our off-premises backups and secured it using hardening techniques and notified the vendor about this vulnerability. 

**Business Impact:**
In terms of availability, this incident disrupted R&D operations for 10 hours because our researchers could not access any data to move forward with our new projects. This incident took place from 10:30 AM [EST] to 8:30 PM [EST]. While the probability of reputational damage from the press and regulatory fines is very low because no customer or employee PII was affected, it resulted in disruption in our research and operations. The server and data have been restored using our off-premises backup after 10 hours of downtime. Currently, our research and operations are resumed, and all our confidential data is safe and remains intact as audits of system logs don’t show exfiltration activity and further investigation is being done. 

**Next Steps: **
Our cybersecurity team has completed the identification, response, containment and ransomware eradication phases of our incident response plan. We have also restored all the data from our backups and operations have resumed. We have disabled vulnerable ports and protocols associated with remote management until the vendor releases a patch. A comprehensive post incident review (PIR) is underway to document lessons learned and update our threat signatures.

**Nature of the attack:**
ConnectAttack, is a new ransomware variant designed to encrypt files with an AES algorithm encryption key and prevents decrypting information without paying the ransom. The attack  encrypted files in the R&D data server by exploiting a zero-day vulnerability (CVSS 10.00) in the ConnectWise ScreenConnect software used to manage our servers. This vulnerability is exploited by malicious actors aiming at medium and large corporations. This attack was a combination of automation and manual effort. The malicious actor exploited zero-day vulnerability and bypassed traditional authentication mechanisms to get into the system to gain admin access to the server and encrypt the files. The intention of the malicious actor was to demand ransom and steal our data. But the adversary could not extract the data because our firewall blocked the action. The attack succeeded because the vulnerabilities found in the software were not officially found by anyone and not released to the public. This prevented the development team at  ConnectWise ScreenConnect developing a patch to solve this vulnerability.

**Notification to Regulatory Authorities:**
As per Red&Blue’s security controls and security incident response process, the FBI and CISA were briefed about this security incident (Level 2). Even though no PII has been compromised, we remain prepared for potential regulatory inquiries and fines.

**Incident Response Details- Detection, Analysis & Containment:**
During the incident, our security service software collecting logs from all servers and running analysis detected the ransomware attack and has notified the cybersecurity team immediately. While the R&D server was compromised unfortunately, the other servers were immediately isolated from the network and were hardened to prevent them from being compromised too. A level 2 incident ticket was raised after the notification, and the incident response was initiated according to our policies and relevant authorities were notified too. We have taken a sound forensic image of our R&D server for further investigation.

in order to mitigate any additional risk at the data center Red&Blue enforced several precautions and implemented security best practices. 
1.	As an official patch has not been released by the vendor, we have disabled a few vulnerable ports and protocols related to the remote management software. And also increase network segmentation for the server’s security.
2.	Using another platform temporarily until the vendor releases a patch to fix this vulnerability. 

Further Analysis of data indicated the R&D server was compromised on 3/1/2026 at 10:30:44 AM [EST] and further attacks on Red&Blue’s other servers were blocked before they were compromised. After further analysis to understand the mechanics of the attack and the risk it posed, we have identified how the malicious attacker compromised our server.

**Step-1:** The malicious actor found a zero-day vulnerability in the ConnectWise ScreenConnect software and developed an exploit for it. The exploit bypassed our authentication mechanisms and compromised the server administrators account . They made an HTTP connection request form an external IP and downloaded a file called receipt.exe into the server. Then the actor executed the exploit to install ransomware to the server and encrypt all our files using AES-256 algorithm. 
**Step-2:**  The security monitoring system logs indicate that the script attempted to stop multiple processes which would have likely detected the attack and stop it. A further function was to delete log files such as syslog, to hamper efforts to detect the script. However, since the syslog files are sent to the security monitoring system in real time without being staged on the server, automated log analysis detected anomalous behaviour and triggered an incident alert. It finally encrypted the target server and displayed a ransom note, directing Red&Blue incident responders to another domain (http://decrypt-server.com), which was registered on February 5th ,2026, The malicious  actor demanded 50 bitcoins to decrypt the files..
**Step-3:** The ransomware attempted to exfiltrate data but was blocked by Next generation firewall. After analysis, the cybersecurity team at Red&Blue confirmed that no other infrastructure was affected other than the R&D server. 

**Next Steps:**
With significant risks at play until full-service restoration, Red&Blue continues to be on high alert throughout the restoration process.
1.	New attack signatures are being added to the company’s security monitoring system to prevent the attack in the future.
2.	A vulnerability scan is being performed to ensure all servers are immune to the new zero-day vulnerability.
3.	Post-incident review, reporting, and lesson learned are being updated.

**Recommendations:**
1.	Ensure signatures in endpoint security monitoring systems are regularly updated.
2.	Ensure backups are regularly updated and regularly test them to ensure they are working as expected.
3.	Implement a secure VPN or Zero Trust Network Access (ZTNA) for all remote management interfaces.
4.	Increase the security awareness of employees and train them how ransomware propagates to the servers and how to prevent them
5.	Consider deploying an intrusion prevention system.
6.	Restrict access to any remote management software and interface from external IP address and establish a secure VPN solution.
