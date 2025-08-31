# h1 Kill Chain  

## x)

### Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains, chapters Abstract, 3.2 Intrusion Kill Chain.

The document introduces a cyber security concept call “Intelligence-Driven Computer Network Defense” which is aimed at helping organizations protect themselves against sophisticated cyber-attacks from potential attackers (hackers).  
-  Traditional cyber security tends to be reactionary rather than preventative, fixing any vulnerabilities after an attack has already taken place or succeeded, and the document discusses a different kind of threat which it refers to as “Advanced Persistent Threat” (APT).  
-  These attacks are carried out by highly skilled, organized and well-funded who conduct long-term attacks which can last several years to gain access to the system and steal sensitive information.  
-  The attackers are persistent in the sense that they do not give up after one failed attempt, they will try to achieve their goal by using different approaches until successful.  
-  It introduces a cyber-attack concept called the “Cyber Kill Chain” which is a chain of seven sequential steps that attackers must complete to be successful.
    
These seven steps are: 
-  Reconnaissance   
The attackers research their target to gather as much sensitive information as possible, which can be done from websites, mailing lists or even social media.
-  Weaponization   
The attackers create malware (malicious software) which is used to trick victims into running it on their devices, which is usually hidden within legitimate looking documents, which can be a .pdf or Microsoft Office document.
-  Delivery     
The attackers send the “weapon” to the target, the most common methods are email attachments, websites and USB removable media.
-  Exploitation      
Once successfully delivered and opened, the malware exploits vulnerabilities in an application, operating system or software and in some cases even the users themselves.
-  Installation     
The malware installs itself on the victim’s computer, creating a trojan or backdoor which the attacker will use to gain access to the system.
-  Command and Control (C2)     
The installed malware connects to the attackers’ servers which establishes a C2 channel, giving them remote “hands on the keyboard” access to the targets system.
-  Actions on Objectives     
After all the previous steps have been completed in the “chain”, the attackers accomplish their true goals which is usually the stealing of data by collecting, encrypting and extracting information from the system.  The attacker can also use their access to move laterally inside the network.      

        
-  It is important for defenders to move their detection and analysis up the kill chain as well as have a plan of action across all the phases of the kill chain.  
-  Attackers tend to re-use tools and infrastructure for it to be more economical.  By understanding these tools and infrastructure, defenders can force them to change their intrusion methods and prevent any future intrusion which have re-used the same techniques, gaining a tactical advantage over the attackers.
-  If the defenders can break any single link in the chain before the attackers complete every phase, they can successfully prevent the entire attack, so the defenders have multiple opportunities to succeed whereas the attackers must succeed at every step.  
    
Intelligence-Driven Defense:
-  Analyzing failed and successful attacks that have occurred to identify pattern and “indicators” (digital fingerprints that attackers leave behind).
-  Using the indicators to detect and stop future attacks earlier in the kill chain.
-  Understanding that ATPs tend to reuse tools, techniques and infrastructure which can become their weakness.
-  Creating a comprehensive defense strategy that can address each phase of the kill chain.  
     
The case study included in the document provides a real-world example where defenders used this approach to stop multiple related attack attempts that were carried out over several months.  They were successful in preventing the attack because they had identified recurring indicators that were used in the previous attempts.
     
My understanding of the information given in the document is that by better understanding how attackers operate by using intelligence about their methods, defenders can gain a strategic advantage and make it a lot harder as well as more expensive for attackers to succeed.  I believe this is very important because it means that defenders can be proactive instead of reactive when it comes to cyber-attacks, and in a world where everyone and everything is more interconnected than ever this is a good thing because it results in better cyber security, and that any potential attacker will have more difficulty being successful, which may prevent people from trying to hack organizations or people for malicious reasons.

## a)

-Tactic    
Refers to the “why” of an attacker’s action, such and their objective or tactical goal.       
One such tactic is “Credential Access”, which is when attackers try to steal account names and their passwords to gain access to a system.  By using legitimate credentials, the attack is harder to detect and gives the attackers more freedom within the system.  I picked this tactic because I think this is the most common method that most ordinary people think of when they consider what “hacking” is, having controlling access to someone else’s account.

-Technique     
Refers the “how”, the method an attacker uses to achieve their objective or goal.     
One technique is “Brute Force” which is a technique of attempting to gain access of accounts through repeated login attempts using different password combinations.  

-Sub-technique     
Refers to an even more detailed explanation of how a technique is used, variations or specific methods used.     
“Password Guessing” is a sub-technique of “Brute force” which involves guessing the password of a target based on common patterns, dictionary words, or personal information about the target (collected from a website or social media), and is more successful when the password is weak or the target uses the same password across multiple accounts or different websites.
“Password cracking” is another sub-technique which involved using a specialized tool to systematically test password combinations against captured password hashes (which are the algorithms used to encrypt plain text passwords, called a cipher).   

-Procedure     
Refers to the “what” and describes the details of a strategy of a technique (or sub-technique) by an attacker against their target, explaining the tools and steps used in a particular attack.     
ATP3 is a Chinese based threat group that uses various strategies, but one of them related to brute force and password cracking, is brute forcing password hashes to be able to leverage plan text credentials.     
Pony is a malware that steals credentials, using a small dictionary of common passwords against a collected list of local accounts.    



Sources    
https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf     
https://attack.mitre.org/#    
https://www.ibm.com/think/topics/mitre-attack    
https://en.wikipedia.org/wiki/Cyber_kill_chain    
https://en.wikipedia.org/wiki/Brute-force_attack    
https://stytch.com/blog/what-is-password-hashing/   
https://en.wikipedia.org/wiki/Ciphertext    
https://attack.mitre.org/docs/APT3_Adversary_Emulation_Plan.pdf    



