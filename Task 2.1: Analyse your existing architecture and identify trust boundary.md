Entities, processes, data flows and trust boundaries: 

The existing Complaint Management System (CMS) architecture is based on the previously developed C4 diagrams. The key external entities include, Consumers, Help desk Agents, Support Staff, Help Desk Managers, and System Administrators. All of them use the system through web or mobile interfaces. The CMS may communicate to other systems outside of it, like email and SMS. The system has a web application interface, a Django-based backend, authentication and session management, and a PostgreSQL database. Users send data to the web interface, which sends it to the backend for processing and then to the database for storage. There are several trust boundaries, such as those between the web application and external users, the frontend and backend, the backend and database, and between different tenant organisations. 

 

Sensitive data: 

The CMS manages many kinds of private information in different parts of the architecture. This includes data on consumer complaints, which may include personal information, as well as records of past complaints and notes on how they were resolved made by support staff. The system also keeps track of and processes information about users, such as their login information, roles, and session information. Tenant-specific information, like organisation IDs and access rights, is also very important for keeping data separate when there are multiple tenants. Most sensitive data is stored in the PosteSQL database and processed in the backend application layer. When complaints are filed, updated, or retrieved data is also sent between different parts of the system. These flows are very important for keeping things safe. 

 

Vulnerable components: 

Certain components of the CMS architecture have the potential for security risks, which need to be analysed in greater depth. The Django backend and the API endpoints are critical, as they handle all incoming requests and apply business logic, making it a primary target for attacks like injections and unauthorised access. The authentication and authorisation mechanisms are critical, as any vulnerability in this section may allow attackers to impersonate users and gain privileged access. The isolation of the tenants, which happens by identifying the organisation, is critical in preventing cross-tenant access. Additionally, complaint input forms represent a key entry point for untrusted data, increasing the risk of injection attacks. The PostgreSQL database, which stores all complaint and user data, is another high-value target. These components will be analysed further using STRIDE threat modelling in the next task. 
