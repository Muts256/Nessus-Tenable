<h1>Hi, I'm Michael! <br/><a href="https://www.linkedin.com/in/michael-musoke/">Cybersecurity Professional</a></h1>

<h2>👨‍💻 Tenable Installation and Configuration </h2>

The objective of this lab  is to:
  - Install and configure Nessus scanner on Kale Linux.
  - Configure scans and how to scan the network.
  - Generate reports.

<h2> Network Topology </h2>

Technology used
  - Kali Linux
  - Ubuntu PC
  
    ![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T1.png)

<h2> Install Nessus scanner on Kali Linux </h2>

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




<h2> Vulnerability Scanning </h2> 

To create a New Scan, in the My Scan on the right-hand side, click on New Scan.

![image alt](https://github.com/Muts256/SNC-Public/blob/7627f86c904e8746eda91998520e06542123492a/Images/Tenable/T24.png)













<h2> 🤳 Connect with me:</h2>

[<img align="left" alt="michael-musoke | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />][linkedin]

[linkedin]: https://linkedin.com/in/michael-musoke
