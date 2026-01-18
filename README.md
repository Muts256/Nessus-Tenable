<h1>Hi, I'm Michael! <br/><a href="https://www.linkedin.com/in/michael-musoke/">Cybersecurity Professional</a></h1>

<h2>👨‍💻 Tenable Installation and Configuration </h2>

The objective of this lab  is to:
  - Install and configure Nessus scanner on Kali Linux.
  - Configure scans and how to scan a network.
  - Generate reports.
  - Interprete CVSS

## Table of Contents

- [Network Topology](#network-topology)
- [Install Nessus Scanner on Kali Linux](#install-nessus-scanner-on-kali-linux)
- [Vulnerability Scanning](#vulnerability-scanning)
- [Generating Reports](#generating-reports)
- [Common Vulnerability Scoring System](#common-vulnerability-scoring-system)

<h2>Network Topology</h2>

Technology used
  - Kali Linux
  - Ubuntu PC
  
    ![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T1.png)

<h2>Install Nessus Scanner on Kali Linux</h2>

On Kali Linux, open a browser and navigate to [Tenable](https://www.tenable.com/download/nessus) website. Select the latest Nessus version available, select Linux-Ubuntu-amd64 for the platform.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T2.png)

Open a terminal on Kali Linux and change the directory to the Downloads folder where Nessus was downloaded to 

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T3.png)

It is good practice to verify that the download has not been tampered with. On the web browser page next to the Download button, click on the checksum button. Copy the sha256 value
On the Kali Linux terminal, issue the command:

echo "Hash-value-copied Nessus-downloaded" > sha256sum_nessus

This command combines the hash value copied from the Tenable website and the Nessus instance downloaded into one file named sha256sum_nessus. 
Then use the command sha256sum -c sha256sum_nessus

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T4.png)

The result should be ok; otherwise, something may not be quite right with the download.

Make the download executable by issuing the command chmod 744 Nessus version. chmod 700 will do as well

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T5.png)

Next, install Nessus: ./Nessus download. Enter the password if required.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T6.png)

Installation will then start.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T7.png)

Next is to register with tenable for an activation code. On a web open page at the tenable for education page [Activation Code](https://www.tenable.com/tenable-for-education/nessus-essentials). Use a valid email as the activation code will be sent to this address. 

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T8.png)

On the terminal after Nessus is installed, start the service.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T9.png)

To enable the Nessus service to start during boot time, issue the command 
sudo systemctl enable nessusd.service

Open a web browser and open the Nessus web interface at localhost port 8834


![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T10.png)

Because the certificate is self-signed, you will receive a warning. Click on advanced, then accept the risk and continue. 

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T11.png)

Check the Register Offline box and click continue.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T12.png)

On the next screen, select Nessus Professional and click continue.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T13.png)

On the Register Nessus page, copy the challenge code and visit the Offline Registration page. Once the challenge code is copied, an activation code will be sent to the email used at the start of the registration process. A license key will be generated. Copy this license into the space provided.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T14.png)

Once the license is accepted. Create a user and password to log in. Click submit

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T16.png)

Nessus will begin the initialisation of the components before access is granted.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T17.png)

When access is granted, click on the settings tab, then the Software Updates tab. Select the Update plugins radio.  Select Daily on the Update Frequency. Then click save.
This will ensure that the latest plugins are installed as and when they are released.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T19.png)

To download the plugins manually, click on Manual Software Update on the button in the top right-hand corner

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T20.png)


On the next screen, select Update all components and click continue

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T21.png)

A wheel will appear at the top of the Manual Software Update, keeping track of the progress 

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T22.png)

Updating the components and the plugins takes a long time. Wait for notification of completion


![image alt](https://github.com/Muts256/SNC-Public/blob/05d0af8a6e9cf3c44b21d097af29e8496dc84cf0/Images/Tenable/T23.png)

<h2>Vulnerability Scanning</h2> 

To create a New Scan, in the My Scan on the right-hand side, click on New Scan.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T24.png)

In the Scan Templates, select the type of scan to be done. In this case, a Basic Network Scan 

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T25.png)

Under New Scan/Basic Network Scan. Fill in the required information. In the Basic – General Name of the scan, Description, Target (IP Addresses of the host to be scanned. These can be a single IP address or a range, including an entire network if the license purchased allows it.  Scans can be scheduled in the schedule section, and notifications.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T26.png)


Under the Discovery tab, Select Port scan

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T27.png)

Under the Assessment tab

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T28.png)

Under the Reports tab. Select the information that you would like to appear in the report.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T29.png)

Under the Advanced tab: select the default option

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T30.png)

Save the settings. On the My Scans page, click on the play button to start a scan.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T31.png)

Wait for the scanning to complete. With the scan completed, navigate to the scan and click on it

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T32.png)

Under the Vulnerabilities tab, the outcome of the scan will be displayed

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T33.png)


To find out more about the vulnerability, click on it.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T34.png)

A description of the vulnerability will provide insight into why it is flagged. A solution section will show how the vulnerability can be mitigated


<h2>Generating Reports</h2>

Select the scan for which the report is required on the top-right-hand, either select the report or the export button

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T36.png)


On the next screen, select the format of 3 options: HTML, PDF, or CSV, then the desired report.
Then click Generate Report 

![image alt](https://github.com/Muts256/SNC-Public/blob/a08571c6da4be45d8c8e1132c88bb8381d927581/Images/Tenable/T37.png)

If you click the export button, select the format desired, then this will be exported to the downloads folder.

## Common Vulnerability Scoring System

**CVSS (Common Vulnerability Scoring System)** is an industry-standard framework used to measure the severity of security vulnerabilities. It assigns a numeric score from **0.0 to 10.0**, which helps organisations understand how serious a vulnerability is and how quickly they should respond.

CVSS is based on three metric groups: Base, Temporal, and Environmental.

### **1. Base Metrics**
Intrinsic, unchanging characteristics of the vulnerability  
*Examples: how easy it is to exploit, impact on confidentiality, integrity, and availability*

### **2. Temporal Metrics**
Factors that may change over time  
*Examples: availability of exploits, existence of a patch*

### **3. Environmental Metrics**
Impact in the context of your specific organisation  
*Examples: how important the affected system is to your business*

CVSS provides a consistent, objective way to prioritise remediation. A higher score means the vulnerability is more critical and typically requires faster mitigation.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T35.png)


## Interpretation
cvss:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H

This is a **CVSS v3.0 Base Score vector**, and each part describes a characteristic of the vulnerability.

#### Attack Vector (AV:N) – **Network**
The vulnerability can be exploited remotely over a network.  
No physical or local access is required.

#### Attack Complexity (AC:L) – **Low**
The attack is straightforward.  
No special conditions, race conditions, or unusual states are needed.

#### Privileges Required (PR:N) – **None**
The attacker does not need any credentials or permissions to exploit this vulnerability.

#### User Interaction (UI:N) – **None**
No user interaction is required.  
The attack works without a victim clicking or doing anything.

#### Scope (S:C) – **Changed**
The vulnerability can break out of its security boundary.  
Compromising one component can impact another system, service, or environment.  
This usually increases severity significantly.

#### Confidentiality Impact (C:H) – **High**
Successful exploitation can lead to complete loss or disclosure of data.

#### Integrity Impact (I:H) – **High**
An attacker can fully modify or overwrite data.

#### Availability Impact (A:H) – **High**
An attacker can completely disrupt system availability (e.g., shutdown, crash, DoS).


This is a **critical vulnerability** that is:

- Remotely exploitable  
- Easy to exploit  
- Requires no privileges  
- Requires no user interaction  
- Allows crossing security boundaries  
- Results in full compromise of confidentiality, integrity, and availability

---

## Remediation

The results of the vulnerability scan are communicated to system owners and stakeholders, with findings prioritised according to CVSS scores, business impact, and system criticality. Recommended remediation actions are proposed and agreed upon with the relevant owners. Upon completion of remediation activities, a follow-up scan was conducted to confirm closure of the identified vulnerabilities and reduce residual risk.

---

## Lessons Learned

- Gained practical experience installing and configuring the Nessus vulnerability scanner.  
- Understood the importance of verifying downloads using SHA256 hashes to ensure file integrity.  
- Learned how to activate Nessus plugins and adjust scanner settings for accurate results.  
- Practised running vulnerability scans.  
- Improved ability to interpret scan findings, including severity levels and CVSS scores.    
- Learned how to generate, export, and review detailed vulnerability reports.  
- Understood how vulnerability scanning fits into a broader security programme.
<h2> 🤳 Connect with me:</h2>

[<img align="left" alt="michael-musoke | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />][linkedin]

[linkedin]: https://linkedin.com/in/michael-musoke
