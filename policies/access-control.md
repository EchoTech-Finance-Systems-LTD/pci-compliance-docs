# Access Control Policy

**Document ID:** POL-AC-001  
**Version:** 3.0  
**Effective Date:** August 14, 2025  
**Next Review Date:** February 14, 2026  
**Owner:** Chief Security Officer  
**Approved By:** [Digital Signature/Date]  

**PCI DSS Requirements:** 7.1, 7.2, 7.3, 8.1, 8.2, 8.3, 8.4, 8.5, 8.6  

---

## 1. Purpose and Scope

This policy establishes access control requirements for all systems, applications, and data within the cardholder data environment (CDE) to ensure compliance with PCI DSS requirements and protect cardholder data from unauthorized access.

### Scope
- All personnel with access to CDE systems
- All systems storing, processing, or transmitting CHD
- All network components connecting to the CDE
- Service providers and vendors with CDE access
- Remote access connections to the CDE

---

## 2. Access Control Principles

### 2.1 Least Privilege
- Users granted minimum access necessary for job function
- Access rights regularly reviewed and adjusted
- Privilege escalation requires additional authorization
- Administrative access limited to designated personnel

### 2.2 Need-to-Know Basis  
- Access granted only to specific data/systems required
- Business justification required for all access requests
- Regular validation of access necessity
- Automatic removal when business need ends

### 2.3 Separation of Duties
- Critical functions require multiple person authorization
- Development, testing, and production access segregated
- Administrative functions separated from operational tasks
- Financial/audit functions independent from IT operations

---

## 3. User Access Management

### 3.1 Account Provisioning
1. **Access Request Process:**
   - Formal request via ServiceNow with manager approval
   - HR verification of employment status
   - Security team review and authorization
   - Automated provisioning where possible

2. **Required Documentation:**
   - Business justification for access
   - Specific systems/data required
   - Access level and duration
   - Manager approval and date

### 3.2 Account Types

#### Standard User Accounts
- **Purpose:** Day-to-day business operations
- **Permissions:** Read/write to assigned systems only
- **Authentication:** Multi-factor authentication required
- **Review Frequency:** Quarterly

#### Administrative Accounts  
- **Purpose:** System administration and maintenance
- **Permissions:** Elevated privileges for specific systems
- **Authentication:** Strong MFA + privileged access management
- **Review Frequency:** Monthly
- **Additional Controls:** Session recording, approval workflows

#### Service Accounts
- **Purpose:** Application and system integrations
- **Permissions:** Minimum required for service function
- **Authentication:** Certificate-based or API keys
- **Review Frequency:** Quarterly
- **Management:** Centralized credential management system

### 3.3 Account Lifecycle Management

#### New User Onboarding
- [ ] HR notification of new hire
- [ ] Manager submits access request
- [ ] Security background check verification
- [ ] Account creation with temporary credentials
- [ ] Security awareness training completion
- [ ] Manager confirmation of appropriate access

#### Access Modifications
- [ ] Change request with business justification
- [ ] Manager approval for access changes
- [ ] Security team review and implementation
- [ ] User notification and training if needed
- [ ] Documentation update in access registry

#### User Termination/Transfer
- [ ] HR notification triggers immediate access review
- [ ] Account disabling within 4 hours of notification
- [ ] Retrieval of company devices and credentials
- [ ] Transfer of data ownership if applicable
- [ ] Account deletion after retention period
- [ ] Exit interview security component

---

## 4. Authentication Requirements

### 4.1 Password Policy
- **Minimum Length:** 12 characters
- **Complexity:** Upper/lower case, numbers, special characters
- **History:** Cannot reuse last 12 passwords
- **Expiration:** 90 days maximum (longer if MFA enabled)
- **Account Lockout:** 6 failed attempts, 30-minute lockout
- **Default Passwords:** Must be changed before first use

### 4.2 Multi-Factor Authentication (MFA)
**Required For:**
- All administrative access
- Remote access to CDE
- Access to cardholder data
- Privileged user accounts
- VPN connections

**Approved MFA Methods:**
- Hardware security keys (preferred)
- Mobile authenticator apps
- SMS (only where other methods unavailable)
- Biometric authentication (supplementary)

### 4.3 Single Sign-On (SSO)
- Centralized authentication through approved SSO provider
- SAML 2.0 or modern OAuth 2.0/OpenID Connect
- Session timeout controls implemented
- Strong authentication at SSO level propagates to all systems

---

## 5. Access Review and Certification

### 5.1 Regular Access Reviews

#### Quarterly Reviews
- **Scope:** All user access to CDE systems
- **Process:** Manager certification of subordinate access
- **Timeline:** Completed within 30 days of quarter end
- **Documentation:** Results retained for 12 months

#### Monthly Administrative Reviews
- **Scope:** All administrative and privileged accounts
- **Process:** Security team verification of access necessity
- **Timeline:** Completed by 15th of following month
- **Documentation:** Exceptions documented and remediated

#### Annual Comprehensive Review  
- **Scope:** All access rights across entire organization
- **Process:** Cross-functional team review with attestation
- **Timeline:** Completed within 60 days of fiscal year end
- **Documentation:** Formal report to senior management

### 5.2 Automated Access Monitoring
- **Daily:** Automated reports of new/modified accounts
- **Weekly:** Privileged access usage reports
- **Monthly:** Dormant account identification
- **Quarterly:** Access pattern analysis for anomalies

---

## 6. Privileged Access Management

### 6.1 Privileged Account Controls
- **Just-in-Time Access:** Temporary elevation for specific tasks
- **Session Recording:** All privileged sessions logged and recorded
- **Approval Workflows:** Manager approval for privileged access requests
- **Secure Credential Storage:** Passwords managed in PAM solution
- **Regular Rotation:** Automated credential rotation every 30 days

### 6.2 Administrative Access Restrictions
- **Dual Control:** Two-person authorization for critical changes
- **Time Restrictions:** Administrative access limited to business hours
- **Location Restrictions:** Administrative access from approved locations only
- **Activity Monitoring:** Real-time monitoring of administrative activities
- **Break-Glass Procedures:** Emergency access with enhanced logging

---

## 7. Remote Access Security

### 7.1 VPN Requirements
- **Strong Authentication:** Multi-factor authentication required
- **Endpoint Security:** Device compliance verification
- **Encryption:** Minimum AES-256 encryption
- **Session Monitoring:** All VPN sessions logged and monitored
- **Automatic Disconnect:** Idle session timeout after 30 minutes

### 7.2 Remote Desktop Access
- **Centralized Gateway:** All RDP traffic through secure gateway
- **Network Segmentation:** RDP access limited to specific network segments  
- **Session Recording:** All remote desktop sessions recorded
- **File Transfer Controls:** Restricted file transfer capabilities
- **Print/Clipboard Controls:** Limited local resource access

---

## 8. System Access Controls

### 8.1 Server Access
- **Local Accounts:** Disabled except for emergency break-glass
- **Domain Authentication:** All servers joined to managed domain
- **Administrative Groups:** Membership regularly reviewed and documented
- **Service Accounts:** Centrally managed with regular password rotation
- **Audit Logging:** All logon/logoff events logged and monitored

### 8.2 Database Access
- **Named Accounts:** No shared database accounts
- **Role-Based Access:** Database roles mapped to business functions
- **Query Monitoring:** Sensitive data access logged and monitored
- **Data Masking:** Production data masked in non-production environments
- **Connection Encryption:** All database connections encrypted

### 8.3 Application Access
- **Role-Based Access Control:** Application permissions based on business roles
- **Data Classification:** Access controls based on data sensitivity
- **API Security:** API access authenticated and authorized
- **Session Management:** Secure session handling with appropriate timeouts
- **Input Validation:** Protection against injection attacks

---

## 9. Network Access Controls

### 9.1 Network Segmentation
- **CDE Isolation:** Cardholder data environment properly segmented
- **Firewall Rules:** Least privilege network access controls
- **VLAN Segmentation:** Logical separation of network segments
- **DMZ Implementation:** Public-facing systems in demilitarized zone
- **Internal Network Controls:** Micro-segmentation where feasible

### 9.2 Wireless Network Security
- **Enterprise WPA3:** Strong wireless encryption protocols
- **Network Isolation:** Guest networks separated from corporate
- **Device Authentication:** 802.1X authentication for corporate devices
- **Monitoring:** Wireless intrusion detection and prevention
- **Access Point Management:** Centralized wireless infrastructure management

---

## 10. Physical Access Controls

### 10.1 Facility Access
- **Badge-Controlled Entry:** Electronic access control systems
- **Visitor Management:** Escort requirements for non-employees
- **Access Logging:** All facility access logged and retained
- **Security Cameras:** Video surveillance with retention requirements
- **After-Hours Access:** Enhanced security for off-hours facility access

### 10.2 Server Room/Data Center Access
- **Dual Authentication:** Badge plus biometric verification
- **Mantrap Entry:** Physical access control vestibules
- **Continuous Monitoring:** 24/7 video surveillance and motion detection
- **Environmental Controls:** Temperature, humidity, and power monitoring
- **Visitor Logs:** All data center access logged with business justification

---

## 11. Vendor and Third-Party Access

### 11.1 Service Provider Access
- **Contractual Requirements:** Security requirements in all contracts
- **Limited Access:** Vendor access restricted to necessary systems only
- **Monitoring:** All vendor access logged and monitored
- **Time-Limited Access:** Vendor accounts disabled when not actively needed
- **Regular Reviews:** Quarterly review of all vendor access

### 11.2 Vendor Access Management
- **Approval Process:** Business owner approval for vendor access requests
- **Security Assessment:** Vendor security posture review before access
- **Access Restrictions:** Vendor access limited to specific IP ranges/times
- **Activity Monitoring:** Enhanced monitoring of vendor activities
- **Termination Process:** Formal process for ending vendor relationships

---

## 12. Monitoring and Compliance

### 12.1 Access Monitoring
- **Real-Time Alerts:** Immediate notification of suspicious access patterns
- **Log Aggregation:** Centralized logging of all access events
- **Behavioral Analytics:** Machine learning-based anomaly detection
- **Regular Reporting:** Daily, weekly, and monthly access reports
- **Incident Response:** Automated response to access violations

### 12.2 Compliance Measurement
- **Access Metrics:** Regular measurement of access control effectiveness
- **Policy Violations:** Tracking and trending of policy violations
- **Remediation Tracking:** Time-to-resolution for access issues
- **Training Effectiveness:** Measurement of security awareness training impact
- **Audit Preparedness:** Regular self-assessments for external audits

---

## 13. Training and Awareness

### 13.1 Required Training
- **New Employee Orientation:** Access control policies and procedures
- **Annual Refresher Training:** Updated policies and threat awareness
- **Role-Specific Training:** Additional training for privileged users
- **Incident Response Training:** Access-related incident handling procedures

### 13.2 Training Documentation
- **Completion Records:** Training completion tracked for 24 months
- **Competency Testing:** Assessment of policy understanding
- **Refresher Requirements:** Triggered by policy changes or incidents
- **Specialized Training:** Additional training for high-risk roles

---

## 14. Incident Response

### 14.1 Access Violations
- **Immediate Response:** Account suspension for suspected compromise
- **Investigation Procedures:** Forensic analysis of access violations
- **Containment Actions:** Limiting scope of potential breach
- **Recovery Procedures:** Account restoration after investigation
- **Lessons Learned:** Post-incident review and policy updates

### 14.2 Reporting Requirements
- **Internal Reporting:** Immediate notification to security team
- **Management Notification:** Executive briefing for significant incidents
- **Regulatory Reporting:** Compliance with breach notification requirements
- **Documentation:** Detailed incident documentation and timeline

---

## 15. Policy Exceptions

### 15.1 Exception Process
1. **Business Justification:** Clear business need for exception
2. **Risk Assessment:** Analysis of security risks and mitigation
3. **Compensating Controls:** Additional security measures implemented
4. **Approval Authority:** CISO approval required for all exceptions
5. **Time Limitation:** Exceptions limited to specific time periods
6. **Regular Review:** Monthly review of all active exceptions

### 15.2 Exception Documentation
- **Exception Registry:** Central tracking of all policy exceptions
- **Risk Acceptance:** Formal risk acceptance by business owner
- **Monitoring Requirements:** Enhanced monitoring during exception period
- **Remediation Plan:** Timeline for bringing system into compliance

---

## 16. Related Documents

- **Information Security Policy** (POL-SEC-001)
- **Password Policy** (POL-PWD-001)
- **Remote Access Policy** (POL-RA-001)
- **Privileged Access Management Procedures** (PROC-PAM-001)
- **Identity and Access Management Procedures** (PROC-IAM-001)
- **Incident Response Plan** (POL-IR-001)

---

## 17. Revision History

| Version | Date | Changes | Approved By |
|---------|------|---------|-------------|
| 1.0 | 2023-02-15 | Initial version | [CISO Name] |
| 2.0 | 2024-02-15 | Added PAM requirements | [CISO Name] |
| 2.1 | 2024-08-15 | Updated MFA requirements | [CISO Name] |
| 3.0 | 2025-08-14 | PCI DSS 4.0 alignment | [CISO Name] |

---

*This document is reviewed quarterly and updated as needed to maintain PCI DSS compliance and security effectiveness.*

**Document Classification:** Internal Use Only  
**Next Scheduled Review:** February 14, 2026