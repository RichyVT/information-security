# h1 Should Tero wear a helmet

# Threat modeling

## x)

### o	Braiterman et al 2020: Threat modeling manifesto
-	Identifying potential security/privacy problems in a system (ideally before they can be exploited, and throughout its lifetime with frequent analysis).
-	Everyone can and should be concerned about privacy, safety and security of their system.
-	Values 
Culture of finding and fixing any problems rather than a guideline that is set in stone.
People and teamwork over tools and processes.
Doing threat modelling rather than just discussing it.
Frequent analysis rather than a one-and-done attitude.
-	Principles –
Goal is to improve security and privacy with early and frequent analysis of the system.
Integration should align with an organizations practices and must be manageable.
Outcome should reflect value to stakeholders
Process should be systematic, include different viewpoints and be documented, enabling repeatability as well as providing measurability.
-	Things to avoid (anti-patterns)
Relying on only one person’s knowledge or expertise.
Analyzing issues without seeking proper/possible solutions.
Tendency to overfocus, don’t lose sight of the big picture by focusing only on a single aspect.
Seeking one ideal view instead of multiple perspectives.

### o	Shostack 2022: Welcome to the Worlds Shortest Threat Modeling Course (12 parts, about 15 min total, audio is enough for all except video 7 "Data flow diagrams")
-	We do it to anticipate any problems when it’s still inexpensive to deal with them.
-	Set of methods that allow us to identify any potential issues, resulting in a more secure system.

-	Good starting points for threat modelling 
- What are we working on? Collaborating and sketching (brainstorming/sharing ideas with colleagues) is encouraged, as well as proper documentation/recording of the process.
External entities –> data flows –> data stores –> external entities –> processes (data flow diagram)
- What can go wrong? Using STRIDE (Spoofing, Tampering, Information Disclosure, Denial of Service, Elevation of Privileges) or kill chain can provide guidance.  Structure (in how we think about threats) is necessary so that when many people collaborate, consistency is provided.
- What are we going to do about it? Writing a feature, deploying a control, risk management.  Somethings are fixable, others are not and that is where risk management comes into play.
- Did we do a good job?  Were the participants’ efforts worthwhile? If yes, then we have done a good job, if no, then we still need to improve.

### o	OWASP CheatSheets Series Team 2021: Threat Modeling Cheat Sheet
-	Threat modelling should be done as early as the design phase of the SDLC (Software Development Life Cycle).
-	Built-in is preferable to bolt-on.
-	“Think like an attacker mindset” and improved visibility into systems and its interactions will be beneficial when threat modelling.
-	Common problems:
Some developers lack knowledge of security when it comes to systems.
Time consuming
Poor communication between teams.
Lack of tools, resources and education.
-	STRIDE is a popular threat modelling technique.
Spoofing –> attacker impersonates a legitimate user.
Tampering –> attacker maliciously updates a database.
Repudiation –> attacker manipulates logs to cover their actions.
Information disclosure –> attacker extracts data (user info) from database.
Elevation of privileges –> attacker tampers with JWT to change their role.
-	Ranking threats based on likelihood and impact.
-	META - Mitigate, Eliminate (remove potential problematic features), Transfer (shift responsibility), Accept (do nothing due to constraints).
-	Some solutions may be: 
Have team meetings with the people responsible for security, provide regular cross-team workshops.
Invest in regular security training.
Implement automated tools that can facilitate the detection of a threat or the increase in security.
Promote security culture as an integral part of the SDLC.

### Darknet diaries Ep. 72: The Bangladeshi bank heist
-	This episode is about a bank heist that happened in 2016, involving North Korean hackers and the Bangladesh bank, as well as the New York federal reserve.
-	The hackers (known as Lazarus group) attempted to steal nearly $1billion USD ($951 million USD) from the Bangladesh bank, the funds were being stored at the New York Reserve.
-	The heist was carried out by infiltrating the bank’s computer systems.
-	The attackers sent phishing emails to the employees (of the Bangladesh Bank) in 2015, and once they gained access to the network, they spent months learning how the banks systems worked, focusing their efforts on SWIFT, the international banking transfer system.
-	They discovered that the Bangladesh Bank has approximately $1 billion USD stored at the New York Federal Reserve.
-	They timed their attack during a long weekend in February 2016, using the different time zones and holidays to their advantage.
-	Although they attempted to transfer $951 million USD, they only managed to successfully transfer $81 million USD, to bank accounts that the attackers had set up in the Philippines.
-	The rest of the funds were blocked when suspicious details were noticed related to the transfers, such as a foundation name that was misspelled which alerted the bank.
-	The hackers laundered the stolen funds through casinos in the Philippines, where they used a strategy which made the money look legitimate before cashing out and disappearing.
-	A big surprise was the fact that it wasn´t just any ordinary cybercriminal group, it was done by the infamous Lazarus group, a group of hackers backed by the North Korean government, which in my opinion made the topic extra interesting as they are a very well-known group.
-	The Lazarus group were the ones responsible for hacking Sony Pictures (movie production company) when the movie “The Interview” was announced (a comedy movie about 2 Americans that go to North Korea).
-	Although the attackers got away with the stolen funds, the US department of Justice identified and charged one North Korean programmer, although he remains at large, so the group technically got away scot-free and $81 million dollars richer.
-	I thought the topic was very interesting because it was about a nation-state carrying out a cybercrime for financial gain against another country.

## a) 
Security hygiene.      
What basic security practices should everyone follow? Are there some security hygiene practices that every company or average Joe should follow? (This subtask does not require tests with a computer. A bullet list is enough)
-	Use a password manager when possible, and use unique, strong passwords for every account.
-	Use multi-factor authentication when possible.
-	Keep your software up to date and enable automatic updates.
-	Be cautious with emails, their attachments and links, verify the sender before opening them.
-	Use good anti-virus software.
-	Get in the habit of regularly backing up your data.
-	Use encrypted messaging apps when transmitting sensitive information.
-	Secure your wi-fi, use strong encryption (WPA3)
-	Be mindful of what you share on social media.
-	Provide employee security awareness training.
-	Regular security assessment and penetration testing.
-	Control physical access to facilities and equipment.

## b) 
Make-belief boogie-man - a threat model for imaginary company       
My imaginary company will be a medium sized wine producer called Tasty Wines Co. which focuses on direct-to-consumer sales via their online store.   

## (1)	What are we working on?
“Crown Jewels”
-	Customer payment data (credit card or banking info)
-	Customer information and their purchase history.
-	Wine inventory and price data.
-	Proprietary wine recipes and production process.
High-value assets
-	Company website and e-commerce platform.
-	CRM (customer relationship management) system.
-	Financial and accounting data.
-	Employee personal information.
Medium-value assets
-	Marketing materials and social media accounts.
-	Business communications.
-	Office IT equipment.
-	Production facility security system.
    
Company systems:       
Customer –> load balancer –> firewall –> web servers –> application servers –> database cluster –> payment gateway –> Internal network (CRM system, inventory management, email server, employee workstations)

Customer is king:        
The customer(s) interact with us as several touchpoints.       
The primary and most important is through our e-commerce website, where they can browse our wine catalog, read about any wines they are interested in, and finally make a purchase.  It is essential that the website remains operational 24/7 since customers make their purchases at any given time.
Customers also interact with us through email communications for order confirmations, shipping notifications, our monthly newsletter or any other inquiries they might have.  Some customers also contact our sales team via the phone to place purchase orders or to ask any additional questions.  These touchpoints are important to our business operation, and it is vital that we maintain our customers’ trust by protecting their personal data, payment information and guaranteeing a reliable service. 
Our business depends on maintaining this trust relationship, if they were to lose confidence in our ability to keep this information secure, or deliver our product consistently, they may choose another producer which would mean a loss of revenue.  It would negatively impact on our company reputation and may result in a loss of future potential clients and their business.

## (2)	What can go wrong? 
I will use the STRIDE analysis that I mentioned earlier.
- Spoofing   
Attackers could create a fake website that is identical to ours to steal customer credentials.
Employees could have compromised their email accounts, leading to fraudulent communications with the customers or the theft of their information.
Counterfeit wine could be sold with our brand name.
- Tampering     
Wine information or customer orders (such as price or quantity) could be modified, leading to financial loss or worse.
Product reviews could be manipulated to damage our reputation (review bombing).
- Repudiation      
Customers could deny placing expensive wine orders.
Employees can claim they didn’t access sensitive customer information when they actually did.
3rd party vendors could deny receiving payment for services.
- Denial of service     
Our website could be overwhelmed during peak seasons, e.g. holidays, after new wine product releases.
Payment processing systems could be disrupted, preventing any sales from going through.
Our email systems could be flooded, delaying or preventing communication with the customers. 
- Elevation of privileges      
Web application vulnerabilities could allow any potential attacker to gain administrative access to our systems.
Employees accounts could be compromised and used to access our systems.
3rd party integrations could result in unintended access to our internal systems.


High priority risks      
- Data breach of our customers payment data.
- E-commerce site downtime during peak seasons or otherwise.
- Ransomware attack.

Threat Actor Analysis       
We need to understand who might want to target us to prepare for such an attack from any such threat actors.
Cybercriminal group: Profit target attackers may want to target our payment processing systems or customer databases to obtain valuable information they can later use to exploit for financial gain.  They may try to use any potential vulnerability that exist in our e-commerce platform.
Competitor corporate espionage: Other wine companies (competitors) may attempt to steal our proprietary wine recipes, customer lists, or pricing strategies.  This can be done by social engineering against our employees or ex-employees who have access to our company’s sensitive information.
Opportunistic hackers: Someone might try to hack us simply because we are accessible, using unsecured databases or weak passwords which they can use to gather information about our company and then sell it further to any interested party.

Business Continuity Considerations           
Our business model creates a few critical dependencies which threat actors could attempt to exploit.  We sell the majority of our product online, so any disruption to our website or e-commerce platform may result in a potential loss of revenue and business.  
Wine production is also seasonal, therefore any disruption during harvest or bottling periods may cause disproportionate damage to our business.
Our reputation within the winde industry is one of our most important assets, any negative publicity (about security breaches or counterfeit products) can potentially result in loss of revenue, reduced future business and could damage our brand image.
Customer trust is also a very important asset to our business, many of our customers trust our company and product which is why they make repeat purchases.  If we were to do anything that will negatively impact this trust, we would lose customers and their business, especially in an industry that relies heavily on word-of-mouth and wine enthusiast communities.


## (3)	What are we doing about?        
META     
Mitigate (reduce risk)         
-	Use multi-factor authentication for all employees, especially when accessing sensitive data.
-	Using firewalls and intrusion detection systems is possible.
-	Encrypt all customer information.
-	Provide security awareness meeting at regular intervals for all employees.
Eliminate (remove any potential risk)           
-	Use 3rd party payment processors instead of storing payment and credit card data internally.
-	Use cloud services for our email systems, providing better security infrastructure than our in-house system.
-	Outsource IT infrastructure management to specialized security firms.
Transfer (Share risk)             
-	Purchase cyber liability insurance coverage, covering any potential data breaches and business interruptions.
-	Require vendors to have specific insurance coverage and security certificates.
-	Use contracts which clearly define liability for security incidents.
Accept (acknowledge and monitor)           
-	Accept the risk of possible website defacement attacks, they are low impact and easily fixed with manageable recovery.
-	Accept the possibility of customer account compromises which can be solved with communicating with the customer.

Reduce attack surface          
Reducing our attack surface means limiting the ways attackers can reach our valuable assets.  We achieve this by segmenting our network so that any customer-facing system is isolated from other internal business systems.  We also limit the number of our services that are connected to the internet wherever possible and disabling any applications which are unused.
We also implement the principle of least privilege for all employees, e.g. sales staff do not have access to the company’s financial systems and productions employees do not have access to customer data, this reduces the risk of any potential damage from any employee accounts that might be compromised. 

## (4)	What are we doing about it?      
Threat modeling is an ongoing process, and like our business, it must evolve with time.       
- Every quarter we revisit our threat model to assess whether any new business processes, technologies, or market conditions have created new risks, e.g. if we start selling our wines to more countries, we need to consider the new regulatory requirements and risks.
- Annual penetration tests are carried out by professional security firms, using the same techniques that real attackers would use to help us identify any potential vulnerabilities in our systems that need to be addressed.
- We provide regular security meetings for our employees, seeing as they are potentially our company’s’ greatest vulnerabilities, this includes information about phishing and other social engineering techniques that real attackers would use.


##Sources     
https://darknetdiaries.com/episode/72/     
https://www.threatmodelingmanifesto.org/    
https://www.youtube.com/watch?v=2pvprvsr1lo&list=PLCVhBqLDKoOOZqKt74QI4pbDUnXSQo0nf&index=1      
https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html    
https://www.enisa.europa.eu/topics/cyber-hygiene     
https://owasp.org/www-community/Threat_Modeling      
https://en.wikipedia.org/wiki/Threat_model     
https://www.ncsc.gov.uk/collection/risk-management/threat-modelling       
https://www.practical-devsecops.com/types-of-threat-modeling-methodology/       

