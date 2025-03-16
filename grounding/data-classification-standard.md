# Data Classification Framework for GDPR Compliance

## Data Classification Categories

| Classification Level | Description | Examples | Risk Level |
|---------------------|-------------|----------|------------|
| **Public Data** | Information that can be freely disclosed to the public without any adverse impact | Marketing materials, public financial reports, job postings, information on public websites | Low |
| **Internal Data** | Non-sensitive information intended for use within the organization | Internal memos, project plans without PII, training materials, organizational charts | Medium-Low |
| **Confidential Data** | Business-sensitive information that could cause damage if disclosed | Business strategies, intellectual property, financial forecasts, vendor contracts | Medium-High |
| **Restricted Data** | Highly sensitive information including personal data subject to GDPR | Personal identifiable information (PII), financial account details, health records | High |
| **Restricted Data - Pseudonymized** | Personal data that has been processed so that it can no longer be attributed to a specific data subject without additional information | User IDs, IP addresses, device identifiers, encrypted identifiers, hashed email addresses, cookie IDs that can be linked to a natural person via lookup tables | High |
| **Restricted Data - Directly Identifiable** | Personal data that can directly identify a natural person without needing additional information | Names, email addresses, physical addresses, phone numbers, social security numbers, passport numbers, driver's license numbers, biometric identifiers | Very High |
| **Special Category Data** | Special categories of personal data as defined by GDPR Article 9 | Racial/ethnic origin, political opinions, religious beliefs, genetic data, biometric data, health data, sexual orientation | Very High |

## Data Handling Requirements by Classification

### Data Retention Standards

| Classification Level | Retention Period | Justification Requirement | Review Cycle | Deletion Process |
|---------------------|------------------|---------------------------|--------------|-----------------|
| **Public Data** | As needed for business purposes | Minimal | Annual | Standard deletion |
| **Internal Data** | Up to 5 years or as needed | Business purpose documentation | Annual | Standard deletion with verification |
| **Confidential Data** | Up to 3 years after last use | Documented business necessity | Bi-annual | Secure deletion with certificate |
| **Restricted Data** | Minimum necessary period, typically 1-2 years | Documented legal basis required | Quarterly | Secure deletion with audit trail |
| **Restricted Data - Pseudonymized** | Can be retained longer than directly identifiable data, typically 1-3 years | Documented legal basis required | Quarterly | Secure deletion with audit trail, including lookup tables |
| **Restricted Data - Directly Identifiable** | Strict minimum necessary period, typically 6-18 months | Strong documented legal basis required | Monthly | Secure deletion with detailed audit trail |
| **Special Category Data** | Minimum necessary period, typically 6-12 months | Explicit legal basis and necessity documentation | Quarterly | Secure deletion with verification and audit trail |

### Data Transmission Standards

| Classification Level | Encryption | Authentication | Transport Protocol | Additional Controls |
|---------------------|------------|----------------|-------------------|---------------------|
| **Public Data** | Optional | Not required | Standard (HTTP/HTTPS) | No additional controls required |
| **Internal Data** | TLS 1.2+ | Basic authentication | HTTPS | Access logging |
| **Confidential Data** | TLS 1.3 | Multi-factor authentication | HTTPS/SFTP | Access logging, transmission logging |
| **Restricted Data** | TLS 1.3 with strong ciphers | Multi-factor authentication | HTTPS/SFTP/VPN | Access logging, transmission logging, data loss prevention |
| **Restricted Data - Pseudonymized** | TLS 1.3 with strong ciphers | Multi-factor authentication | HTTPS/SFTP/VPN | Access logging, transmission logging, data loss prevention, separate transmission of lookup tables |
| **Restricted Data - Directly Identifiable** | TLS 1.3 with strong ciphers plus additional encryption layer | Strong multi-factor authentication | HTTPS/SFTP/VPN with restricted endpoints | Access logging, transmission logging, enhanced DLP controls, approval required |
| **Special Category Data** | End-to-end encryption | Strong multi-factor authentication | VPN/Secure protocols only | Access logging, transmission logging, DLP, additional approval required |

### Data Storage Standards

| Classification Level | Encryption | Storage Location | Access Controls | Backup Requirements |
|---------------------|------------|------------------|----------------|---------------------|
| **Public Data** | Not required | Any approved storage | No restrictions | Standard backup |
| **Internal Data** | At rest encryption | Approved corporate storage | Role-based access | Regular backup with 30-day retention |
| **Confidential Data** | Strong encryption at rest | Secured corporate storage | Role-based access with justification | Regular backup with encryption and 90-day retention |
| **Restricted Data** | Strong encryption with key management | Secured storage in GDPR-compliant locations | Role-based access with approval and logging | Encrypted backup with 1-year retention and access controls |
| **Restricted Data - Pseudonymized** | Strong encryption with key management | Secured storage in GDPR-compliant locations | Role-based access with approval and logging | Encrypted backup with 1-year retention and access controls, separate storage of lookup tables with additional controls |
| **Restricted Data - Directly Identifiable** | Strong encryption with separated key management | Secured storage in GDPR-compliant locations with additional security measures | Strict role-based access with time-limited approval and detailed logging | Encrypted backup with 1-year retention and enhanced access controls |
| **Special Category Data** | Strong encryption with separate key management | Secured storage in EU only (unless adequate safeguards) | Strict need-to-know access with time-limited authorization | Encrypted backup with 1-year retention and strict access controls |

### Data Processing and Derived Use

| Classification Level | Purpose Limitation | Legal Basis Required | Data Minimization | Impact Assessment |
|---------------------|---------------------|----------------------|-------------------|-------------------|
| **Public Data** | Broad use permitted | Not required | Basic | Not required |
| **Internal Data** | Limited to business purposes | Legitimate interest | Moderate | Not required |
| **Confidential Data** | Limited to specified purposes | Legitimate interest/contractual | Strong | Recommended |
| **Restricted Data** | Strictly limited to specified purposes | Consent/contract/legal obligation | Very strong | Required |
| **Restricted Data - Pseudonymized** | Limited to specified purposes, with broader analytical use possible | Consent/contract/legal obligation | Strong with pseudonymization procedures | Required with focus on pseudonymization controls |
| **Restricted Data - Directly Identifiable** | Strictly limited to essential specified purposes | Explicit consent/clear contract/specific legal obligation | Extremely strict with data minimization | Required with detailed risk mitigation |
| **Special Category Data** | Strictly limited to specific legal basis | Explicit consent/legal exceptions only | Extremely strict | Required with additional safeguards |

## GDPR Specific Requirements

### Data Subject Rights Management

| Classification Level | Right to Access | Right to Rectification | Right to Erasure | Right to Portability |
|---------------------|-----------------|------------------------|------------------|----------------------|
| **Public Data** | Not applicable | Not applicable | Not applicable | Not applicable |
| **Internal Data** | Applicable if personal data | Applicable if personal data | Applicable if personal data | Limited applicability |
| **Confidential Data** | Applicable for personal elements | Applicable for personal elements | Applicable for personal elements | Applicable for personal elements |
| **Restricted Data** | Full compliance required | Full compliance required | Full compliance required | Full compliance required |
| **Restricted Data - Pseudonymized** | Full compliance required with lookup process | Full compliance required with lookup process | Full compliance required with lookup process | Full compliance required with lookup process |
| **Restricted Data - Directly Identifiable** | Priority compliance required | Priority compliance required | Priority compliance required | Priority compliance required |
| **Special Category Data** | Priority compliance required | Priority compliance required | Priority compliance required | Priority compliance required |

### Data Transfer Controls

| Classification Level | EU Transfer | Adequate Countries | Non-Adequate Countries | Transfer Documentation |
|---------------------|-------------|---------------------|------------------------|------------------------|
| **Public Data** | Permitted | Permitted | Permitted | Not required |
| **Internal Data** | Permitted | Permitted | Permitted with basic controls | Basic documentation |
| **Confidential Data** | Permitted | Permitted | SCCs or other safeguards required | Documented safeguards |
| **Restricted Data** | Permitted | Adequate safeguards required | Strong safeguards required (SCCs with supplementary measures) | Comprehensive documentation required |
| **Restricted Data - Pseudonymized** | Permitted | Adequate safeguards required | Strong safeguards required (SCCs with supplementary measures) | Comprehensive documentation required with risk assessment for pseudonymization strength |
| **Restricted Data - Directly Identifiable** | Permitted with enhanced controls | Strong safeguards required | Very strong safeguards required (SCCs with robust supplementary measures) | Detailed risk assessment and comprehensive documentation with DPO approval |
| **Special Category Data** | Permitted | Strong safeguards required | Restricted; requires robust safeguards and DPO approval | Detailed risk assessment and documentation required |

### Breach Notification Requirements

| Classification Level | Notification Timeline | Notification Recipient | Documentation Required | Remediation Priority |
|---------------------|------------------------|------------------------|------------------------|---------------------|
| **Public Data** | Not required | Not required | Minimal | Low |
| **Internal Data** | As per internal policy | Internal teams | Basic incident report | Medium-Low |
| **Confidential Data** | As per internal policy | Internal teams and affected parties | Detailed incident report | Medium-High |
| **Restricted Data** | 72 hours to DPA | DPA, affected individuals, internal teams | Comprehensive breach documentation | High |
| **Restricted Data - Pseudonymized** | 72 hours to DPA | DPA, affected individuals (if lookup tables also compromised), internal teams | Comprehensive breach documentation with pseudonymization assessment | High |
| **Restricted Data - Directly Identifiable** | 72 hours to DPA (priority notification) | DPA (immediate), affected individuals (without undue delay), internal teams | Comprehensive breach documentation with detailed impact analysis | Very High |
| **Special Category Data** | 72 hours to DPA | DPA (priority), affected individuals, internal teams | Comprehensive breach documentation with impact analysis | Very High |

## Implementation Guidelines

### Data Discovery and Classification Process

1. **Data Inventory**: Conduct regular data mapping to identify all data assets
2. **Classification Assessment**: Apply the classification framework to each data asset
3. **Labeling**: Implement appropriate data labeling mechanisms
4. **Documentation**: Maintain a data register with classifications
5. **Review Cycle**: Establish regular review cycles based on data sensitivity

### Technical Controls by Classification

| Classification Level | Access Monitoring | Data Loss Prevention | Activity Logging | Anonymization/Pseudonymization |
|---------------------|------------------|---------------------|----------------|--------------------------------|
| **Public Data** | Not required | Not required | Basic | Not required |
| **Internal Data** | Basic monitoring | Not required | Standard logging | Optional |
| **Confidential Data** | Regular monitoring | Basic DLP controls | Enhanced logging | Recommended where applicable |
| **Restricted Data** | Continuous monitoring | Advanced DLP controls | Comprehensive logging | Required where possible |
| **Restricted Data - Pseudonymized** | Continuous monitoring | Advanced DLP controls with pseudonymization verification | Comprehensive logging with lookup table access tracking | Required with pseudonymization strength validation |
| **Restricted Data - Directly Identifiable** | Real-time monitoring with alerts | Strict DLP controls with blocking capabilities | Detailed audit logging with alerting | Required with additional technical safeguards |
| **Special Category Data** | Real-time monitoring | Strict DLP controls | Detailed audit logging | Required with technical safeguards |

### Compliance Documentation Requirements

| Classification Level | Processing Records | DPIA Required | Lawful Basis Documentation | Consent Management |
|---------------------|---------------------|--------------|---------------------------|-------------------|
| **Public Data** | Minimal | No | Minimal | Not required |
| **Internal Data** | Basic | No | Basic documentation | If applicable |
| **Confidential Data** | Standard | If high risk | Clear documentation | If used as basis |
| **Restricted Data** | Detailed | Yes | Comprehensive documentation | Robust consent management |
| **Restricted Data - Pseudonymized** | Detailed with pseudonymization methods | Yes, with focus on pseudonymization techniques | Comprehensive documentation with pseudonymization procedures | Robust consent management with pseudonymization notice |
| **Restricted Data - Directly Identifiable** | Highly detailed | Mandatory with senior approval | Comprehensive documentation with necessity justification | Strict consent management with verification and regular renewal |
| **Special Category Data** | Comprehensive | Mandatory | Explicit documentation | Strict consent management with verification |
