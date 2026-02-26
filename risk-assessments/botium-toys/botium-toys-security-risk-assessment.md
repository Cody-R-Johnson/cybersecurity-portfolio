# Botium Toys – Security Risk Assessment & Compliance Evaluation

## Project Overview

This project documents a structured security audit and risk assessment conducted for a fictional retail organization, Botium Toys. The objective was to evaluate the organization's security posture, identify control gaps, assess regulatory compliance exposure, and prioritize remediation efforts.

The assessment covered technical controls, administrative policies, physical security, and regulatory compliance alignment (PCI DSS, GDPR, SOC considerations).

---

## Scope of Assessment

The audit evaluated the organization's entire security program, including:

- On-premises infrastructure
- Employee endpoint devices (desktops, laptops, smartphones)
- Internal network
- Ecommerce and inventory systems
- Data storage and retention practices
- Legacy systems
- Physical storefront and warehouse
- Compliance controls and governance processes

The assessment focused on identifying missing controls, weak implementations, and areas of high regulatory risk exposure.

---

## Business Risk Summary

**Overall Risk Score: 8/10 (High)**

The organization demonstrates significant control gaps in core security domains including encryption, access control, disaster recovery, and data protection compliance.

Primary risk drivers include:
- No encryption for cardholder data
- No disaster recovery or backup strategy
- No least privilege implementation
- Broad internal access to PII/SPII
- Weak password enforcement
- No intrusion detection system (IDS)

These deficiencies create exposure to financial loss, regulatory penalties, and reputational damage.

---

## Key Control Findings

### 1. Access Control & Least Privilege (High Risk)

- All employees have access to internally stored data.
- Cardholder data and customer PII are broadly accessible.
- Separation of duties is not implemented.
- No role-based access restrictions.

**Impact:** Increased risk of insider threat, fraud, and regulatory non-compliance.

---

### 2. Encryption & Data Protection (High Risk)

- Credit card data is not encrypted at rest.
- Credit card data is not encrypted in transit.
- Sensitive data confidentiality controls are insufficient.

**Impact:** Direct violation risk of PCI DSS requirements and potential GDPR exposure.

---

### 3. Disaster Recovery & Backups (High Risk)

- No disaster recovery plan exists.
- No formal data backup strategy.
- No documented business continuity process.

**Impact:** Extended operational downtime and potential permanent data loss.

---

### 4. Password & Authentication Controls (Medium Risk)

- Password policy exists but lacks modern complexity standards.
- No centralized password management system.
- Password enforcement is inconsistent.

**Impact:** Increased likelihood of credential compromise.

---

### 5. Intrusion Detection & Monitoring (Medium Risk)

- Firewall implemented and operational.
- Antivirus deployed and monitored.
- No Intrusion Detection System (IDS) implemented.
- Legacy systems monitored informally without structured schedule.

**Impact:** Reduced visibility into malicious activity and delayed incident detection.

---

### 6. Physical Security (Low Risk)

- Locks installed at storefront and warehouse.
- CCTV operational and maintained.
- Fire detection and prevention systems functional.

**Impact:** Physical security controls are sufficient relative to other risk areas.

---

## Regulatory Compliance Exposure

### PCI DSS

High-risk gaps identified:

- Unauthorized access to cardholder data
- No encryption for payment data
- Weak access controls
- Inadequate password enforcement

**Compliance Status:** Not compliant

---

### GDPR

- 72-hour breach notification plan documented.
- Privacy policies documented and enforced.
- No formal data classification program.
- Broad access and lack of encryption weaken confidentiality.

**Compliance Risk:** High

---

### SOC Considerations

- User access policies exist but need strengthening.
- Integrity controls implemented.
- Data availability maintained.
- Confidentiality controls insufficient.

---

## Risk Prioritization

### High Priority Remediation

1. Implement encryption for payment data (at rest and in transit)
2. Enforce least privilege and role-based access control (RBAC)
3. Establish disaster recovery plan
4. Implement automated data backup strategy
5. Restrict cardholder data access

### Medium Priority Remediation

1. Deploy intrusion detection system (IDS)
2. Strengthen password policy and enforcement
3. Implement centralized password management
4. Formalize legacy system monitoring schedule
5. Establish asset inventory and classification program

### Low Priority

Physical security controls require minimal adjustment.

---

## Recommended Security Roadmap

### Phase 1 – Immediate Risk Reduction
- Deploy encryption mechanisms
- Restrict sensitive data access
- Create backup architecture
- Implement RBAC

### Phase 2 – Monitoring & Detection
- Deploy IDS
- Formalize monitoring processes
- Standardize patch and legacy system management

### Phase 3 – Governance & Compliance Alignment
- Implement asset classification
- Formalize compliance mapping to PCI DSS & GDPR
- Conduct regular security audits

---

## Skills Demonstrated

- Security risk assessment
- Control gap analysis
- Regulatory mapping (PCI DSS, GDPR, SOC)
- Risk scoring and prioritization
- Policy evaluation
- Incident impact analysis
- Security documentation
- Business continuity planning concepts

---

## Key Takeaways

This assessment highlights how missing foundational controls (encryption, access control, backups) significantly increase regulatory and operational risk.

Security posture maturity requires:
- Asset visibility
- Enforced least privilege
- Encryption standards
- Monitoring visibility
- Documented recovery processes

Without these, organizations face elevated financial, legal, and reputational exposure.

---

## Portfolio Note

This project reflects applied cybersecurity analysis aligned with NIST CSF principles and compliance frameworks. The documentation demonstrates structured thinking, risk evaluation methodology, and remediation prioritization appropriate for entry-level SOC and security analyst roles.
