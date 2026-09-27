<div align="center">

# Gurvin Singh

<img src="https://readme-typing-svg.demolab.com?font=Share+Tech+Mono&size=15&duration=2600&pause=800&color=00FF41&center=true&vCenter=true&width=560&lines=Detection+Engineering+%7C+Blue+Team;Wazuh+%7C+Sigma+%7C+Python;I+build+the+sensor%2C+the+detection%2C+the+case+file" alt="Detection Engineering | Blue Team. Wazuh | Sigma | Python. I build the sensor, the detection, the case file."/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logoColor=white)](https://www.linkedin.com/in/gurvin-s-6a02b3278/)
![Location](https://img.shields.io/badge/📍_NYC-Blue_Team-0077B5?style=flat-square&labelColor=0D1117)

</div>

**CySA+ and Security+ certified blue-team defender.** I build my own SOC, then break it,
investigate it, and harden it. Every step is documented in public.
Open to SOC Analyst and Detection Engineering roles — NYC or remote.

---

### 👻 SPECTRE: WiFi intrusion detection, built end to end

<table>
<tr>
<td width="50%" valign="top">

<p>Two ESP32-C5 boards run custom promiscuous-mode firmware and stream 802.11 frame metadata
over UART into a <b>stdlib-only FastAPI detection engine</b> (deauth flood, evil twin,
beacon/probe flood and RSSI anomaly rules), which forwards scored threats to
<b>Wazuh over RFC 5424</b> and drives a Next.js SOC console.</p>

<p>Sensor to SIEM to analyst view, every layer mine. Two of the four detections map to ATT&amp;CK: <b>T1557</b> (evil twin) and <b>T1499</b> (deauth flood).</p>

<p><i>Run against my own network only, on hardware I own. The sensor forwards threats and
summaries, <b>never raw frames</b>: the SIEM stores decisions, not a packet archive.</i></p>

<p>
<img src="https://img.shields.io/badge/License-AGPL--3.0-005E7A?style=flat-square&labelColor=0D1117" alt="AGPL-3.0"/>
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
<a href="https://github.com/gurvinny/spectre/actions/workflows/codeql.yml"><img src="https://img.shields.io/github/actions/workflow/status/gurvinny/spectre/codeql.yml?branch=main&style=flat-square&label=CodeQL&labelColor=0D1117" alt="CodeQL"/></a>
<a href="https://github.com/gurvinny/spectre/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/gurvinny/spectre/ci.yml?branch=main&style=flat-square&label=CI&labelColor=0D1117" alt="CI"/></a>
<a href="https://github.com/gurvinny/spectre/actions/workflows/browser-qa.yml"><img src="https://img.shields.io/github/actions/workflow/status/gurvinny/spectre/browser-qa.yml?branch=main&style=flat-square&label=browser%20QA&labelColor=0D1117" alt="Browser QA"/></a>
</p>

<p><b><a href="https://github.com/gurvinny/spectre">→ github.com/gurvinny/spectre</a></b></p>

</td>
<td width="50%" valign="top">
<a href="https://github.com/gurvinny/spectre">
<img width="100%" src="https://raw.githubusercontent.com/gurvinny/spectre/main/docs/screenshots/02-command-center.png" alt="SPECTRE command center: live threat feed, device inventory and spectrum view"/>
</a>
</td>
</tr>
</table>

---

### 🗺️ Where it ships to: the detection pipeline

SPECTRE is one source among several. Everything lands in a self-built SOC running on a single
Proxmox node behind a pfSense perimeter, five VLAN segments, default-deny between them.

```mermaid
flowchart LR
    EP["Linux / Windows hosts<br/><i>Wazuh agents · FIM · auditd · SCA</i>"] --> SIEM
    FWL["pfSense<br/><i>firewall + DNS logs</i>"] --> SIEM
    RF["SPECTRE sensor<br/><i>ESP32-C5 WiFi · RFC 5424</i>"] --> SIEM

    SIEM["<b>Wazuh SIEM + XDR</b><br/>decoders · normalisation · correlation"]
    SIEM --> RULES["Detection logic<br/><i>Wazuh rulesets · MITRE ATT&amp;CK mapping</i>"]
    RULES --> SEV{"Triage"}
    SEV -->|true positive| IR["Preserve · contain · eradicate<br/><i>evidence first, then isolate</i>"]
    SEV -->|false positive| TUNE["Tune<br/><i>refine rule · allowlist</i>"]
    SEV -->|benign true positive| DOC["Document &amp; close<br/><i>so it is not re-investigated</i>"]
    TUNE --> RULES
    IR --> CASE["Case writeup<br/><i>NIST SP 800-61 · published</i>"]

    classDef src fill:#0D1117,stroke:#455A64,color:#E6EDF3
    classDef core fill:#161B22,stroke:#008F11,color:#E6EDF3
    classDef out fill:#161B22,stroke:#0077B5,color:#E6EDF3
    class EP,FWL,RF src
    class SIEM,RULES,IR,TUNE,DOC core
    class CASE out
```

---

<div align="center">

### 🔬 More work: *what each project proves*

<table align="center">
<thead>
<tr><th></th><th align="left">Project</th><th align="left">What it proves</th></tr>
</thead>
<tbody>
<tr>
  <td align="center">🛡️</td>
  <td><b><a href="https://github.com/gurvinny/security-analyst-portfolio">Security Analyst Portfolio</a></b></td>
  <td>Detection engineering: IR playbooks · NIST writeups · ATT&amp;CK-mapped detection logic</td>
</tr>
<tr>
  <td align="center">🐍</td>
  <td><b><a href="https://github.com/gurvinny/Automated-Phish-Extractor">Automated Phish Extractor</a></b></td>
  <td>Tier-1 SOC triage: .eml parsing, IOC defang, SPF/DMARC in 30s</td>
</tr>
<tr>
  <td align="center">🛸</td>
  <td><b><a href="https://github.com/gurvinny/pelican-deepfield">Pelican Deepfield</a></b></td>
  <td>Theme plugin for a game-server control panel. Shipping discipline: semver releases, tagged and changelogged</td>
</tr>
<tr>
  <td align="center">🏠</td>
  <td><b><a href="https://github.com/gurvinny/home-network-lab">Home Network Lab</a></b></td>
  <td>Defense-in-depth: VLAN segmentation · default-deny routing · centralized logging</td>
</tr>
</tbody>
</table>

</div>

---

<div align="center">

### 🔧 Recent work

<pre>
╔════════════════════════════════════════════════════════════╗
║ HARDENING SPECTRE supply chain + code scanning             ║
║           2026-09-12 -> 2026-09-14                         ║
╠════════════════════════════════════════════════════════════╣
║ PROBLEM   No code scanning configured at all · deps        ║
║           drifting until an advisory caught them           ║
║ FOUND     next 15.5.20 carried 10 advisories, two          ║
║           critical unauthenticated RCE:                    ║
║           GHSA-2xp9-vwfh-vxw4  image optimizer, AVIF       ║
║               WAS EXPLOITABLE · image route live until fix ║
║           CVE-2026-75604       windows-hosted server       ║
║               NOT APPLICABLE · Linux containers only       ║
║               patched anyway                               ║
║ FIXED     Bumped to 15.5.25 · used npm overrides to        ║
║           force patched versions of 4 transitive deps      ║
║           Disabled the image optimizer outright,           ║
║           dropping /_next/image from the attack surface    ║
╠════════════════════════════════════════════════════════════╣
║ CONTROLS  CodeQL: JS/TS · Python · Actions                 ║
║           Dependabot across five ecosystems                ║
║           Browser QA promoted to a required check          ║
║ STATUS    RESOLVED · 0 open advisories                     ║
╚════════════════════════════════════════════════════════════╝
</pre>

<sub><a href="https://github.com/gurvinny/spectre/pull/20"><b>PR #20</b></a></sub>

</div>

---

<div align="center">

### 🔎 Investigation

<pre>
╔════════════════════════════════════════════════════════════╗
║ OUTAGE    Wazuh SIEM full pipeline failure                 ║
║           2026-04-24                                       ║
╠════════════════════════════════════════════════════════════╣
║ PROBLEM   0 dashboard entries · all services active        ║
║ CAUSE     Admin hash mismatch · missing OpenSearch role    ║
║           Dashboard keystore overriding yml config         ║
║ FIXED     Auth chain repaired · roles created              ║
║           Keystore updated · auditd conflicts resolved     ║
╠════════════════════════════════════════════════════════════╣
║ RESULT    Log pipeline restored · alerting end to end      ║
║ HARDENED  CIS Ubuntu 24.04 L1    83.0% -> 88.9%            ║
║           USG Level 2 Server           90.98%              ║
║             435 of 471 rules · 36 open (34 med, 2 high)    ║
║ STATUS    RESOLVED                                         ║
╚════════════════════════════════════════════════════════════╝
</pre>

<sub><a href="https://github.com/gurvinny/security-analyst-portfolio/tree/main/investigations/wazuh-siem-recovery-2026-04"><b>Full case study</b></a></sub>

</div>

---

<div align="center">

### 🎖️ Credentials & tooling

**B.S. Cybersecurity & Information Assurance** · Western Governors University · expected 02/2027

[![CySA+](https://img.shields.io/badge/CompTIA_CySA%2B-C8202F?style=flat-square&logo=comptia&logoColor=white)](https://www.credly.com/earner/earned/badge/8ff86bbc-133d-46b6-b91e-7475ded8ed63)
[![Security+](https://img.shields.io/badge/CompTIA_Security%2B-C8202F?style=flat-square&logo=comptia&logoColor=white)](https://www.credly.com/earner/earned/badge/3714ff8f-276c-47f4-ac49-b1551eefefcc)
[![Network+](https://img.shields.io/badge/CompTIA_Network%2B-C8202F?style=flat-square&logo=comptia&logoColor=white)](https://www.credly.com/earner/earned/badge/7d61a205-31d0-4a51-bd04-3e227f634e3c)
[![A+](https://img.shields.io/badge/CompTIA_A%2B-C8202F?style=flat-square&logo=comptia&logoColor=white)](https://www.credly.com/earner/earned/badge/e33d46ab-136c-4ed0-a7e2-ad82078659ab)

[![THM101](https://img.shields.io/badge/TryHackMe-Cyber_Security_101-212C42?style=flat-square&logo=tryhackme&logoColor=white)](https://tryhackme-certificates.s3-eu-west-1.amazonaws.com/THM-BPY9Y4IOOB.pdf)
[![THMrooms](https://img.shields.io/badge/121_rooms-top_3%25-008F11?style=flat-square&labelColor=0D1117)](https://tryhackme.com/p/gurvin)
![CIS](https://img.shields.io/badge/CIS_Ubuntu_24.04_L1-88.9%25-008F11?style=flat-square&labelColor=0D1117)
![USG](https://img.shields.io/badge/USG_Level_2_Server-90.98%25-008F11?style=flat-square&labelColor=0D1117)

<sub>USG = Ubuntu Security Guide, Level 2 Server profile. CIS = Center for Internet Security benchmark. Both scores are from audits run against my own hosts.</sub>

<br/>

**Detection & response**
![Wazuh](https://img.shields.io/badge/Wazuh-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![Splunk](https://img.shields.io/badge/Splunk-374151?style=flat-square&logo=splunk&logoColor=9CA3AF) *(learning)*
![Sigma](https://img.shields.io/badge/Sigma-005E7A?style=flat-square&logoColor=white)
![MITRE](https://img.shields.io/badge/MITRE_ATT%26CK-FF0000?style=flat-square&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=flat-square&logo=wireshark&logoColor=white)

**Network & systems**
![pfSense](https://img.shields.io/badge/pfSense-2C3E50?style=flat-square&logoColor=white)
![VLAN](https://img.shields.io/badge/VLAN_Segmentation-455A64?style=flat-square&logoColor=white)
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=flat-square&logo=proxmox&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

**Build**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)

</div>

---

<div align="center">

### 🎧 Beyond security

**[Slo-Fi](https://slofi.live)** is a real-time audio engine that runs entirely in your browser.
Nothing ever leaves the machine: no upload, no account, no server to breach. Cloudflare
Workers serves static assets only; there is no server-side code.

Held to the same bar as the security work. **550+ assertions across five test layers**, each
layer floored independently in CI so a collapse in one cannot hide behind another's volume.

<img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
<img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logoColor=white" alt="Playwright"/>
<img src="https://img.shields.io/badge/Cloudflare_Workers-F38020?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare Workers"/>

**[slofi.live](https://slofi.live)** · **[source](https://github.com/gurvinny/Slo-Fi)**

</div>

---

<div align="center">
<sub>Security concerns: see the <a href="https://github.com/gurvinny/.github/blob/main/SECURITY.md">security policy</a>. Issues are disabled on this repository.</sub>
</div>
