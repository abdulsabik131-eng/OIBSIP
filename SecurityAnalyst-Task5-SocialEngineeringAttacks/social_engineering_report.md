# Social Engineering Attacks: Research Report

## Introduction

Social engineering is the use of deception, manipulation, impersonation, or psychological pressure to make people reveal information or perform unsafe actions. It is effective because it targets trust, urgency, fear, authority, curiosity, and helpfulness instead of relying only on technical vulnerabilities.

The SANS 2025 Security Awareness Report states that 80% of surveyed organizations identified social engineering as their top human-related security risk.

## 1. Phishing

Phishing is a fraudulent attempt to steal information or cause an unsafe action by pretending to be a trusted person or service.

### Types

- **Spear phishing:** Targeted phishing against a specific person or department.
- **Whaling:** Phishing aimed at executives or high-value individuals.
- **Vishing:** Voice or telephone phishing.
- **Smishing:** SMS or text-message phishing.

### How it works

1. Research the target.
2. Prepare a convincing email, call, message, link, or attachment.
3. Create urgency or fear.
4. Trick the victim into clicking, opening, replying, approving MFA, or transferring money.
5. Use the result for credential theft, malware delivery, fraud, or further attacks.

### Case study: 2020 Twitter attack

Attackers called Twitter employees while pretending to be internal IT support. They used a fake VPN-support story and directed employees to a fraudulent login page. Twitter reported that 130 accounts were targeted and 45 were compromised. The attackers then accessed internal support tools and took over high-profile accounts to publish Bitcoin scam messages.

### Prevention

1. Conduct regular phishing-awareness training.
2. Use phishing-resistant MFA such as passkeys or security keys.
3. Deploy email filtering, URL scanning, and attachment sandboxing.
4. Verify sensitive requests through a separate trusted channel.

## 2. Pretexting

Pretexting is an attack in which an attacker creates a false story or identity to make a request appear legitimate.

### Common method

The attacker researches the target, impersonates IT support, a manager, a bank employee, or another trusted person, then uses realistic details and urgency to request credentials, MFA approval, documents, or money.

### Case study

The 2020 Twitter attack also involved pretexting. Attackers claimed to be help-desk staff responding to VPN problems. This false scenario made the request appear legitimate and encouraged employees to provide information and authenticate to attacker-controlled pages.

### Prevention

1. Verify identities using independently known contact details.
2. Apply least privilege to administrative tools.
3. Enforce a policy that staff must never share passwords, MFA codes, or recovery codes.

## 3. Baiting

Baiting uses an attractive object, file, download, or offer to tempt a victim into an unsafe action.

### Physical baiting

Examples include infected USB drives labeled as salary data, exam results, or confidential documents.

### Digital baiting

Examples include fake software updates, cracked applications, free downloads, fake browser extensions, and attractive malicious files.

### Case study: Stuxnet

Stuxnet used infected USB devices as one propagation method. This was useful in environments with limited or isolated network connectivity. The case demonstrates how removable media can become a bridge into sensitive systems.

### Prevention

1. Restrict and scan removable media.
2. Download software only from trusted official sources.
3. Never plug in unknown USB devices or open unexpected files.

## 4. Quid Pro Quo

Quid pro quo means “something for something.” The attacker offers help, a reward, a refund, or another benefit in exchange for information or access.

### Prevention

- Use official support channels.
- Never share passwords or MFA codes for technical help.
- Verify the identity of anyone offering a service or benefit.

## 5. Comparison Table

| Attack type | Primary target | Psychological lever | Best countermeasure |
|---|---|---|---|
| Phishing | Email and messaging users | Urgency and trust | Filtering, awareness, MFA |
| Spear phishing | Specific employees | Personalization and authority | Verification and targeted training |
| Whaling | Executives and finance teams | Authority and financial pressure | Dual approval and out-of-band verification |
| Vishing | Phone users and help desks | Trust and urgency | Call-back verification |
| Smishing | Mobile users | Curiosity and urgency | Mobile filtering and link verification |
| Pretexting | Employees with access | Authority and familiarity | Identity verification and least privilege |
| Baiting | Curious users and isolated systems | Curiosity and reward | USB restrictions and trusted downloads |
| Quid pro quo | Users seeking help or benefits | Reciprocity and reward | Approved support channels |

## 6. Organisational Recommendations

1. Conduct regular phishing, vishing, and smishing awareness training.
2. Teach employees to verify unusual requests independently.
3. Prohibit sharing passwords, MFA codes, recovery codes, and private keys.
4. Establish a simple process for reporting suspicious activity.
5. Measure reporting rates and provide follow-up coaching after simulations.

## 7. Incident Response

When a social engineering attempt is reported:

1. Preserve emails, messages, URLs, attachments, phone numbers, and timestamps.
2. Determine whether the user clicked, replied, opened, shared information, or approved MFA.
3. Reset exposed credentials and revoke sessions when necessary.
4. Block malicious indicators after validation.
5. Review email, authentication, endpoint, and proxy logs.
6. Escalate confirmed compromise immediately.
7. Document lessons learned and update controls.

## Conclusion

Social engineering attacks succeed because people are often the easiest path around technical defenses. Strong protection requires awareness training, identity verification, least privilege, phishing-resistant MFA, filtering, removable-media controls, and a clear reporting process.

## References

1. [CISA Phishing Infographic](https://www.cisa.gov/sites/default/files/2023-02/phishing-infographic-508c_0.pdf)
2. [SANS 2025 Security Awareness Report](https://www.sans.org/press/announcements/security-awareness-report-2025)
3. [SANS 2023 Attack and Threat Report](https://www.sans.org/white-papers/sans-2023-attack-threat-report)
4. [Twitter: An Update on Our Security Incident](https://blog.x.com/en_us/topics/company/2020/an-update-on-our-security-incident)
5. [New York DFS Twitter Investigation Report](https://www.dfs.ny.gov/reports-and-publications/other-reports/Twitter_Report)
6. [SANS Security Awareness and Culture Report 2026](https://www.sans.org/press/announcements/ai-second-biggest-human-risk-workplace-sans-institutes-2026-security-awareness-culture-report-finds)
