## Abuse Cases

**Actors:**

External attacker,

Authenticated malicious user,

Compromised user account,

Malicious website acting via victim's browser (CSRF)

  -----------------------------------------------------------------------
  Abuse Case     Abuse Case Title     Actor             Goal
  Number                                                
  -------------- -------------------- ----------------- -----------------
  1              Cross-Tenant data    Authenticated     Read or modify
                 access               user              another tenant's
                                                        data

  2              CSRF account         Malicious website Perform actions
                 manipulation                           as victim

  3              Password brute force External attacker Gain access to
                                                        account

  4              Session hijacking    External attacker Take over an
                                                        active user
                                                        session

  5              SQL injection        External attacker Execute
                                                        unauthorized SQL
                                                        queries to read,
                                                        modify, or delete
                                                        database data

  6              Password database    External attacker Crack passwords
                 compromise                             offline
  -----------------------------------------------------------------------

## Abuse Case 1

### Title

- Cross-Tenant data access

###  Actor 

- Authenticated user

###  Goal 

- Read or modify another tenant's data

### Preconditions 

- Attacker has a valid authenticated account

- Application relies on user supplied tenant ID

- Missing or inconsistent tenant checks on backend APIs

### Trigger

- Attacker modifies request parameters (e.g. tenantId)

###  Main flow

1.  Attacker logs in as a valid user

2.  Intercepts an API request

3.  Changes tenantId to another tenant

4.  Backend does not re-validate tenant ownership

5.  System returns unauthorised tenant data

Postconditions

- Confidential cross-tenant data exposed

- Regulatory and trust impact

Mitigations

- Enforce tenant isolation server-side on every request

- Never trust client-provided tenant identifiers

- Add authorisation middleware

### MITRE ATT&CK

- T1190 -- Exploit public facing application

- T1068 -- Privilege escalation

## Abuse Case 2

### Title 

- CSRF account manipulation

### Actor

- Malicious website

### Goal

- Change victim's account data without consent (integrity breach)

### Preconditions

- Victim is logged in

- No CSRF token protection

- Sensitive actions triggered by POST/GET

### Trigger

- Victim visits attacker-controlled website

### Main Flow

1.  Victim logs into the application

2.  Victim opens malicious website

3.  Website silently submits a forged request

4.  Browser includes valid session cookies

5.  Application accepts request as legitimate

### Postconditions

- Password / email changed

- Potential account takeover

### Mitigations 

- CSRF tokens

- Strict cookies

- Double submit cookie pattern

- Re-authentication for sensitive actions

### MITRE ATT&CK

- T1189 -- Drive by compromise

- T1056 -- Input capture

## Abuse Case 3

### Title 

- Password brute force attack

### Actor

- External attacker

### Goal

- Gain unauthorised access to a user account by repeatedly attempting
  different passwords

### Preconditions

- Login endpoint is publicly accessible

- No or weak rate limiting on authentication attempts

- No account lockout or CAPTCHA after failed attempts

- Attacker can automate requests

### Trigger

- Attacker submits repeated login requests to the authentication
  endpoint

### Main Flow

1.  Attacker identifies the login endpoint

2.  Attacker uses an automate script or tool to submit many password
    attempts

3.  Application processes each attempt without blocking

4.  Correct password is eventually guessed

5.  Attacker successfully authenticates as the victim

### Postconditions

- Attacker gains full access to the victim\'s account

- Senstivice user data may be accessed or modified

- Account may be used for further attacks

### Mitigations 

- Rate limiting on login attempts

- Account lockout after multiple failed attempts

- CAPTCHA after repeated failures

- Strong password policy

- Monitoring and alerting for abnormal login behaviour

### MITRE ATT&CK

- T110 -- Brute force

  - T1110.001 - Password guessing

  - T1110.003 - Password spraying

## Abuse Case 4

### Title 

- Session Hijacking

### Actor

- External Attacker

### Goal

- Take over an active user session

### Preconditions

- Session IDs not rotated on login

- No HTTPS or secure cookie flags

- Predictable session identifiers

### Trigger

- User logs in from shared or insecure network

### Main Flow

1.  Attacker captures session ID

2.  Reuses stolen session ID

3.  Application accepts session as valid

4.  Attacker gains full user access

### Postconditions

- Full account compromise

- Unauthorised actions performed

### Mitigations 

- Secure cookies

- HTTPS everywhere

- Session rotated on login

- Short session expiration

### MITRE ATT&CK

- T1539 -- Steal web session cookie

- T1040 -- Network sniffing

## Abuse Case 5

### Title 

- SQL Injection

### Actor

- External Attacker

### Goal

- Execute unauthorised SQL queries to read, modify, or delete database
  data, leading to confidentiality and integrity breaches.

### Preconditions

- Application uses dynamic SQL queries built with user input

- Input fields are not properly validated or sanitised

- No use of parameterised queries or prepared statements

- Database user has excessive privileges

### Trigger

- Attacker submits malicious SQL payload through an input field (e.g. a
  login form or search box)

### Main Flow

1.  Attacker identifies an input field that interacts with the database

2.  Attacker submits a crafted SQL payload

3.  Application concatenates the input directly into a SQL query

4.  Database executes the injected SQL command

5.  Attacker gains unauthorised access to data or modifies database
    records

### Postconditions

- Sensitive data is disclosed or altered

- User accounts may be compromised

- Database integrity is reduced

- Potential full system compromise

### Mitigations 

- Use parameterised queries / prepared statements

- Implement strict input validation

- Use ORM frameworks

- Apply least-privilege access to database accounts

- Log and monitor suspicious query behaviour

### MITRE ATT&CK

- T1190 -- Exploit public facing application

- T1059 -- Command and scripting interpreter (SQL)
