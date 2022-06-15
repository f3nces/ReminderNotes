## Passive Recon

[TOC]

### **1. Target Validation**

+ WHOIS - http://whois.domaintools.com

+ nslookup 



### **2. Finding Subdomains**

#### Websites

+ crt.sh - https://crt.sh/

+ dnsdumpster - https://dnsdumpster.com/

+ Google Dorking - 

  + https://ahrefs.com/blog/google-advanced-search-operators/
  + https://www.exploit-db.com/google-hacking-database
  
  | Operator                            | Description                                                  |
  | ----------------------------------- | ------------------------------------------------------------ |
  | "<search term>"                     | Force an exact-match search                                  |
  | **+** <term>                        | Force Google to include a term                               |
  | **-** <term>                        | Force Google to exclude a term                               |
  | **site:**                           | Search within a specific website                             |
  | **intitle:**                        | Search for a term within the title of a document             |
  | **inurl:**                          | Search only within the URL of a document                     |
  | link:                               | Search for pages that point to the URL                       |
  | related:                            | Search for web pages that are similar to the specified page  |
  | **filetype:**   <alias is> **ext:** | Filters by using the file extension of a resource            |
| cache:                              | Displays the version of a web page as it appeared when Google crawled the site |
  | **OR**<or> \|                       | Specify synonyms or alternative forms                        |
  | numrange:                           | Specifies a range                                            |
  
  

#### Tools

+ sublist3r - https://github.com/aboul3la/Sublist3r

+ OWASP  Amass - https://github.com/OWASP/Amass

+ Other tools:

  + theharvester (comes in Kali)
  + ct-exposer (find certificates assigned to subdomains) - https://github.com/chris408/ct-exposer
  + Subfinder - https://github.com/projectdiscovery/subfinder
  + Spiderfoot - https://github.com/smicallef/spiderfoot
  + Bluto - https://github.com/samyoyo/Bluto

#### Verify Live Domains
+ httprobe - https://github.com/tomnomnom/httprobe

  


### **3. Data Breaches**

#### Email Gathering

+ Search for emails, names, departments, etc. - https://www.hunter.io

#### Credential Gathering  

+ Tool for parsing breached passwords - https://github.com/hmaverickadams/breach-parse



### **4. Identifying Website Technologies**

+ wappalyzer (extension for browser)
+ whatweb (comes in Kali)
+ builtwith - https://builtwith.com/