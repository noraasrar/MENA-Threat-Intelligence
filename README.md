# 🛡️ MENA Threat Intelligence 

Welcome to my Cyber Threat Intelligence research hub focusing on Middle Eastern APT tradecraft, identity threat weaponization, and incident remediation strategies.

---

# CYBER THREAT INTELLIGENCE ADVISORY: HANDALA (VOID MANTICORE) MDM WEAPONIZATION
**TLP: AMBER** | **Analyst:** Nora | **Target Region:** MENA / Global Enterprise

---

## 1. Executive Summary (BLUF)
Threat actor **Handala** (tracked as *Void Manticore / BANISHED KITTEN*) has shifted tactics from compiled wiper malware to "Living-off-the-Cloud" identity weaponization. By compromising hyper-privileged tenant credentials, the actor executes global batch remote-wipe commands via Mobile Device Management (MDM) platforms (e.g., Microsoft Intune), bypassing traditional endpoint detection and response (EDR) controls.

---

## 2. Threat Actor Profile & Geopolitical Context
- **Attribution:** Front persona linked to the Iranian Ministry of Intelligence & Security (MOIS).
- **Strategy:** Fuses physical/cyber hacktivism personas with state-sponsored destructive capabilities to maximize psychological impact and public friction.
- **Target Sectors:** Healthcare, defense industrial base, energy, and telecommunications in the MENA region and allied Western entities.

---

## 3. Attack Lifecycle & TTPs (MITRE ATT&CK)

| Phase | Technique ID | Technique Name | Details |
|---|---|---|---|
| **Initial Access** | `T1078` / `T1566` | Valid Accounts / Phishing | Adversary-in-the-Middle (AiTM) credential harvesting; VPN access routed via Starlink nodes. |
| **Reconnaissance** | `T1003` / `T1087` | OS Credential Dumping / Account Discovery | Dumping LSASS process memory (`comsvcs.dll`) and running ADRecon scripts. |
| **Execution** | `T1651` / `T1485` | Management Deployment / Data Destruction | Accessing tenant admin consoles to issue batch "Factory Reset" commands to enrolled estates. |

---

## 4. Strategic Remediation & Hardening Controls
1. **Restrict Programmatic Remote Wipes:** Mandate Just-In-Time (JIT) access and multi-party quorum approvals for batch actions across Intune/Entra ID.
2. **Behavioral Telemetry Shift:** Implement SIEM detection rules alerting on high-volume spikes of device management API calls (e.g., >10 wipe requests in 60 minutes).
3. **Phishing-Resistant MFA:** Enforce Hardware FIDO2 Security Keys for all global and tenant administrative roles to eliminate AiTM phishing vectors.
