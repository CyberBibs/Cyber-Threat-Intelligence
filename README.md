# Cyber Threat Intelligence

## Objective

The objective of this lab is to show my threat intelligence skill and assist organizations proactively prevent and mitigate cyberattacks by providing actionable information about potential or existing threats. This involves collecting, analyzing, and sharing data about attackers, their motives, and attack methods to enable proactive defense and improve security posture. 

In this lab, I investigated real-world threats using penCTI and the AlienVault OTX connector, to identify high-risk actors and activities, and report my findings in a way that supports an organization's critical decision-making.

### Skills Learned

- Application of cyber frameworks such as Diamond Model, Kill Chaun and time analysis to understand attacker behavior and impact.
- Cyber Threat Intelligence.
- Starting, stoping and managing docker.

## Components
### Virtualization Platform
- **Microsoft Azure:** Acts as the hypervisor hosting all other virtual machines/servers.

### Threat Intelligence Platform
- **OpenCTI (Open Cyber Threat Intelligence):**
  - An open-source platform I used to manage and share cyber threat intelligence (CTI) in this project.
- **AllienVault Connector :**
  - a software component that i connected to OpenCTI to facilitates data integration and automation between AlienVault's Open Threat Exchange (OTX) OpenCTI.

### Container
- **Docker:**
  - The conte.

### Operating System
- **Ubuntu 22.04:**
  - Manages user authentication and domain management.

### Tools Used
- OpenCTI : .
- AllienVault OTX Connector: .
- Azure VM: .
- Docker: .

### About the System
The Client Details System (version 1.0) is a web-based application built using PHP, CSS, Bootstrap, and JavaScript. It serves as a centralized platform for managing client information, providing both user and administrator panels. The user panel facilitates the entry and retrieval of client details, while the administrator panel empowers system management and user administration.

### Threat Considered
Due to the vulnerability found in our assessment of the Client Details System 1.0, we discovered that the “uemail” parameter allows SQL Injection. We exploited this vulnerability and compromised the application, thereby able to access user data (username and password) and the underlying database information CVE-2023-7137.     

### Attack scenario
For this vulnerability assessment, the attack scenarios considered include firstly, an attacker exploiting vulnerabilities in input validation mechanisms of the Client Details System to inject malicious SQL queries into user input fields and potentially gaining unauthorized access to the database and executing arbitrary commands. Secondly, the attacker can also bypass authentication mechanisms to gain unauthorized access to privileged functionalities within the system. Thirdly, attackers can also use automated tools to attempt and guess admin credentials to gain uncontrolled access.

### Steps
1. OWAS ZAP: Used OWASP ZAP, an open-source web application security scanner, to conduct automated vulnerability scans on the http://localhost/clientdetailsystem. We Configured ZAP to perform comprehensive scans, including both passive and active scanning, then reviewed the scan results to identify and prioritize potential security vulnerabilities detected by OWASP ZAP. As shown in Proof of Concept, BLIND SQL injection and UNION Query SQL inject were identified as critical vulnerability.  
![Picture2](https://github.com/user-attachments/assets/8c621698-fb08-40e9-bbab-f3403fe1b5df)

2. Burp Suite: we use this to carry out manual tests and also capture HTTP Post Request Header. Extracted payloads and attack vectors identified by OWASP ZAP for manual verification, we then Utilized Burp Suite's Repeater tool to replay requests and manipulate parameters with the identified payloads by Conducting targeted manual testing, including input validation bypass, XSS, and other injection attacks, to validate and further exploit identified vulnerabilities.
![Picture3](https://github.com/user-attachments/assets/6f51cdcb-d689-422a-aaf0-888ef4dcb94d)

3. SQLMAP: used for detecting and performing SQL injection vulnerability present in the Client Detail System. The steps perform using SQLMap are descriped below; <br>
   i. Capture and Save HTTP POST Request Header: We initiated the testing process by          capturing the HTTP POST request header generated from the login request with            invalid username and password inputs within the Client Details System (CDS).            This interception was conducted using Burp Suite. The captured request,                 containing the attempted exploit, was then saved as a text file named request.txt       for further analysis and exploitation.
 ii.  Enumerate Databases and Discover Injection Point: Utilizing the saved HTTP              request file, SQLMap was employed to scan the Client Details System for SQL             injection vulnerabilities. Command executed was:
   sqlmap.py -r C:\Users\musta\OneDrive\Desktop\request.txt --dbs --flush     session.
                            Output
   ![Picture4](https://github.com/user-attachments/assets/d481269c-870d-4319-b7cf-2becb942f468)




Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*
