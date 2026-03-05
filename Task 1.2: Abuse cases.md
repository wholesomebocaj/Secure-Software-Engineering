# Task 2.1 Abuse Cases

#### Abuse Case 1 - Cross-Tenant Data Access

**Threat actor**: Malicious employee of Company A

**Goal**: Access complaint data belonging to another company (Company B).

**Steps**:

- Login with valid employee credentials.
- Intercept an API request used to retrieve complaints.
- Modify the organisation/tenant ID in the request
- Attempt to access complaint records belonging to another organisation

**ATT&CK**: T1190 - Exploit Public Facing Application

**CAPEC**: CAPEC-233 - Privilege Escalation

**CIA Impact**: Confidentiality

**Affected security requirements:**

- SR1 - Enforce tenant-based access control
- SR3 - Secure authentication

#### Abuse Case 2 - Injection Attack via Complaint Form

**Threat actor:** External attacker  
**Goal:** Manipulate the backend database to read or modify complaint records.

**Steps:**

- Submit a complaint through the web form.
- Insert malicious SQL or command input into text fields.
- Exploit lack of input validation.
- Extract or modify complaint records.

**ATT&CK:** T1190 - Exploit Public Facing Application  
**CAPEC:** CAPEC-66 - SQL Injection

**CIA impact:** Integrity / Confidentiality

**Affected security requirements:**

- SR2 - Validate and sanitise all input
- SR5 - Logging and monitoring

#### Abuse Case 3 - Credential Stuffing Attack

**Threat actor:** External attacker  
**Goal:** Gain access to CMS user accounts.

**Steps:**

- Obtain leaked username/password combinations from other breaches.
- Attempt automated login attempts against the CMS login system.
- Successfully authenticate into a user account.
- Access complaint records or internal system data.

**ATT&CK:** T1110 - Brute Force  
**CAPEC:** CAPEC-49 - Password Brute Forcing

**CIA impact:** Confidentiality

**Affected security requirements:**

- SR3 - Secure authentication
- SR6 - Rate limiting

#### Abuse Case 4 - Complaint Record Tampering

**Threat actor:** Malicious helpdesk employee  
**Goal:** Modify complaint records to hide mistakes or fraud.

**Steps:**

- Log into the CMS as a help desk agent.
- Access a complaint not assigned to them.
- Modify the resolution notes or complaint status.
- Save changes without proper authorisation.

**ATT&CK:** T1098 - Account Manipulation  
**CAPEC:** CAPEC-122 - Privilege Abuse

**CIA impact:** Integrity

**Affected security requirements:**

- SR1 - Tenant-based access control
- SR5 - Logging and monitoring

#### Abuse Case 5 - Denial of Service Attack

**Threat actor:** External attacker  
**Goal:** Disrupt the CMS system so consumers cannot submit complaints.

**Steps:**

- Send a large number of automated requests to the complaint submission API.
- Overload the server with excessive traffic.
- Cause system slowdown or service outage.

**ATT&CK:** T1499 - Endpoint Denial of Service  
**CAPEC:** CAPEC-125 - Flooding Attack

**CIA impact:** Availability

**Affected security requirements:**

- SR6 - Rate limiting
- SR5 - Logging and monitoring
