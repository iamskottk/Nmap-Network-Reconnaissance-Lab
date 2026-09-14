# 🔎 Nmap Network Reconnaissance Lab

![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-blue)
![Nmap](https://img.shields.io/badge/Tool-Nmap-red)
![Kali Linux](https://img.shields.io/badge/Platform-Kali%20Linux-black)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 👤 Author

### Kabo Sekoto
**🔐 Junior Cybersecurity Practitioner**

> `Learning → Building → Testing → Securing`

This repository forms part of my practical cybersecurity learning portfolio, documenting hands on labs, security experiments and technical progression.

### 🌐 Cybersecurity Journey

<p align="center">
  <a href="https://linkedin.com/in/kabosekoto">
    <img src="https://img.shields.io/badge/🔵_LinkedIn-Professional%20Profile-0A66C2?style=for-the-badge" />
  </a>
  &nbsp;
  <a href="https://www.youtube.com/@IamSkottK">
    <img src="https://img.shields.io/badge/🔴_YouTube-Cybersecurity%20Lab-FF0000?style=for-the-badge" />
  </a>
</p>


---

## 📌 Project Overview

This project demonstrates the use of **Nmap (Network Mapper)** for network reconnaissance and security assessment within a controlled laboratory environment.

The objective is to identify:

* Live hosts
* Open ports
* Running services
* Service versions
* Potentially exposed network services

> ⚠️ **Ethical Notice:** Nmap should only be used against systems and networks that you own or have explicit permission to test.

---

## 🎯 Objectives

* Perform basic network reconnaissance
* Discover active hosts
* Identify open TCP ports
* Identify running services
* Perform service/version detection
* Perform basic OS detection
* Analyse network exposure
* Document security findings

---

## 🧪 Lab Environment

| Component        | Details                      |
| ---------------- | ---------------------------- |
| Operating System | Kali Linux                   |
| Virtualisation   | Oracle VirtualBox            |
| Tool             | Nmap                         |
| Network          | Host-only / NAT lab network  |
| Target           | Authorised laboratory system |
| Example Network  | `192.168.56.0/24`            |

---

# 🔹 Phase 1 — Identify Network Configuration

First, identify the Kali Linux network interface and IP address.

```bash
ip addr
```

Alternative:

```bash
ifconfig
```

Example:

```text
192.168.56.10/24
```

The `/24` indicates the subnet:

```text
192.168.56.0/24
```

---

# 🔹 Phase 2 — Host Discovery

Use Nmap to identify active hosts on the authorised laboratory network.

```bash
nmap -sn 192.168.56.0/24
```

### What this does

The `-sn` option performs host discovery without performing a port scan.

It helps identify which systems are currently online.

Example:

```text
Nmap scan report for 192.168.56.10
Host is up.

Nmap scan report for 192.168.56.20
Host is up.
```

---

# 🔹 Phase 3 — Port Scanning

After identifying an authorised target, perform a basic port scan.

```bash
nmap 192.168.56.20
```

Example results:

```text
PORT    STATE    SERVICE
22/tcp  open     ssh
80/tcp  open     http
443/tcp open     https
```

### Interpretation

| Port | Service | Security Consideration                     |
| ---- | ------- | ------------------------------------------ |
| 22   | SSH     | Remote administration should be restricted |
| 80   | HTTP    | Unencrypted web traffic                    |
| 443  | HTTPS   | Secure web communication                   |

> An open port does **not automatically mean that the system is vulnerable**. Further investigation is required.

---

# 🔹 Phase 4 — Service and Version Detection

Use Nmap service detection to identify the software running behind open ports.

```bash
nmap -sV 192.168.56.20
```

Example:

```text
22/tcp  open  ssh    OpenSSH
80/tcp  open  http   Apache HTTP Server
443/tcp open  https  Apache HTTP Server
```

Service/version detection can help identify software that may require:

* Security updates
* Configuration changes
* Vulnerability assessment
* Service hardening

---

# 🔹 Phase 5 — Operating System Detection

Attempt to identify the target operating system.

```bash
sudo nmap -O 192.168.56.20
```

Example:

```text
OS details: Linux
```

> OS detection may require elevated privileges and may not always be accurate.

---

# 🔹 Phase 6 — Combined Scan

A more detailed reconnaissance scan can combine service and OS detection.

```bash
sudo nmap -sV -O 192.168.56.20
```

This provides additional information about the target's:

* Open ports
* Services
* Service versions
* Possible operating system

---

# 🔎 Security Findings

Example findings from the laboratory scan:

| Finding          | Risk Consideration              | Recommended Control                  |
| ---------------- | ------------------------------- | ------------------------------------ |
| SSH exposed      | Remote administration available | Restrict access using firewall rules |
| HTTP exposed     | Unencrypted communication       | Redirect to HTTPS where appropriate  |
| HTTPS exposed    | Web service accessible          | Keep TLS and web server patched      |
| Outdated service | Possible security exposure      | Apply vendor security updates        |

> **Note:** Replace these example findings with the actual results obtained from the authorised laboratory scan.

---

# 🛡️ Recommended Security Controls

Based on network reconnaissance findings, organisations should consider:

* Firewall restrictions
* Network segmentation
* Least-privilege access
* Secure remote administration
* Service hardening
* Regular patch management
* Vulnerability assessments
* Centralised logging and monitoring
* IDS/IPS controls
* Regular network security assessments

---
# 🧰 Commands Used

```bash
ip addr

nmap -sn 192.168.56.0/24

nmap 192.168.56.20

nmap -sV 192.168.56.20

sudo nmap -O 192.168.56.20

sudo nmap -sV -O 192.168.56.20
```

---

# 🧠 What I Learned

Through this project I gained practical experience with:

* Network reconnaissance
* Host discovery
* TCP port scanning
* Service identification
* Service/version detection
* Basic OS detection
* Network exposure analysis
* Security risk identification
* Security recommendations
* Technical documentation

This project also builds on my existing **IT infrastructure and networking experience** while developing practical cybersecurity skills.

---

# 💻 Skills Demonstrated

```text
Networking
    ↓
Network Reconnaissance
    ↓
Nmap
    ↓
Service Identification
    ↓
Security Analysis
    ↓
Risk Assessment
    ↓
Security Recommendations
```

---

# 🚀 Future Improvements

Future versions of this laboratory may include:

* Nmap vulnerability scanning
* Nmap NSE scripts
* Wireshark traffic analysis
* Service enumeration
* Firewall testing
* Network segmentation testing
* Vulnerability management
* SIEM integration
* Automated reconnaissance reporting

---

# ⚖️ Ethical & Legal Disclaimer

This project was created for **educational and authorised security testing purposes**.

Nmap scans should only be performed against systems and networks where you have explicit permission to conduct security testing.

Unauthorised scanning may violate organisational policies or applicable laws.

---

## 📚 References

> Official documentation and industry frameworks referenced throughout this project.

- 🌐 [**Nmap**](https://nmap.org/) — Network discovery and security auditing
- 📖 [**Nmap Reference Guide**](https://nmap.org/book/man.html) — Official Nmap documentation
- 🐉 [**Kali Linux**](https://www.kali.org/) — Penetration testing and security platform
- 🛡️ [**MITRE ATT&CK**](https://attack.mitre.org/) — Adversary tactics and techniques framework
---

# 🏁 Conclusion

This project demonstrates a practical network reconnaissance workflow using Nmap:

**DISCOVER → SCAN → ENUMERATE → ANALYSE → ASSESS → DOCUMENT → SECURE**

The exercise strengthens practical networking and cybersecurity skills and forms part of my transition from **IT Administration to Cybersecurity**.

---

## 📌 Project Status

**Status:** ✅ Completed

**Environment:** Controlled Cybersecurity Laboratory

**Primary Tool:** Nmap

**Platform:** Kali Linux

**Portfolio:** Cybersecurity Practical Learning

---

