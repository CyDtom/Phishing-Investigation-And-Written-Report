# Phishing Investigation And Written Report
<img src="https://i.imgur.com/7W6cWEq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />   


## Introduction

I conducted this phishing analysis exercise after completing training and labs from [Securityblue.team's](https://elearning.securityblue.team/public/lab-certificate/1afacae9-17f3-43ad-9522-3b0f33a1b27e) BTL1 course, which focused on phishing analysis. To hone my skills in analyzing email phishing attempts, I obtained a suspicious email from my Gmail account and utilized a variety of tools to gather evidence and compose a detailed report.


The tools I used are: 
- Outlook
- [Sublime Text2](https://www.sublimetext.com/2)
- [domaintools](https://whois.domaintools.com/)
- [VirusTotal](https://www.virustotal.com/gui/home/upload)
- [Browersling Url Sandbox](https://www.browserling.com/)

## Email Description and Artifacts 
![image](https://i.imgur.com/9kmEnxs.png)

### Artifacts
- **Sending Address**:  o3.email.webuyanycarusa.com
- **Subject Line**: Claim Your Metamask Airdrop Today!
- **Recipient**:  Crismejia73xxx@gmail[.]com
- **Sending Server IP**: 159.135.234.42
- **Date and Time**: Sun, 24 Sep 2023 01:55:28 -0700
- **SHA-256**: 0eae230a252373cce84574ede7462f3728f99ea4e11e8d02a0dbf0913a88e287
- **Embedded URL (Sanitized)**: 
hxxps[://]fcg-cdn[.]exponea[.]com/webuyanycarusa/e/[.]eJzj4knl392u5XDXxPjPMQchhSR2vvW7Ti09lLQ43HTb9i_nq1NVT2zc823J1R9cMVpfT9VKiWaUlBQUW-nrJxcXFOXnpaXqFZToZxp-muKw4LvzTUcrXi6m0mIh9tSKgvy81EQrbiA3V4g1NTcxM8dKFMhJFuJ3d_ZTCHENDlHQVXDOL6iMCtHXT8pPqdQvSUzKSdUvgbCL9EtSICLRRrGYgliUGcdCuSmZZfqJWTzxs1kVJ7_OmPTvYnc_AAPxV84[.]ida4hBLgC11YeA/cli
- **Final URL (Sanitized)**: hxxps[://]potrfoliometamosk[.]com/


### Description
This email appears to be a phishing attempt. It is designed to deceive recipients into believing that it is coming from Metamask, a popular cryptocurrency wallet and browser extension for Ethereum. However, it is important to note that this email is not legitimate, and recipients should exercise caution and not engage with it.




## Artifact Analysis / Methods
Sublime Text 2
![image](https://i.imgur.com/vC9viGq.png)
Browsling
![image](https://i.imgur.com/lMMjFVw.png)
- Using Outlook I am able to download the email 
- using sublimetext2 we are quickly able to Find Sending server IP, date and time, Embedded URL, and much more
- A Whoisdomain search on the sender's IP shows that the email did not come from Google/Gmail but from "m234-42.mailgun[.]net" 
- A quick Google search on Mailgun reveals that "Attackers are either compromising accounts with weak passwords or just buying Mailgun’s services and then sending out phishing emails." (Avanan, 2023)
- A VirusTotal search on the entire link shows that it has already been flagged for malicious and phishing activity by Webroot.
- Using Browserling on the full URL shows that the link leads to a web page that prompts the recipient to check if the connection is secured, which then redirects them to a blank page
- Looking at the complete URL shows that it is a redirect link

 ## Suggested Defensive Measures
We have encountered this email originating from an unrecognized domain, with all communications stemming from a single sender within that domain. Consequently, the recommended course of action is to implement an email gateway block specifically targeting the sender's email address, preventing any further messages from that source. Furthermore, it is advisable that we also do a web proxy block for the Final Url for defense in-depth

 #### 1. Requesting an email gateway block for the sending address "o3.email.webuyanycarusa.com".

#### 2. Requesting a web proxy block for the domain "hxxps[://]potrfoliometamosk[.]com/".
