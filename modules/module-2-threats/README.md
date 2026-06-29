# Module 2: Threat Modeling for Sub-National Payment Rails

## 📌 Overview
In the West African informal economy, financial inclusion is primarily driven by low-bandwidth, decentralized payment rails. While high-income demographics rely on encrypted banking applications, the "last mile" operates almost entirely on Unstructured Supplementary Service Data (USSD), SMS, and Agency Banking (POS kiosks). 

This module deconstructs the specific cybersecurity vulnerabilities inherent in these sub-national payment rails and establishes localized, data-driven threat models to protect grassroots financial actors.

---

## 📱 1. USSD Vulnerabilities: The Unencrypted Frontier

USSD operates as a real-time session between a mobile device and the network operator. Because it was originally designed for basic network querying, it lacks end-to-end encryption, making it a highly exploitable channel for financial routing.

### 🔴 Primary Attack Vectors
* **SS7 Protocol Exploitation:** The underlying Signaling System 7 (SS7) network architecture is notoriously vulnerable to interception. Attackers with network access can intercept USSD session tokens and route bank authorization prompts to rogue devices.
* **SIM Swapping & Session Hijacking:** By socially engineering telecom agents, attackers port a victim's number to a new SIM card, gaining immediate control over all USSD-linked banking infrastructure and two-factor authentication (2FA) codes.
* **Malicious MMI Strings (USSD Phishing):** The recent industry-wide transition to updated, unified USSD recharge and service systems—replacing fragmented legacy codes—successfully reduced the attack surface for generic shortcode spoofing. However, attackers continue to deploy malicious USSD strings via deceptive SMS broadcasts, tricking users into dialing codes that inadvertently authorize fund transfers.

### 🟢 Defensive Protocols
* **Time-Based Session Timeouts:** Enforcing strict, aggressive session timeouts for financial USSD queries to minimize the window for interception.
* **Out-of-Band Authentication:** Requiring secondary confirmation (such as a localized physical token or biometric prompt) for high-value USSD transfers.

---

## 💬 2. SMS-Based Threats: The Human Exploit

In the absence of internet banking, SMS serves as the primary ledger of truth for informal economic actors. If an SMS says money has been received, goods are released. This visual trust model is highly susceptible to manipulation.

### 🔴 Primary Attack Vectors
* **Alphanumeric Sender ID Spoofing:** Attackers bypass standard telecom filters to send SMS alerts that perfectly mimic the sender ID of major commercial banks (e.g., "FirstBank" or "GTBank"). 
* **Synthetic Credit Alerts:** Tailored specifically against local merchants, attackers generate mathematically accurate but entirely fabricated SMS credit alerts. The merchant releases goods based on the fake text before checking their actual account balance.
* **Smishing (SMS Phishing):** Distributing links to cloned fintech portals disguised as mandatory account upgrades or digital rights verification forms.

### 🟢 Defensive Protocols
* **Cryptographic Verification:** Shifting merchants away from "visual trust" (reading a text) toward independent ledger verification (checking an active, secure channel).
* **Behavioral Network Anomalies:** Deploying network traffic analysis rules to flag sudden spikes in localized spoofed sender IDs within specific geographic cells.

---

## 🏪 3. Agency Banking Kiosks: Human-in-the-Middle (HitM)

Point of Sale (POS) agents serve as the human ATM network across Nigeria. While this decentralization solves access issues, it introduces severe physical and digital vulnerabilities.

### 🔴 Primary Attack Vectors
* **Hardware Skimming & Firmware Tampering:** Exploitation of poorly regulated, low-cost POS terminals that are injected with keyloggers capable of capturing PINs and card track data.
* **The Rogue Agent (HitM):** Malicious operators who capture over-the-shoulder PIN entries or execute unauthorized dual-transactions while a customer is distracted.
* **Denial of Service via Connectivity:** Agents falsely claiming "network failure" to force users to repeat transactions, intentionally causing duplicate debits which the agent later exploits.

### 🟢 Defensive Protocols
* **Agent Cryptographic Identity:** Ensuring POS terminals are hard-locked to verified biometric identities, preventing the secondary sale of terminals to unverified actors.
* **Consumer Recourse Frameworks:** Establishing standardized, accessible digital rights protocols that allow unbanked users to dispute fraudulent POS debits without navigating complex corporate banking bureaucracy.

---

## 📊 Analytics & Next Steps
Understanding these threats is only the first step. In **Module 3**, we will explore how integrating decentralized, open-source payment standards like the **Interledger Protocol (ILP)** can bypass many of these legacy vulnerabilities, establishing a verifiable, low-friction trust layer for the informal economy.
