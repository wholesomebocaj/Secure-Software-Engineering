# CIA Security Objectives

## Confidentiality Objectives (C)

Confidentiality ensures that sensitive complaint information is only accessible to authorised users.

**C1 - Protect consumer complaint data**

Complaint records may contain sensitive personal information and financial details. Only authorised users such as help desk agents and support staff of the relevant organisation should be able to access these records.

**C2 - Enforce multi-tenant data isolation**

The CMS will be used by multiple organisations (e.g. banks and telecom companies). Data belonging to one organisation must never be visible to another organisation's employees.

**C3 - Protect authentication credentials**

User login credentials and authentication tokens must be protected to prevent attacker from gaining unauthorised access to the system.

## Integrity Objectives (I)

Integrity ensures that information stored within the CMS remains accurate and cannot be modified without authorisation.

**I1 - Protect complain records from unauthorised modification**

Complaint details submitted by consumers must not be altered by unauthorised user or attackers

**I2 - Protect reolution notes and status updates**

Help desk agents and support engineers must only modify complaints they are assigned to, ensuring that resolution notes and status updates remain accurate.

**I3 - Protect audit logs and monitoring data**

System logs used by administrators and help desk managers must remain accurate and protected from tampering.

## Availability Objectives (A)

Availability ensures that the CMS remains accessible and operational for users when required.

**A1 - Ensure 24/7 complaint submission**

Consumers must be able to submit complaints through the CMS web or mobile interface at any time.

**A2 - Maintain system performance for large user bases**

The system must support millions of users without service disruption.

**A3 - Protect the system against denial-of-service attacks**

The CMS must implement mechanisms to prevent malicious user from overwhelming the system and making it unavailable.

# Security Requirements

| **Security Requirement** | **Description** | **CIA** | **OWASP ASVS** |
| --- | --- | --- | --- |
| SR1 - Enforce tenant-based access control | Each request must verify the user's organisation and role to prevent cross-tenant access to complaint data. | Confidentiality | V8.2 Authorization |
| SR2 - Validate and sanitise input | All complaint form inputs must be validated to prevent injection attacks and malicious data modification. | Integrity | V5 Input Validation |
| SR3 - Secure authentication | Users must authenticate using strong password policies and secure session management. | Confidentiality | V2 Authentication |
| SR4 - Encrypt sensitive data | Complaint data and personal information must be encrypted during transmission and storage. | Confidentiality | V9 Data Protection |
| SR5 - Implement logging and monitoring | Security events such as login attempts and complaint updates must be logged to detect tampering or misuse. | Integrity | V7 Logging |
| SR6 - Implement rate limiting | The system must limit excessive requests to prevent denial-of-service attacks and maintain service availability. | Availability | V4 Access Control |
