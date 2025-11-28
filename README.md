# Auditing a Network & Planning for a Secure WLAN Implementation

**Lab title:** Auditing a Network & Planning for a Secure WLAN Implementation

---

# Overview

This lab focuses on assessing the security of wireless networks (WLANs) by analyzing broadcast information, capturing wireless traffic, evaluating encryption
strength, and performing WPA/WPA2 key recovery using the Aircrack-ng suite. 
The lab concludes with a WLAN security implementation plan designed to mitigate risks identified during testing.

Wireless networks are highly flexible but expose organizations to threats such as unauthorized access, 
sniffing attacks, rogue access points, and weak encryption configurations. 
This lab simulates a real-world IT auditing engagement by guiding the entire WLAN security assessment process, from reconnaissance to exploitation to remediation planning.

---

# Why This Lab Is Important

Wireless networks remain one of the most frequently attacked components of corporate infrastructures. 
Many breaches begin with weak Wi-Fi passwords, outdated encryption, or rogue devices broadcasting insecure access points. 
This lab demonstrates practical WLAN auditing skills that employers expect in roles such as:

- IT Auditor  
- SOC Analyst  
- Cybersecurity Analyst  
- Penetration Tester  
- Network Security Engineer  

The ability to audit wireless networks, crack WPA keys, analyze encryption protocols, and provide actionable security recommendations is a rare hands-on skillset that immediately stands out in interviews and hiring processes.

---

# Tools & Software

- **Aircrack-ng Suite** — WLAN packet capture, analysis, and key recovery  
- **Kali Linux** — Auditor system used for testing  
- **Windows Server 2016** — Simulated workstation environment  

---

# Lab Topology

```
vWorkstation (Windows Server 2016)  →  172.30.0.2
Kali Linux (Auditor System)        →  172.30.0.33
```

![Topology](audit_top.png)

---

# Section 1: Exploring the Aircrack-ng Suite

## Step 1: Reviewing Airmon-ng
Command:  
`man airmon-ng`  
Used to enable and manage monitor mode on wireless interfaces.  
![Airmon-ng](airmon_command.png)

---

## Step 2: Reviewing Airodump-ng
Command:  
`./airodump-ng --help`  
Used for capturing 802.11 frames, identifying APs, clients, channels, and encryption types.  
![Airodump-ng](airodump.png)

---

## Step 3: Reviewing Aireplay-ng
Command:  
`./aireplay-ng --help`  
Used to inject frames, generate wireless traffic, and perform deauthentication to capture WPA handshakes.  
![Aireplay-ng](aireplay.png)

---

## Step 4: Reviewing Aircrack-ng
Command:  
`aircrack-ng --help`  
Used to crack WEP and WPA/WPA2 pre-shared keys from captured packets.  
![Aircrack-ng](aircrack.png)

---

# Section 2: Applied WLAN Assessment

## Step 1: Attempting WPA Key Recovery
Command:

```
aircrack-ng -w /WLAN/wordlist/wordlist.txt /WLAN/wordlist/WLAN/Capture-01.cap
```

Aircrack-ng analyzes the capture file, identifies access points, and verifies handshake presence.  
![Aircrack WPA](aircrack_WLAN.png)

---

## Step 2: Selecting Target Network and Cracking the Key
Selected target network index **18**, allowing Aircrack-ng to run a dictionary attack against the captured handshake.  
The WPA key was successfully recovered.  
![Network Target](network_target.png)

---

# Section 3: Analysis, Evaluation & WLAN Implementation Plan

## Part 1: Public Wi-Fi Risk Analysis

Risks associated with hotel/public Wi-Fi:
- Packet sniffing  
- Evil Twin attacks  
- Session hijacking  
- MITM attacks  
- Rogue access points  
- Malware propagation  

Safer practices:
- Use a VPN  
- Disable sharing  
- Prefer HTTPS  
- Avoid sensitive logins  
- Use mobile hotspots  

---

## Part 2: Tools & Commands Research

**Example wordlist source:**  
https://github.com/danielmiessler/SecLists

Command to crack WPA with a downloaded wordlist:

```
aircrack-ng -w downloaded_list.txt Capture-01.cap
```

---

## Part 3: WLAN Security Implementation Plan

### a. Summary of Findings
- Networks using weak encryption (WEP) detected  
- Weak WPA-PSK passphrases  
- Visible SSIDs and broadcast metadata  
- Successfully cracked WPA key demonstrates real vulnerability  

---

### b. Critical Risks & Vulnerabilities
- Weak or guessable passwords  
- Legacy encryption (WEP, TKIP)  
- No mutual authentication  
- Exposure to offline dictionary attacks  
- No wireless intrusion monitoring  
- SSID broadcasting  

---

### c. Overall WLAN Security Assessment
The WLAN security posture is rated **moderate to weak**, depending on encryption protocols and password strength.

---

### d. Security Recommendations

**Encryption & Authentication**
- Upgrade to WPA3-SAE  
- Deploy WPA2-Enterprise with RADIUS  
- Disable WPS  
- Enable 802.11w Management Frame Protection  

**Password Standards**
- Enforce long, random passphrases (16+ characters)  
- Avoid dictionary words  
- Rotate credentials periodically  

**Network Hardening**
- Use VLANs to separate guest and internal networks  
- Disable SSID broadcasting where appropriate  
- Deploy wireless IDS/IPS  
- Conduct regular WLAN audits  

---

# Skills Demonstrated

- WLAN auditing and reconnaissance  
- 802.11 packet capture and frame analysis  
- WPA handshake extraction  
- WPA offline dictionary attack  
- Understanding WEP/WPA/WPA2 weaknesses  
- Identifying cipher suites (AES, TKIP, CCMP)  
- Wireless security risk assessment  
- Drafting enterprise WLAN security plans  
- Professional audit reporting  
- Hands-on use of Kali Linux & Aircrack-ng  

---

# Conclusion

This project demonstrates a complete WLAN security assessment workflow, showcasing practical penetration testing and IT auditing skills. 
It highlights the ability to identify vulnerabilities, exploit weak configurations, and develop professional-grade remediation strategies competencies 
valued across cybersecurity and auditing careers.
