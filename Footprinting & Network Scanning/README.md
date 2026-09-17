<div align="center">

# 🔐 PENETRATION TESTING REPORT
## Footprinting & Network Scanning Phases

</div>

| **Field** | Details |
|---|---|
| **Author** | Pritesh Kalsariya |
| **Program/Batch** | B083-Networkwalks |
| **Date** | 13 Sept 2026 |
| **Modules Completed** | W2-PM1 (Multiple Kali Tools)<br>W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network |
| **Permission Secured from Client?** | Yes |
| **Phases Covered** | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>**Phase 3-5:** In Progress |

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

- `10.17.252.177`
- `10.17.252.27`


After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

---

# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential security observations.

| **#** | **Risk / Finding** | **Evidence / Observation** | **Potential Impact** | **Risk Level** |
|---:|---|---|---|:---:|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager | Attackers may use exposed technology/version information to identify software requiring further security review | **🟠 Medium** |
| 2 | Server IP address identifiable | Nslookup resolved the domain to `192.232.216.135` | Provides information about the network location of the web service | **🟢 Low** |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration | **🟢 Low** |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application's security architecture | **🟢 Low** |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, and service-related records | DNS information can help build a broader infrastructure profile | **🟠 Medium** |
| 6 | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network | Unknown or unauthorized devices may potentially be present on a network | **🟠 Medium** |

### Risk Level Key

- 🔴 **Critical**
- 🟠 **Medium**
- 🟢 **Low**

The practical exercises primarily involved **information gathering and host discovery**. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address, or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

---

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

### 1. Review Publicly Exposed Technology Information

Organizations should regularly review what information about their web technologies, CMS platforms, and plugins is publicly visible.

### 2. Keep Software Updated

CMS platforms, plugins, and other web technologies should be regularly updated and reviewed against current security advisories.

### 3. Review HTTP Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Review DNS Records Regularly

DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

### 5. Properly Configure and Monitor the WAF

Keep the WAF (ModSecurity) enabled and properly configured. WAF rules should be regularly reviewed, tuned, and monitored.

### 6. Perform Regular Internal Network Discovery

Organizations should periodically scan their own networks to identify active devices and maintain visibility of the internal environment.

### 7. Investigate Unknown Devices

Any unexpected device discovered during network scanning should be investigated and verified.

### 8. Maintain Network Documentation

Network topology and device information should be documented and updated regularly.

### 9. Perform Security Testing with Authorization

Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

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

![Evidence 1](1_whois_Reconnaissance.png)

![Evidence 2](2_whatweb_Reconnaissance.png)

![Evidence 3](3_nslookup_Reconnaissance.png)

![Evidence 4](4_curl_Reconnaissance.png)

![Evidence 5](5_wafw00f_Reconnaissance.png)

![Evidence 6](6_dnsrecon_Reconnaissance.png)

![Evidence 7](7_Network_Scanning.png)

![Evidence 8](8_topology_Network_Scanning.png)

---

## 👤 Author

**pritesh Kalsariya**  
Cybersecurity Professional — B083

**LinkedIn:** [www.linkedin.com/in/pritesh-kalsariya-4529a833b](https://www.linkedin.com/in/pritesh-kalsariya-4529a833b)

---

## 📌 Project Information

**Program Name:** Cybersecurity Program at Networkwalks | **Week:** 02 | **Focus:** Footprinting & Network Scanning | **Repository** GitHub |
