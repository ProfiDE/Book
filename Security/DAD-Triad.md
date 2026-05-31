# DAD Triad

The **DAD Triad** is the attacker's counterpart to the [CIA Triad](CIA-Triad.md). Where CIA describes what defenders try to preserve, DAD describes what attackers try to violate. The name comes from the first letters of its three pillars:

- **Disclosure**
- **Alteration**
- **Denial**

Together, these principles help security teams understand how systems fail and how to prioritize defenses against common threat goals.

## Disclosure

**Disclosure** means exposing information to unauthorized people or systems—the opposite of **confidentiality**.

The attacker's goal is to read, steal, or leak data that should remain private. Sensitive information such as credentials, personal records, financial data, or intellectual property becomes valuable once it is disclosed.

Common attacks that target disclosure include:

- Phishing and credential theft
- SQL injection and data exfiltration
- Insider threats and accidental leaks
- Unencrypted traffic interception

**Example:** An attacker exploits a misconfigured cloud storage bucket and downloads thousands of customer records. No data was changed and the service stayed online, but **disclosure** occurred.

## Alteration

**Alteration** means changing information in an unauthorized way—the opposite of **integrity**.

The attacker's goal is to tamper with, corrupt, or falsify data so that users and systems can no longer trust it. Alteration can be subtle (changing a single transaction) or obvious (defacing a website).

Common attacks that target alteration include:

- Malware that modifies system or application files
- Man-in-the-middle attacks that change data in transit
- Privilege escalation to edit protected records
- Supply-chain compromises that inject malicious code

**Example:** An attacker gains access to a news website's CMS and changes headlines before publication. The site remains available and no customer database was stolen, but **alteration** has undermined trust in the content.

## Denial

**Denial** means blocking or disrupting access to systems, applications, or data—the opposite of **availability**.

The attacker's goal is to make resources unreachable for legitimate users. Denial can be temporary or prolonged, targeted or widespread.

Common attacks that target denial include:

- Distributed denial-of-service (DDoS) attacks
- Ransomware that encrypts files and locks users out
- Deleting or destroying critical infrastructure
- Resource exhaustion (CPU, memory, bandwidth)

**Example:** A botnet floods an e-commerce site with traffic until it crashes. No data was stolen or modified, but customers cannot place orders—**denial** of service has succeeded.

## How the Three Principles Work Together

Real-world attacks often threaten more than one pillar of the DAD Triad at once:

| Scenario | Principles affected |
|----------|---------------------|
| Ransomware | **Denial** (encrypted files), often **Alteration** (data changed), sometimes **Disclosure** (data exfiltrated before encryption) |
| Data breach with website defacement | **Disclosure** (stolen records) and **Alteration** (changed public pages) |
| DDoS during a credential-stuffing campaign | **Denial** (site offline) while attackers attempt **Disclosure** (account access) |

Mapping an incident to DAD helps clarify what the attacker achieved and what recovery steps are needed.

## DAD and CIA: Two Sides of the Same Model

The DAD Triad is not a separate framework—it mirrors CIA from the attacker's perspective:

| CIA (defend) | DAD (attack) |
|--------------|--------------|
| Confidentiality | Disclosure |
| Integrity | Alteration |
| Availability | Denial |

When planning defenses, each CIA control should address the corresponding DAD threat. Encryption protects **confidentiality** against **disclosure**. Hashing and signatures protect **integrity** against **alteration**. Backups and redundancy protect **availability** against **denial**.

## Why the DAD Triad Matters

The DAD Triad provides a simple framework for:

- Analyzing attacker goals and threat models
- Classifying incidents by what was actually compromised
- Prioritizing controls based on likely attack outcomes
- Communicating impact to stakeholders in clear terms

When responding to an incident, asking *"Which part of the DAD Triad did the attacker achieve?"* helps focus containment and recovery. A phishing attack that only harvested credentials threatens **disclosure**. A defaced homepage threatens **alteration**. A flood of junk traffic threatens **denial**.

## Beyond the Triad

Like the CIA Triad, DAD is a starting point—not the full picture of modern threats. Other attacker goals—such as **repudiation** (denying actions), **fraud**, or **espionage for strategic advantage**—do not fit neatly into three letters. Still, most attacks map back to disclosure, alteration, or denial in some way.

Understanding the DAD Triad alongside the CIA Triad helps you think systematically about both defense and offense in information security.
