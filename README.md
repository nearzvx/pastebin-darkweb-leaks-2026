# 16. Pastebin & Dark Web Data Leaks

## Classification
- **Category:** Data Leaks / Credential Dumps
- **Sources:** Pastebin, dark web forums, Brinztech breach alerts, Cybernews

---

## 16A. Leakbase Post-Takedown Fire Sale (May 2026)

**Size:** 10+ Terabytes
**Source:** Dark web forums (post-takedown)
**Platform:** Leakbase (seized by Europol/FBI March 2026)

### Background
Leakbase was a central hub in the cybercrime ecosystem with **142,000+ registered users** before international law enforcement seized it in March 2026. This 10TB dataset is a "post-takedown fire sale" by former VIP members or admins who maintained offline backups.

### Contents
- **Comprehensive PII ("Fullz")** -- names, addresses, SSNs
- **Financial intelligence** -- credit card details
- **Combo lists** -- massive username/password pairs
- **Database dumps** from multiple breaches
- **Active session cookies** -- can bypass MFA entirely

### Risk
- **Hyper-aggregation**: Consolidating terabytes of breached data into a single searchable repository
- **Session hijacking**: Active cookies bypass MFA
- **Credential stuffing**: Fed into automated botnets

---

## 16B. Tokoparts 79GB "Total Compromise" (May 2026)

**Victim:** Tokoparts (Indonesian automotive supply chain)
**Size:** 79 GB
**Date:** April 2026 (exfiltration), May 2026 (dumped)
**Source:** Dark web forum

### Contents
- **Source code** with hardcoded, still-active database credentials
- **Financial records**: bank statements, tax docs, P&L, supplier contracts
- **Identity data**: KTP (National IDs), NPWP (Tax IDs), employee data
- **Operational data**: logistics agreements, warehouse inventory, pricing

### Root Causes (a "perfect storm")
1. Outdated Magento plugin (CVE-2024-3412)
2. No MFA for executives
3. Default credentials on a backup server
4. Admin credentials found in a **public GitHub repository**

---

## 16C. Geexek 22GB Identity Registry (May 2026)

**Victim:** Geexek (China's primary alternative to Strava)
**Size:** 22 GB single table, **15 million user records**
**Source:** Dark web forum (for sale)
**Status:** Attacker maintains **active persistent access**

### Exposed Data
- Full legal names, dates of birth, **passport numbers**
- Personal and emergency contact details
- **Blood types** and shoe sizes
- **Plaintext passwords** for 15M accounts
- Active backdoor -- attacker claims continued access

---

## 16D. Arbiko Customer Database (May 2026)

**Victim:** Arbiko platform
**Source:** Dark web forum (dumped for free)

### Contents
- Email + password pairs (mix of plaintext and hashed)
- Unredacted customer names
- Personal and corporate email addresses

### Free Dump Strategy
The threat actor bypassed slow escrow negotiations and made the data **freely available** to all forum members, dramatically accelerating secondary attacks (credential stuffing, phishing).

---

## 16E. AlienBoot.net Booter Source (Pastebin)

**Date:** March 2018 (but still relevant)
**Source:** https://pastebin.com/PCLXkqdx

### Contents
Complete source code and database of **AlienBoot.net**, a DDoS booter/stresser service. Useful for understanding booter infrastructure and tracking related threats.

---

## 16F. OSINT Tools for Pastebin Monitoring

### PastebinSearch (byfranke/PastebinSearch)
**URL:** https://github.com/byfranke/PastebinSearch

An advanced OSINT tool for searching Pastebin:

| Feature | Detail |
|---------|--------|
| Multi-engine | DuckDuckGo, Google, Bing, direct Pastebin archive |
| Automation | Selenium with anti-bot evasion |
| Output | JSON and CSV export |
| Strategies | password, database, api, config, mysql, mongodb |

### pastebin_scraper (CyberOne-TeamARES)
**URL:** https://github.com/CyberOne-TeamARES/pastebin_scraper

Automated Pastebin monitoring for data leaks:
- Uses Pastebin API
- MySQL database backend
- Logs interesting pastes by type
- Requires Pastebin PRO account

### CVE-to-PoC Mapper
**URL:** https://apify.com/huntersreeni/cve-poc-mapper

Maps CVEs to publicly available PoC code by searching GitHub, ExploitDB, and NVD simultaneously.

---

## 16G. Vodafone Hardcoded Credentials

As detailed in `03-vodafone-lapsus-leak.md`, the Lapsus$ dump of Vodafone source code included **hardcoded PostgreSQL database credentials** in the codebase itself.

---

## Significance

These leaks demonstrate several alarming trends:
1. **Credential stuffing at scale** -- combo lists are fed into automated botnets within hours
2. **Session cookie theft** bypasses MFA entirely
3. **Persistent access** -- attackers maintain backdoors even after discovery
4. **Free dumps** accelerate secondary attacks dramatically
5. **GitHub credential exposure** remains a top attack vector
