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




## Sources
https://owasp.org/Top10/A01_2021-Broken_Access_Control/     
https://owasp.org/Top10/A05_2021-Security_Misconfiguration/    
https://owasp.org/Top10/A06_2021-Vulnerable_and_Outdated_Components/     
https://owasp.org/Top10/A03_2021-Injection/     
https://en.wikipedia.org/wiki/OWASP    
https://www.akamai.com/glossary/what-is-owasp    
https://www.blackduck.com/glossary/what-is-owasp-top-10.html    








