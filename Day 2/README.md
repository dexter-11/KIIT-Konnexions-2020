# Day 2 [Reconnaissance / Footprinting]

### What is Footprinting ?
Footprinting is a vital first step in the process of penetration testing because it allows for
the gathering of information, both passively and actively, about your intended target of
evaluation. Spending a good amount of time learning about your target before you start
launching attacks and strikes against it will allow for more precise targeting and more
accurate and productive actions. In addition, taking time to gain information and plan
your next steps will allow you to be more stealthy.

### Objective:
The objective of Footprinting is to gather details about -
1. Network information
2. Operating system information
3. Organization information, such as CEO and employee information, office information, contact numbers, and email
4. Network blocks
5. Network services
6. Application and web application data and configuration information
7. System architecture
8. Intrusion detection and prevention systems
9. Employee names

### Types of Information Gathering:
1. Passive : Eg. Publicly available online  (Google, Social Media)
2. Active : Eg. Social Engineering

### Tools Used:
1. **Google Dorks** : Used to gather data available publicly using targeted search techniques.
2. **Shodan** : Shodan is a search engine that lets the user find specific types of computers connected to the internet using a variety of filters. Some have also described it as a search engine of service banners, which are metadata that the server sends back to the client.

Alternatives - **Viz.greynoise.io**  OR  **Censys.io**

3. **https://archive.org/** : Get archived content of a website corresponding to a particular date.
4. **https://www.netcraft.com/** : Gather information about the website/domain/server and services running on it.
5. **whois** : This utility helps you gain information about a domain name, including ownership information, IP information, netblock data, and other information where available.
6. **[nslookup](https://network-tools.com/nslookup/)** : This utility is used to query DNS servers and gain information about various parts of the DNS namespace or individual hosts. 
7. **ping** : Utilizing ICMP, this utility is used to determine not only if a host is reachable, but
also if it is up or down.
8. **traceroute** :  Traceroute procedure allows you to find out precisely how a data transmission (like a Google search) traveled from your computer to another. Essentially, the traceroute compiles a list of the computers on the network that are involved with a specific Internet activity.
9. **whatweb** : WhatWeb identifies websites. Its goal is to answer the question, “What is that Website?”. WhatWeb recognises web technologies including content management systems (CMS), blogging platforms, statistic/analytics packages, JavaScript libraries, web servers, and embedded devices. WhatWeb has over 1700 plugins, each to recognise something different. WhatWeb also identifies version numbers, email addresses, account IDs, web framework modules, SQL errors, and more.
10. **nikto** : It is a web server scanner which performs comprehensive tests against web servers for multiple items.
11. **theharvester** : Gathers emails, subdomains, hosts, employee names, open ports and banners from different public sources like search engines, PGP key servers and SHODAN computer database.

**USAGE**
```
theHarvester -d tesla.com -b google -l 1000
nikto -h https://url
traceroute <ip>
dirb https://url
```



#### Google Dorks - 
```
site: <url>        site url only
-s: <url>          subdomains of url
inurl: <url>       text in complete url
filetype: <url>    pdf/php/txt/other
intitle: <url>     in heading title
intext: <url>      in website body

Eg - intext:“aspx” filetype:txt login pass         -> can find default and common login passwords easily for sites
     inurl:control/userimage.html                  -> all IP cameras use this url
```
### $HACKERSPLOIT_ Google Hacking
https://hackersploit.org/google-hacking-for-penetration-testing/ (Exteremely helpful!)
