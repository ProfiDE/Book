# CIA Triad

The **CIA Triad** is a foundational model in information security. It describes three core principles that organizations use to protect systems, data, and services. The name comes from the first letters of its three pillars:

- **Confidentiality**
- **Integrity**
- **Availability**

Together, these principles help security teams decide what to protect, how to protect it, and how to measure whether protection is working.

## Confidentiality

**Confidentiality** means keeping information private and accessible only to authorized people or systems.

The goal is to prevent unauthorized disclosure. Sensitive data—such as passwords, medical records, financial details, or trade secrets—should not be visible to attackers, competitors, or anyone without a legitimate need to know.

Common controls that support confidentiality include:

- Encryption (in transit and at rest)
- Access control lists and role-based permissions
- Authentication (passwords, MFA, biometrics)
- Data classification and labeling

**Example:** A hospital stores patient records in a database. Only doctors and authorized staff can view them. If an outsider gains access, confidentiality has been broken.

## Integrity

**Integrity** means ensuring that information is accurate, complete, and has not been altered in an unauthorized way.

The goal is to prevent tampering, corruption, or unauthorized modification. Users and systems must be able to trust that data has not been changed maliciously or accidentally.

Common controls that support integrity include:

- Hashing and digital signatures
- Version control and audit logs
- Input validation
- Checksums and file integrity monitoring

**Example:** A student submits an exam through an online portal. If an attacker changes their grade after submission, integrity has been violated—even if the student can still log in and view the result.

## Availability

**Availability** means ensuring that systems, applications, and data are accessible to authorized users when they are needed.

The goal is to prevent downtime, disruption, or denial of service. Security is not only about blocking attackers; it is also about keeping services running reliably.

Common controls that support availability include:

- Backups and disaster recovery plans
- Redundancy and load balancing
- DDoS mitigation
- Patch management and monitoring

**Example:** An online banking site goes offline during a distributed denial-of-service (DDoS) attack. Customers cannot access their accounts. Even if no data was stolen, availability has failed.

## How the Three Principles Work Together

The CIA Triad is most useful when all three principles are considered together. Improving one area can sometimes affect another:

| Scenario | Principle affected |
|----------|-------------------|
| Encrypting a database | Improves **confidentiality**, but may add processing overhead that slightly affects **availability** |
| Strict access controls | Protect **confidentiality** and **integrity**, but overly restrictive rules can reduce **availability** for legitimate users |
| Frequent backups | Support **availability** and can help restore **integrity** after an incident |

Security decisions often involve balancing these trade-offs based on what matters most for a given system or organization.

## Why the CIA Triad Matters

The CIA Triad provides a simple framework for:

- Designing secure systems
- Evaluating risks and threats
- Choosing appropriate security controls
- Communicating security goals to non-technical stakeholders

When analyzing an attack or planning defenses, asking *"Which part of the CIA Triad is at risk?"* helps focus the response. A ransomware incident may threaten **availability** and **integrity**. A data breach primarily threatens **confidentiality**. A defaced website may affect **integrity** and **availability**.

## Beyond the Triad

The CIA Triad is a starting point, not the full picture of modern security. Other concepts—such as **authentication**, **non-repudiation**, **privacy**, and **accountability**—are also important. Still, nearly every security control maps back to confidentiality, integrity, or availability in some way.

Understanding the CIA Triad is one of the first steps toward thinking systematically about information security.
