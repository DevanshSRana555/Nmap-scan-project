# Local Network Security Scan Project

## Objective
To identify active devices and open ports on my local network using Nmap to assess potential security entry points.

## 1. Setup & Installation
- Downloaded Nmap from the [Official Nmap Download Page](https://nmap.org).
- Installed on [Installed on Windows 11 Home Single Language (Version 25H2)].

## 2. Target Identification
- **Local IP Range:** `192.168.29.0/24`
- **Scan Date:** Tue Feb 17, 2026

## 3. Scan Command
Ran the following command with administrative privileges to perform a Stealth SYN scan:
`nmap -sS -oN myscan.txt 192.168.29.0/24`

## 4. Findings & Risks

### Device 1: Gateway/Router (192.168.29.1)
- **Open Ports:** 53 (DNS), 80 (HTTP), 443 (HTTPS), 1900 (UPnP), 7443 (oracleas-https), 8080 (http-proxy), 8443 (https-alt).
- **Risk Assessment:** Multiple web management and proxy ports (80, 443, 8080, 8443) are open. Ensure the router firmware is up to date and default passwords are changed. Port 1900 (UPnP) is active, which can be a common vector for discovery exploits.

### Device 2: Local Workstation (192.168.29.120)
- **Open Ports:** 135 (MSRPC), 139 (NetBIOS), 445 (SMB), 902/912 (VMware), 3306 (MySQL).
- **Risk Assessment:** 
    - **High Risk:** Port 445 (SMB) and 139 (NetBIOS) are open. These are high-priority targets for lateral movement and ransomware within a network.
    - **Medium Risk:** Port 3306 (MySQL) indicates an active database. 

## 5. Saved Results
Full raw results are saved in `myscan.txt` within this repository.
