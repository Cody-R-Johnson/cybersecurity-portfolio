# ICMP Flood Denial-of-Service (DoS) Incident Analysis  
## NIST Cybersecurity Framework (CSF) Application

---

## Project Overview

This case study documents the analysis of an ICMP flood denial-of-service (DoS) attack that disrupted a multimedia company's internal network operations for approximately two hours.  

The incident was analyzed using the National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF) to ensure a structured, comprehensive evaluation across the five core functions: Identify, Protect, Detect, Respond, and Recover.

This report demonstrates applied incident analysis, network security evaluation, and structured response planning aligned with industry frameworks.

---

## Incident Summary

The organization experienced an ICMP flood DoS attack caused by excessive inbound ICMP packets entering the network through a misconfigured perimeter firewall.  

The firewall lacked rate-limiting and filtering controls, allowing the malicious traffic to overwhelm internal network resources.

Impact:
- Internal network services became unavailable
- Core business operations were disrupted
- Non-critical services were temporarily shut down to reduce strain
- Full restoration required approximately two hours

Once identified, the security team blocked malicious traffic, restored critical services, and implemented mitigation improvements.

---

# NIST CSF Analysis

---

## 1. Identify

### Assets Affected
- Internal network infrastructure
- Core internal services dependent on network availability
- Perimeter firewall configuration

### Root Cause
- Misconfigured firewall
- Lack of ICMP filtering and rate-limiting
- No real-time monitoring alerts
- Insufficient layered perimeter defenses

### Risk Exposure Identified
- Availability risk due to poor network hardening
- Monitoring gaps
- Lack of proactive traffic anomaly detection

This phase revealed configuration management weaknesses and insufficient perimeter control validation.

---

## 2. Protect

To reduce future risk, the organization will:

- Standardize firewall configuration baselines
- Implement ICMP rate-limiting rules
- Restrict unnecessary inbound ICMP traffic
- Document and periodically review firewall rules
- Introduce network segmentation to reduce blast radius
- Conduct periodic security audits and penetration testing
- Provide ongoing firewall management training to IT staff

These measures strengthen preventive controls and reduce exposure to availability attacks.

---

## 3. Detect

Detection improvements include:

- Deploying a network-based IDS/IPS at the perimeter
- Centralizing firewall and network logs into a SIEM platform
- Establishing defined traffic baselines
- Creating alert thresholds for abnormal ICMP patterns
- Implementing continuous monitoring procedures

These steps significantly reduce detection time and increase visibility into suspicious activity.

---

## 4. Respond

Future incident response improvements include:

- Formal incident declaration criteria
- SOC-led coordination procedures
- Stakeholder notification protocols
- Isolation of affected network segments
- Rapid firewall rule adjustments
- Log preservation for forensic analysis
- Post-incident root cause analysis review

The organization will also document response workflows to improve repeatability and reduce response time.

---

## 5. Recover

Following containment:

- Critical services were restored
- Firewall configurations were standardized
- Secure baseline configurations were documented
- Stakeholders were notified of system stability

To improve resilience:

- Firewall configurations will be version-controlled and backed up
- Business continuity plans will be updated
- Redundancy options (backup ISP / DDoS mitigation services) will be evaluated
- Recovery procedures will be formally documented

---

## Risk Classification

| Category | Impact Level |
|----------|--------------|
| Availability | High |
| Integrity | Low |
| Confidentiality | Low |
| Operational Disruption | High |
| Regulatory Exposure | Low |

This incident primarily affected availability rather than data compromise.

---

## Security Principles Demonstrated

- Defense in depth
- Perimeter hardening
- Continuous monitoring
- Structured incident response
- Configuration management
- Availability risk mitigation

---

## Skills Demonstrated

- Incident analysis using NIST CSF
- Network attack classification (ICMP flood / DoS)
- Root cause identification
- Firewall misconfiguration analysis
- Detection strategy development
- Incident response planning
- Recovery planning
- Structured security documentation

---

## Key Takeaways

This incident demonstrates how a single firewall misconfiguration can create significant availability risks.  

Layered defenses, proactive monitoring, and structured incident handling are critical to reducing business disruption.

Applying the NIST CSF provided a systematic way to analyze the event beyond immediate containment and helped translate a reactive response into long-term strategic improvements.

---

## Portfolio Note

This project reflects practical incident analysis aligned with the NIST Cybersecurity Framework and demonstrates SOC-relevant skills in network security, detection strategy, and structured incident response planning.
