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
   3. Navigated to the Windows Registry and created a new DWORD named “LocalAccountTokenFilterPolicy” and set the 
      value to “1”
![Vulnerability Management / OpenVAS](https://imgur.com/N80wQHk.jpg)

## Set up OpenVAS to Perform a Credentialed Scan

As the Windows 10 machine rebooted, the subsequent actions were taken to set up OpenVAS for a credentialed scan:

   1. Generated a new credential by supplying the username and password of the Windows 10 virtual machine to OpenVAS
![Vulnerability Management / OpenVAS](https://imgur.com/kO4tHWF.jpg)
   2. Duplicated the current target by selecting the sheep icon located in the "Actions" section. Modified the 
      duplicated target by activating SMB and choosing the credentials generated in the earlier stage.
![Vulnerability Management / OpenVAS](https://imgur.com/p4DzaXC.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/fXZrcf9.jpg)
   3. Duplicated the current task and modified the duplicate to utilize the authenticated target generated in the 
      preceding stage.
![Vulnerability Management / OpenVAS](https://imgur.com/RBOEWfJ.jpg)

## Outcome of Credentialed Scan

The contrast in vulnerabilities uncovered between the unauthenticated and credentialed scans is striking. Not only did the severity rating escalate from 5.0 (medium) to 10.0 (high), but the credentialed scan revealed an additional 107 vulnerabilities.

The credentialed scan enabled OpenVAS to comprehensively assess the system, identifying vulnerabilities within the outdated software. OpenVAS offers a dedicated tab for Common Vulnerabilities and Exposures (CVEs), providing a user-friendly breakdown of each vulnerability. This breakdown encompasses a description, score, vector, references, and remedial actions.

![Vulnerability Management / OpenVAS](https://imgur.com/StaNNul.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/e2KSPtV.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/LFs1KUi.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/xjBjwep.jpg)

## Remediation, Verification Scan, and Conclusion

To address most of the vulnerabilities detected during the credentialed scan, the outdated software on the Windows 10 machine was removed. A subsequent credentialed scan was conducted to confirm that the implemented fixes effectively resolved the anticipated vulnerabilities.

The scan results indicated successful remediation efforts, displaying a decrease in vulnerabilities. Eliminating the outdated software led to a 91% reduction in vulnerabilities identified by OpenVAS.

![Vulnerability Management / OpenVAS](https://imgur.com/ug0PCtI.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/6iyQEUG.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/QdJuK5b.jpg)
![Vulnerability Management / OpenVAS](https://imgur.com/vc44mei.jpg)

<p>This project effectively showcased the setup of OpenVAS and the subsequent resolution of vulnerabilities. It underscored the significance of performing credentialed scans whenever feasible, highlighting that an unauthenticated scan doesn't provide an accurate picture of a system's security. Although some high severity vulnerabilities persisted in the credentialed scan, addressing these was beyond the project's scope.</p>

## Reflection

The purpose of this project was to provide me with practical exposure to vulnerability management, covering configurations and remedial actions. Moving forward, I aim to revisit this project, emphasizing advanced vulnerability remediation in my future endeavors.










