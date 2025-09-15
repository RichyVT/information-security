# H4 Johnny Tables

#  x) 
## OWASP: OWASP 10 2021. 
-  OWASP stands for the Open Web Application Security Project. It is a non-profit foundation and a global community that works to improve the security of software. They provide free materials to anyone interested in improving application security.      

## A01:2021 - Broken Access Control      

-  Found in 94% of tested applicatiions
-  Most common vulnerability overall

### What it is
-  System fails to properly check if users have correct permissions to access resources
-  Users can act outside of their intended permissions
-  Results in unauthorized access to functions or data

### Common attack methods
-  URL manipulation: Changing web addresses to access forbidden areas
-  Missing API controls: No permission checks on create, update or delete operations
-  Privilege escalation: Regular users gaining administrator access
-  Token manipulation: Tampering with JSON Web Token, cookies or session data
-  CORS misconfiguration: APIs accepting requests from untrusted websites
-  Force browswing: Accessing protected pages without proper login

### Prevention methods
-  Server-side only: Never rely on client-side permission checks
-  Deny by default: Block access unless explicitly granted
-  Consistent controls: Use same access control system throughout application
-  Record ownership: Users can only access their own data
-  Proper logging: Track and alert on access control failures
-  Rate limiting: Prevent automated attacks
-  Session management: Invalidate sessions properly, use short-lived tokens
-  Testing: Include access control tests in development process

### Personal observation
This seems to occur when applications do not properly restrict what users are allowed to do, allowing attackers to access other users' data or perform actions they shouldn't be allowed to do and highlights why manual testing is important to make sure an application is secure.

## A05:2021 - Security Misconfiguration     

-  Found in 90% of tested applications
-  Becoming more popular due to the common use of increasingly complex and configurable software       

 ### What it is     
 -  Systems are not set up correctly from a security standpoint, leaving "doors" unlocked that should be secured and leaving thee systems vulnerable

### Common vulnerabilites 
-  Cloud misconfigurations: Improper cloud service permissions 
-  Unnecessary features enabled: Extra ports, services, accounts, or privileges running
-  Default credentials: Unchanged default usernames and passwords
-  Information leakage: Error messages revealing stack traces or system details
-  Disabled security features: Latest security settings not enabled after upgrades
-  Insecure framework settings: Application servers, databases not configured securely
-  Outdated software: Running vulnerable or unpatched systems

### Prevention methods
-  Automated hardening process: Repeatable, fast deployment of secure environments
-  Identical environments: Same configuration for development, QA, and production (with different credentials)
-  Minimal installations: Remove unnecessary features, components, and documentation
-  Regular configuration reviews: Update settings as part of patch management
-  Cloud permission audits: Review storage permissions
-  Security headers: Send appropriate security directives to clients
-  Automated verification: Process to check configuration effectiveness across all environments

### Personal observation
-  Systems remain at risk of being vulnerable without an organized approach with systematic, repeatable security configuration processes

## A06:2021 - Vulnerable and Outdated Components   

### When you're vulnerable
-  Unknown inventory: Don't know versions of all components (including nested dependencies)
-  Outdated software: Running vulnerable, unsupported, or old versions of OS, servers, databases, APIs, libraries
-  No monitoring: Don't regularly scan for vulnerabilities or subscribe to security bulletins
-  Slow patching: Monthly/quarterly update cycles leave long exposure windows
-  Untested updates: Don't verify compatibility when upgrading components
-  Misconfigured components: Security settings not properly configured   

### Prevention methods    
-  Remove unused items: Delete unnecessary dependencies, features, and documentation
-  Continuous inventory: Use tools like OWASP Dependency Check, retire.js to track all components
-  Automated monitoring: Subscribe to CVE alerts and use software composition analysis tools
-  Trusted sources only: Obtain components from official sources using secure connections
-  Monitor maintenance status: Watch for unmaintained libraries that don't receive security patches
-  Virtual patching: If patching is not possible, deploy monitoring/protection for known issues
-  Lifecycle planning: Ongoing process for monitoring, triaging, and applying updates
  
### Personal observation
Software development has become incredibly productive by letting developers assemble applications from hundreds of pre-built components, like having access to a vast library of building blocks. However, each component you add essentially invites a third party into your "security space" and you inherit their security decisions, maintenance practices, and response times to vulnerabilities.

## A03:2021 - Injection

-  Found in 94% of tested applicatiions

### Common injection types

-  SQL Injection: Malicious database commands
-  Cross-site Scripting (XSS): Malicious JavaScript in web pages
-  OS Command Injection: System commands executed through user input
-  NoSQL, LDAP, Expression Language: Various interpreter-specific attacks

### Deteciton methods

-  Source code review: Most effective way to find vulnerabilities
-  Automated testing: Test all inputs (parameters, headers, URLs, cookies, JSON, XML)
-  Security testing tools: SAST, DAST, and IAST in development pipeline

### Prevention methods
-  Separate data from commands: Core principle for all injection prevention
-  Use safe APIs: Parameterized interfaces that avoid interpreters entirely
-  Server-side input validation: Positive validation (though not complete defense)
-  Proper escaping: Use interpreter-specific escape syntax for dynamic queries
-  Caution with ORMs: Even parameterized stored procedures can be vulnerable

### Personal observation
I find it very interesting that this is still an issue after being a known problem for a such a long time.   

## Munroe: xkcd 327: Exploits of a Mom
-  The comic is about the cybersecurity vulnerability known as SQL injection, where malicious code gets executed when user input isn't properly sanitized
-  The SQL input Robert');DROP TABLE Student;-- (which is the son's name) is a command that would delete the entire table containing all the student records
-  When the school inputs the childs name in their database (assuming it is a SQL database) they would have unknowingly executed this command
- "Sanitize your data inputs" refers to cleaning and validating any data entered by a user before using it in a database query

#  d) Sequel. Solve SQLZoo:   

## 0 SELECT basics     
-  1 . We need to change the query from "WHERE name = 'France'" to "WHERE name = 'Germany'" to show the population of Germany:              

<img width="1161" height="402" alt="{76A0C963-EB8C-4B2A-BE74-6588C1BF2ED7}" src="https://github.com/user-attachments/assets/cf76adc5-ae38-4448-aa4a-8122416b0959" />            

-  2 . We need to change the countries in the query "WHERE name IN ('Brazil', 'Russia', 'India', 'China');" to 'Sweden', 'Norway', 'Denmark' to show their names and populations:       

<img width="1166" height="451" alt="{85E3688C-7321-4A11-8847-186485BF090B}" src="https://github.com/user-attachments/assets/4ce2e9af-8d21-4e18-ad95-40f7f9190543" />         


-  3. We need to change the values in the query from "250000 AND 300000" to "200000 AND 250000"       

<img width="1175" height="441" alt="{7847B467-5FDE-44BA-9B5F-2187EC03A2EC}" src="https://github.com/user-attachments/assets/12265933-4408-44f8-8db1-976001f3c190" />        

-  Quiz     

<img width="1209" height="143" alt="{98559E74-9F12-45C5-AC29-2737A0E7834E}" src="https://github.com/user-attachments/assets/f0d6057a-ad02-47dd-b687-cbed0f79e9b8" />       

## 2 SELECT from World: First two subtasks: "1. You can use WHERE..." and "2. Find the countries...".

-  1 . The query "SELECT name, continent, population FROM world" lists the name of the country, name of the continent of said country, and its population from a table called world, and produces a table/list of the selected information.

  <img width="1165" height="404" alt="{4B28F8C4-B232-4FA6-BD9A-4DAD889AA892}" src="https://github.com/user-attachments/assets/e6479545-eb41-42d9-8766-9faf3f1e508a" />

-  2 . The query "SELECT name FROM world WHERE population >= 200000000" lists the name of the countries from a table called world where the population is equal to or greater than 200 million, and produces a table/list of the results.    

<img width="1168" height="409" alt="{C31EB60C-13CA-4EFB-99C2-84648AEE89E0}" src="https://github.com/user-attachments/assets/4b461c15-df12-4ed8-8e38-6f4773f071be" />      

- 3 . The query "SELECT name, gdp/population FROM world WHERE population > 200000000;" lists the name of the countries and the gdp/population from the table called world where the population is at least 200 million

<img width="1162" height="402" alt="{C25A49B9-A2F3-4940-94FA-016052701A5D}" src="https://github.com/user-attachments/assets/e3e7750a-4e62-4ad7-b2d6-bfbe8c69c28b" />     











## Sources
https://owasp.org/Top10/A01_2021-Broken_Access_Control/     
https://owasp.org/Top10/A05_2021-Security_Misconfiguration/    
https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/     
https://owasp.org/Top10/A03_2021-Injection/     
https://en.wikipedia.org/wiki/OWASP    
https://www.akamai.com/glossary/what-is-owasp    
https://www.blackduck.com/glossary/what-is-owasp-top-10.html    








