# **CyberSecurity**

### **Security Bugs & Vulnerabilities**
*4- Preventing Vulnerabilities*
* Keep all software up-to-date
* Firwalls
* Antiviruses
* Educate the emplooyess(attacks and privacy,..)
* Test for bugs
* Application privileges
* Filter user input

**5-Resources for Buffer Overflows**

~~Zero-day vulnerablities~~

Buffer overflow vulnerablity:  when the input does not fit!
Website: 
[rapid7.com](https://www.rapid7.com/)

[Triaxionsecurity](https://www.triaxiomsecurity.com/)

[Secure Coding](https://www.securecoding.com/)

Computer Systems Security [(MIT course)](https://www.youtube.com/watch?v=GqmQg-cszw4&list=PLUl4u3cNGP62K2DjQLRxDNRi0z2IRWnNh)

example: C programming code( gets is nt good compare to fget )

## **Social Engineering Basics**
**1-Social Engineering Attacks**
the most common  social engineering attcks:
1. fake website
2. phishing attakcs
3. fake email address
    
    
##### **2-How To Recognize Phishing Emails**

1. The message is sent from a public email.
2. Notice From add.
3. Dear Customer!!!!
4. The domain name is misspelt.
5. The email is poorly written.
6. it includes suspicious attachment.
7. The message creats a sense of urgency.

Kali Try: 
```bash=
sudo sendemail -f randomemail@gmail.com -t target@gmail.com -u "Hello"-m "click this link to sign up"
```
***URL:*** [sendgrid](https://sendgrid.com/) sending email(no spam!)

**3-Tools For Analyzing Phishing Attacks**

***URL:*** [Emkei Mailer](https://emkei.cz/) attcker can use this to impersonate an email from another company!

[Message header analyzer](https://mha.azurewebsites.net/)
Analyze weather an email is fake or original

[Video:](https://www.youtube.com/watch?v=T6G37RHyPpw)Burp  Protection against Phisishing attacks

Application: Burp Suits

## **End-Point Protection**

**1- End-Point Protection Introduction** security at the end point of the network( mobile, laptop, ...) with the methods such as:
- [ ] Browsers
- [ ]  Antiviruses
- [ ] Passwords
- [ ] File Protections
- [ ]  Host Firewalls


 **2- Browser Security** 
* update the browser regularly!
* better browser : no internet exp!!!!
- [ ] Security Setting
- [ ] Privacy Setting
- [ ] Extensions
- [ ] Injection Attacks
- [ ] Update Time

**3-Firefox Security and Hardening**
Extension: NoScript Security Suit, Https Everywhere, DuckDuckGo 
url: chrisx.xyz 
[yet another firefox](https://chrisx.xyz/blog/yet-another-firefox-hardening-guide/)

**4-Brave Browser Security and Privacy**

Chrome: uBlock Origin

**6-Antivirus Theory**
Pros and Cons!!
EDR: end-point detection and responses 

Fisrt layer : Anti-Virus
Secodn layer : EDR

**How Anti-virus prevent?**

1. Signature Based Detection
1. Heuristic Analysis
1. Sandbox Detection
1. Detecting Behaviour

**7-Default Windows Security**

8 -

**9-Bitdefender, Kaspersky, McAfee, Malwarebytes**

**10- Password Security and Password Managers**

* Credentials: user_name and Password
* 2-factor authentication 
* Strong Password vs poor Pasword(recognizable word, short, ...)

***How to steal the password:***
1. The most common way: Phishing attack 
1. Brute Force

use Password managers: KeePaas, LastPass, NordPass, and 1Password

### **13- File and Disk Encryption**

Website: (https://heimdalsecurity.com/)

### **14-Process Explorer**
Process Explorer : microsoft product nice! try it more
Verify signer!
DLL???

### **15-Netstat and Wireshark**

[WireShark](https://www.wireshark.org/)

netstat -aon
tasklist /fi "pid eq 26260"

### **16-Htop**
sudo apt install htop

# **17-Rootkit Hunter**
scan and find the rootkit :/

# 18-Host Based Firewalls



### **19-Iptables**
Iptable: nat, filtering, map, mangle table??

filter table: input chain,forward chain?? , outpit chain, 

$ iptable -F

### **22-How To Securely Erase Files on Windows Linux Macos**
check the video for the link, or the file

### **23-End-Point Security Recap**

## 08- Network Security 
### **01- Network Security Introduction**
1. Router security 
2. Network Firewalls
3. Port & Vulnerbility Scanning
4. MITM Prevention
5. Wireless Security
6. Monitoring For Threats
### **02- Network Firewalls Theory**
* House-based firewalls vs Network Firewalls
**firewalls types:**
1. Packet filtering firewalls
2. Stateful Inspestion firewalls
3. Application Layer firewalls, most commin web-application firewalls
4. Next Generation firewalls ( combination of all above) the goal: have more protection

### **03- Different Network Firewalls**
* First :Discover it
1. Network Scanning & Discovering Vulnerbilities
2. discover the services that are use in the open ports
3. port 80 is open => 

Port Scan: scan all the ports 
Ports
Services
purpose
security
  Then put it offline, patched/ removed

### **04- Network Security With Nmap**
Network port-scanning with NMAP!
Do it with permeion
```bash=
$ nmap 192.168.1.1 -p 80,90,100
$ nmap 192.168.1.1 -p 80-120  // range of ports
$ nmap 192.168.1.1 -F  // scan top 100 common ports
$ nmap 192.168.1.1 -p 80,90,100
$ nmap 192.168.1.1 -p 80,90,100

```
Classification of attacks: List the 5 types of attacks.
A
1. Passive attack
2. Active attack
3. Close-in attack
4. Insider attack
5. Distribution attack

What is passive attack?
A
Gaining information (reconnaissance) about the target without engaging with victim.
This is legal.

What is active attack?
A
Gaining information (reconnaissance) about the target while actively communicating with the target system.
This is illegal

What is Close-in attack?
A
Attacker is in close physical proximity basis with the systems/networks (ex. shoulder surfing, dumpster driving, eavesdropping)
What is an insider attack?
A
Already inside the organization (ex. backdoors, malware, theft of physical devices). This can be a current employee.

Q
What is a distribution attack?
A
Attackers tamper with hardware /software prior to installation.

What are the phases of the Cyber Kill Chain Methodology?
A
Reconnaissance --> Weaponization --> Deliver --> Exploitation --> Installation --> Command & Control --> Actions on Objectives.

Q
What does TTPs stand for and what is it?
A
Tactics, Techniques, Procedures.
Tactics = the guidelines
Techniques = the "how"
Procedures = how organizations do

Q
IoCs (Indicators of Compromise) can fall into these 4 categories:
A
1. Email indicators
2. Network indicators
3. Host-based indicators
4. Behaviour indicators


Q
8 Types of Hacker classes.
A
1. Black hat (aka crackers)
2. White hat
3. Gray hat
4. Suicide hackers (don't care if they get caught)
5. Script kiddies
6. Cyber Terrorists
7. State-sponsored hackers (ex. Cozy Bear)
8. Hacktivists (political agenda)


Q
5 Steps of Hacking.

* know this for exam
A
1. Recon (passive vs active)
2. Scanning (ex. port scanners)
3. Gaining Access
4. Maintaining Access
5. Clearing tracks (ex. remove log files)
6. 

Ethical hacking = _________ + __________
A
Ethical hacking = permission + intent


Q
IoCs (Indicators of Compromise) can fall into these 4 categories:
A
1. Email indicators
2. Network indicators
3. Host-based indicators
4. Behaviour indicator

List some technical skills of a hacker.
A
- knowledge of major OS environments
- networking
- expert
- knowledgeable in security
- "high technical" knowledge for launching sophisticated attacks

List some non-technical skills of a hacker.
A
- ability to learn quickly
- strong work ethics
- committed to organization's security policies
- awareness of standards and law
- 

# **Jadi CEH Course:**

The most common attack to steal password is Phishing attack
IDS: Intrusion detection system
IPS: Intrusion Prevention System

Planting a backdoor

Incident respone

*Backup:* 
1. Full Backup
1. Differential Backup
1. Incremental Backup

