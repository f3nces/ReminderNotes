## Information Gathering (Reconnaissance)



[TOC]

------

### Reconnaissance

+ Untargeted and targeted reconnaissance 
  + Humans 
  + Infrastructure 
+ Targeted reconnaissance refers to gathering as much information about the target as possible 
  + **Passive**: without directly interacting with the target’s own systems 
  + **Active**: interaction with target’s systems occurs
+ Usually does not trigger any defensive measures



### Objectives
+ Mapping the real-world info onto the cyber-world
  - IP and DNS information about target’s networks
  - Details about IT systems in use, network layouts and diagrams, software versions
  - Account, Email and password information
+ Gaining info for social engineering or  spear phishing attacks
  - Organizational information
  - Personally identifiable data of the employees



### Sources of Information

#### Physical World
+ Location Information
  + Satellite Images (Google Earth, Google Maps (Street View))
  + Drone Recon
+ Recon (if possible) target’s facilities: parking / smoking area /
  + Parking / Break or Smoking Areas / Fencing
  + Security / Access controlled?
  + Restaurants nearby?
+ Dumpster-diving (search garbage)
+ Old hardware
  + How is it dismissed?
  + Can you get/buy it?



#### Target Organization’s Website
+ Organizational structure
  + E-mail addresses
  + Phone and fax numbers
+ Organization's location
+ Clients, subcontractors, projects
+ Links to other sites
+ Vacancy advertisements/procurements
+ How well is the website designed and how clean is the HTML code?



#### Public Sites, Search Engines or other Web sites (OSINT)
+ Search Engines
  + Google, Yahoo, Bing
  + Yandex, Baidu ... (use native language)
  + Google dorking 
+ Specialized Search Engines
  + Shodan
  + Censys
  + DNS Dumpster
  + crt.sh
  + Virustotal
  + Threatcrowd
  + Pastebin
  + Archive.org



#### Social Networks and Blogs
+ Social networks (Facebook, Twitter, LinkedIn, Google+, Instangram)
  + Background and skills (LinkedIn)
  + Employee CVs/data: worker CV, carreers, job title, manager, phone number, name
  + Pictures (badge photos, desk photos, computer photos, etc)
  + Friends, and cliques
  + Fellow co-workers
  + Hobbies, likes and dislikes
+ Blogs including Twitter
  + Some people could tweet about pretty sensitive information including working climate, relationships, etc.
+ Sports trackers (Strava, Endomondo, etc)
+ Accessing public-facing services



#### WHOIS & DNS Servers
+ WHOIS system holds information about Internet resources like domain names,  IP address blocks and autonomous systems
  + What IP ranges could be associated with the target
  + Contacts of who registered the domain (owner name, e-mail, address, technical contacts)
  + ISP information
+ Finding authoritative WHOIS server for a domain:
  + http://whois.domaintools.com



#### Metadata
+ Data about data
+ Extracting metadata from documents could disclose valuable information for the attacker
  + names and usernames – good for later brute-force password attacks
  + folder paths
  + e-mail addresses (discover email pattern)
  + details of document creation



#### Social Engineering
+ Exploit the HumanOS
+ Gathering data by requesting confidential information from an employee or contractor
  + help-desks tend to be friendly
  + phishing: forged e-mails, send a gift-card
  + give out USB sticks or digital photo frames
  + shoulder-surfing



