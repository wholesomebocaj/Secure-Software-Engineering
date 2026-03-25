Element: Web application / Complaint form 

|

Interaction 

 |

T 

 |

I 

 |

D 

 |
|

Submitting a complaint 

 |

Input fields could be manipulated with malicious input to change how the system behaves. 

CIA: I 

ATT&CK: T1190 

CAPEC: 66 

 |

Sensitive complaint data could be exposed if the form handling or error messages are not secure. 

CIA: C 

CAPEC: 118 

 |

A large number of requests could overwhelm the complaint submission system and make it unavailable. 

CIA: A 

ATT&CK: T1499 

CAPEC: 125 

 |

Element: Authentication System 

|

Interaction 

 |

S 

 |

R 

 |

I 

 |

D 

 |

E 

 |
|

Logging into CMS 

 |

An attacker could use stolen credentials to log in as a legitimate user. 

CIA: C 

ATT&CK: T1110 

CAPEC: 49 

 |

A user could deny login activity if proper logging is not in place. 

CIA: I 

 |

Error messages during login could reveal valid usernames. 

CIA: C 

CAPEC: 115 

 |

Repeated login attempts could lock accounts or slow down the system. 

CIA: A,  

ATT&CK: T1110 

 |

If credentials are compromised, an attacker could gain access to higher-level accounts. 

CIA: C/I 

ATT&CK: T1078 

 |

Element: Django Backend / API 

|

Interaction 

 |

T 

 |

R 

 |

I 

 |

D 

 |

E 

 |
|

Viewing or updating complaints 

 |

Complaint status, notes, or tenant IDs may be modified in requests.  

CIA: I  

CAPEC: 115 

 |

Without proper logging, staff could deny making unauthorised changes. 

CIA: I 

 |

Weak access control could allow users to view complaints from other organisations.  

CIA: C  

CAPEC: 233 

 |

Too many API requests could slow down or disrupt the system. 

CIA: A  

ATT&CK: T1499 

 |

Users might access staff-only features if role checks are not enforced properly. 

CIA: C/I 

 |

Element: Tenant Isolation Logic 

|

Interaction 

 |

T 

 |

I 

 |

E 

 |
|

Submitting a complaint 

 |

Changing tenant IDs in requests could affect which data is accessed. 

CIA: I  

CAPEC: 115 

 |

A malicious user could access complaint data belonging to another organisation. 

CIA: C  

CAPEC: 233 

 |

A user might bypass tenant restrictions and gain access to data they shouldn't see. 

CIA: C/I  

ATT&CK: T1078 

 |

Element: PostgreSQL Database 

|

Interaction 

 |

T 

 |

R 

 |

I 

 |

D 

 |

E 

 |
|

Storing complaints, users and history 

 |

Complaint records or history data could be changed through insecure queries. 

CIA: I\
CAPEC: 66 

 |

If logging is weak, it may not be possible to trace who made changes. 

CIA: I 

 |

If the database is compromised, sensitive complaint and user data could be exposed. 

CIA: C 

 |

Heavy queries or too many requests could impact database performance. 

CIA: A 

 |

If the application has too many database permissions, it could lead to wider system compromise.  

CIA: C/I 

 |

Element: Audit / History Records 

|

Interaction 

 |

T 

 |

R 

 |

I 

 |
|

Recording updates and actions 

 |

Logs could be altered to hide malicious activity.\
CIA: I 

 |

If logging is not secure, users could deny actions they performed. 

CIA: I 

 |

Logs might expose sensitive complaint or account information if not protected. 

CIA: C 

 |

Element: External Email / SMS Service 

|

Interaction 

 |

S 

 |

T  

 |

R  

 |

I  

 |

D  

 |
|

Sending notifications to users 

 |

Attackers could spoof notification sources to trick users.  

CIA: C 

 |

Message content could be altered if communication is not secure. 

CIA: I 

 |

Users might dispute receiving notifications if there is no proper record. 

CIA: I 

 |

Notification messages could expose sensitive complaint details. 

CIA: C 

 |

If the service is flooded or fails, users may not receive important updates. 

CIA: A 

 |

Element: Admin Functions 

|

Interaction 

 |

S  

 |

T  

 |

R  

 |

I  

 |

D  

 |

E  

 |
|

Managing tenants, users, and roles 

 |

An attacker could impersonate an admin using stolen credentials. 

CIA: C  

ATT&CK: T1078 

 |

Roles or tenant settings could be changed without proper authorisation. 

CIA: I 

 |

Admins could deny making critical changes if actions are not logged. 

CIA: I 

 |

Incorrect permissions could expose all tenant data. 

CIA: C 

 |

Misuse of admin features could disrupt system access or onboarding. 

CIA: A 

 |

If an attacker gains admin access, they could control users, roles, and data across the system. 

CIA: C/I/A  

ATT&CK: T1078 

 |
