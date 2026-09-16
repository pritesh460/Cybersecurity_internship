## Footprinting & Network Scanning Phases

**W2-PM-FINAL | Cybersecurity | Networkwalks**

| **Pentester Name (Cybersecurity Professional)** | Pritesh Kalsariya |
|---|---|
| **Program/Batch** | B083-Networkwalks |
| **Date** | 13 Sept 2026 |
| **Modules Completed** | W2-PM1 (Multiple Kali Tools)<br>W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network |
| **Permission Secured from Client?** | Yes |
| **Phases Covered** | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery |

---

# 1. Liability Disclaimer

I have performed these activities only on systems and devices where I had secured written permission or on devices/systems that I own myself.

All materials are provided for educational and research purposes only. Do not use anything from this report to break the law.

The instructor, authors, and Networkwalks are not responsible for misuse of the information provided in this report. Every action taken using this knowledge is the user's own responsibility.

Unauthorized access to computer systems can result in criminal charges, financial penalties, loss of employment, and other legal consequences.

---

# 2. Introduction

This report covers the **footprinting of the networkwalks.com domain** using multiple Kali Linux tools (W2-PM1) and **scanning of my own local network** using Zenmap (W2-PM5).

One module covers the footprinting phase and the other covers the scanning phase. Together, they demonstrate how a security professional can move from gathering publicly available information to discovering live hosts on a network.

This report represents the **Week 2** part of my ongoing cybersecurity internship program at Networkwalks.

All commands were performed using **Kali Linux** for footprinting and a **Windows PC with Zenmap** installed for network scanning.

Each activity includes:

- The command or procedure used
- The observed result
- Screenshot evidence
- Security relevance from a penetration-testing perspective

---

# 3. Tools Used

| **Tool** | **Purpose** |
|---|---|
| **Kali Linux & Windows** | Operating systems used for reconnaissance and scanning activities |
| **WHOIS** | Find publicly available domain registration details, dates, and name servers |
| **WhatWeb** | Fingerprint web technologies such as servers, CMS platforms, plugins, and IP information |
| **Nslookup** | Resolve a domain name to its IP address using DNS |
| **Curl -I** | Inspect HTTP response headers from a website |
| **Wafw00f** | Detect whether a Web Application Firewall protects the website |
| **DNSRecon** | Enumerate DNS records such as NS, MX, SPF, TXT, and SRV records |
| **Zenmap (Nmap GUI)** | Scan the local subnet to identify live hosts, IP addresses, and MAC addresses |
| **Windows CMD** | Identify local IP address and MAC address information |

---

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

I performed reconnaissance against the **networkwalks.com** domain using six Kali Linux tools:

- **WHOIS**
- **WhatWeb**
- **Nslookup**
- **Curl**
- **Wafw00f**
- **DNSRecon**

Each tool was used to collect a different type of information about the target.

### WHOIS

First, I used **WHOIS** to obtain publicly available domain registration information and identify the domain's name servers.

The results provided information about the domain registration and hosting infrastructure.

### WhatWeb

I then used **WhatWeb** to identify technologies used by the website.

The results identified:

- **WordPress 7.0.4**
- **WP Download Manager 3.3.58**
- Other information exposed by the website

### Nslookup

Using **Nslookup**, I resolved the domain name to its IP address.

The provided result identified:

```text
192.232.216.135
```

### Curl

I used **Curl** with the `-I` option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint `/wp-json/`.

### Wafw00f

Next, I used **Wafw00f** to determine whether a Web Application Firewall was protecting the website. The result identified **ModSecurity (SpiderLabs)**.

### DNSRecon

Finally, I used **DNSRecon** to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records, and DNS software information.

---

## 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:

- `10.0.0.1`
- `10.0.0.4`
- `10.0.0.19`
- `10.0.0.5`

The example results also included four MAC addresses.

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

---

# 7. Conclusion

During **Week 2 of my Cybersecurity & Ethical Hacking internship**, I completed practical activities covering **footprinting, reconnaissance, and network scanning**.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how **WHOIS** can provide domain information, **WhatWeb** can identify web technologies, **Nslookup** can resolve domain names, **Curl** can inspect HTTP headers, **Wafw00f** can identify a WAF, and **DNSRecon** can provide additional DNS information.

In the network scanning activity, I used **Zenmap** to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain **what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk**.

Finally, I learned that reconnaissance and scanning must always be performed within an **authorized scope**. These activities were completed as part of the assigned educational cybersecurity lab.

---

# 8. Evidence Collected

### 📸 Screenshots & Evidence

> Add your screenshots and evidence below.

![Evidence 1](./images/evidence-1.png)

![Evidence 2](./images/evidence-2.png)

![Evidence 3](./images/evidence-3.png)

![Evidence 4](./images/evidence-4.png)

---

## 👤 Author

**pritesh Kalsariya**  
Cybersecurity Professional — B083

**LinkedIn:** [www.linkedin.com/in/pritesh-kalsariya-4529a833b](https://www.linkedin.com/in/pritesh-kalsariya-4529a833b)

---

## 📌 Project Information

| **Field** | **Details** |
|---|---|
| **Program Name** | Cybersecurity Program at Networkwalks |
| **Week** | 02 |
| **Focus** | Footprinting & Network Scanning |
| **Repository** | GitHub |
