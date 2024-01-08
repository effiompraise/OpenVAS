# Vulnerability Management with OpenVAS
![Vulnerability Management / OpenVAS](https://imgur.com/NAsF8wT.jpg)

## Summary and Aim

In this project, a secure Azure network was established and equipped with two virtual machines. These machines were designated for running the OpenVAS Vulnerability Management Scanner and Windows 10. The Windows 10 virtual machine intentionally had its security controls disabled and outdated software installed to create vulnerabilities.

To emphasize the importance of configuring vulnerability scans correctly, two kinds of scans were carried out. Initially, an unauthenticated scan was performed on the Windows 10 machine. Subsequently, after completing the unauthenticated scan, a credentialed scan was set up and initiated. Remedial actions were based on the findings of the credentialed scan, aimed at addressing significant vulnerabilities.

A final credentialed scan was executed to validate the efficacy of the implemented remedial measures.

## Technologies, Azure Components, and Regulations Used
- Azure Virtual Network
- OpenVAS Vulnerability Management Scanner
- Windows 10 Pro virtual machine
- Outdated software, known to have vulnerabilities
  - Mozilla Firefox, v97.0b5
  - VideoLAN VLC Media Player, v1.1.7
  - Adobe Reader, v10.0.0

## Allocate Resources and set up Virtual Machines to Conduct an Unauthenticated Scan

The initial step in this project involved setting up the OpenVAS Vulnerability Management Scanner. In particular, OpenVAS by HOSSTED was employed with a default developer setup. Concurrently, a Windows 10 Pro virtual machine was established during the installation of OpenVAS.

![Vulnerability Management / OpenVAS](https://imgur.com/7LuWtWI.jpg)

To ready the Windows 10 machine, the firewall was turned off, and obsolete editions of Firefox, VLC Media Player, and Adobe Reader were installed deliberately. The intention was to deliberately expose vulnerabilities in the Windows 10 machine. After disabling the firewall and installing the vulnerable software, the machine was rebooted.

![Vulnerability Management / OpenVAS](https://imgur.com/9fOti4b.jpg)

### The process of setting up OpenVAS for an unauthenticated scan involved completing the following steps:

   1. A new host was established utilizing the private IP Address of the Windows 10 virtual machine.

![Vulnerability Management / OpenVAS](https://imgur.com/ZY2wcT1.jpg)

   2. A new target was created by using the host from the preceding stage. All remaining settings were maintained 
      at their default values, and no credentials were provided to OpenVAS

![Vulnerability Management / OpenVAS](https://imgur.com/YzK0geS.jpg)

   3. A new task was created using the target specified in the preceding step. Once more, all remaining 
      configurations were maintained at their default settings for this scan.

![Vulnerability Management / OpenVAS](https://imgur.com/ID0F05y.jpg)

## Findings from the Unauthenticated Scan

![Vulnerability Management / OpenVAS](https://imgur.com/bRCMecr.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/jKfzPZh.jpg)

## Prepared Windows 10 to undergo a Credentialed Scan

Several adjustments were necessary to prepare the Windows 10 machine for a credentialed scan. Initially, it was essential to confirm that the Domain, Private, and Public profiles in the Windows Firewall remained disabled, as per the initial configuration.

Subsequently, the subsequent actions were undertaken:

   1. Disabled User Account Control
![Vulnerability Management / OpenVAS](https://imgur.com/xKgGmAh.jpg)
   2. Enabled Remote Registry
![Vulnerability Management / OpenVAS](https://imgur.com/D84DEjx.jpg)
   3. Navigate to the Windows Registry and create a new DWORD named “LocalAccountTokenFilterPolicy” and set the 
      value to “1”
![Vulnerability Management / OpenVAS](https://imgur.com/N80wQHk.jpg)














