# Day 1 [Introduction to Ethical Hacking | Linux Basics | Networking]

## Software Requirments

1. VirtualBox - 6.1.4 [ [Download](https://download.virtualbox.org/virtualbox/6.1.14/VirtualBox-6.1.14-140239-Win.exe) ]
2. Kali Linux 64-Bit - 2020.3 [ [Download](https://cdimage.kali.org/kali-2020.3/kali-linux-2020.3-installer-amd64.iso) | [Torrent](https://images.kali.org/kali-linux-2020.3-installer-amd64.iso.torrent) ]
3. Metasploitable2 [ [Download](https://nchc.dl.sourceforge.net/project/metasploitable/Metasploitable2/metasploitable-linux-2.0.0.zip) ]
4. Burp Suite Community Edition [ [Download](https://portswigger.net/burp/releases/professional-community-2020-9-1) ]

## Hardware Requirements

1. Laptop :)
2. External WiFi Adapter [**Not Necessary**] 
   Should support Monitor mode & Packet Injection - *Buy only if you wish to practice Wireless hacking (Demo will be shown)*

## Installation

1. [Youtube Tutorial](https://www.youtube.com/watch?v=yH4plWQ5UbE&ab_channel=OSDock) to install Kali Linux in VirtualBox.
2. Kali Regular Repo : **`deb http://http.kali.org/kali kali-rolling main non-free contrib`**
3. Make sure your **/etc/apt/sources.list** has the above entry, if it doesn't add it and save the file.
4. After booting up Kali, add yourself to the sudoer's list. Run the command **`sudo usermod -a -G $USER root`**. Check sudo rights - **`sudo -l`**
5. Kali 2020.1 onwards, Kali discarded the default root-user policy. Enable it [here](https://itsfoss.com/kali-linux-root-user/).
6. Ensure Virtualbox Guest Additions is properly installed [here](https://www.kali.org/docs/virtualization/install-virtualbox-guest-additions-kali/)
7. Issue with Shared Folder access permissions - [Solution](https://innovativebeast.com/shared-folder-permission-denied-issue-in-virtualbox/)

## Resources

1. [Read](https://www.kali.org/blog/) about the Kali releases and it's features. Visually, it has become quite interesting recently! 
2. [Introduction to Ethical Hacking](http://wiki.cas.mcmaster.ca/index.php/Ethical_Hacking)
3. [Basic Kali Linux Commands](https://github.com/dexter-11/Konnexions-2020/blob/master/Day%201/Kali-Linux_Command_List.txt)
4. Linux essentials for Hackers - [Hackersploit](https://hackersploit.org/linux-essentials-for-hackers/) || [Nullbyte](https://null-byte.wonderhowto.com/how-to/linux-basics/) - RECOMMENDED




## Day 1a [Handy commands and actions]

### Your handy terminal shortcuts!
* *Ctrl+C* Terminates a job/process
* *Ctrl+Shift+C* Copy
* *Ctrl+Shift+V* Paste

### Keep system and applications up-to-date

**`sudo apt-get update && sudo apt-get upgrade`** OR **`sudo apt update && sudo apt full-upgrade`**    -> Update the kali repositories

**`sudo apt-get install <application_name>`** -> Install/update git community repositories


### Access privileges
Most Popular command - **`chmod 777 <file>`**   
            
When we want to set permissions, we just add up the number. 
For example, to set the permissions to read and write, we will use ‘6’ (4 + 2) for the permission. 
 
Here are the different permutations:
   * 0 – *no permission*
   * 1 – *EXECUTE*
   * 2 – *WRITE*
   * 3 – *write and execute*
   * 4 – *READ*
   * 5 – *read and execute*
   * 6 – *read and write*
   * 7 – *read, write, and execute*
   
Depending on the permissions you want to grant to the file, you just set the number accordingly.
What about the 3 digits ‘777’? Well, the First digit is assigned to the Owner, the Second digit is assigned to the Group and the Third digit is assigned to the Others. 
**So for a file with ‘777’ permission, everyone can read, write and execute the file.**


## Day 1b [Types of Hackers | Networking]

1. [Hacker_Roadmap](https://github.com/sundowndev/hacker-roadmap#wrench-exploitation-tools) (:star: Star this repository for future reference)

2. [Types of Hackers](https://www.malwarefox.com/types-of-hackers/) 

#### NETWORKING
```
sudo ifconfig 
OR ip -a           // network adapter information (Your machine's IP is visible at eth0)
iwconfig           // wlan adapters information
ping <ip/url>      // ping to check connection and stability
arp -a             // IP address with MAC address
route              //routing table tells you where the traffic exits
netstat -ano       // all open connections and which one is talking from what port number
```

* Running a local sever on Kali machine -> **`python -m SimpleHTTPServer 8080`** <br/>
Now, go in any browser and enter **<kali_ip>:8080** to access system files! <br/>

TCP : https   smtp   ftp <br/>
    1. Connection oriented <br/>
    2. Give Response <br/>
    
UDP : dns   ntp <br/>
    1.No response <br/>

_____________Three Way Handshake______________ <br/>
CLIENT  ---------->Server    <br/>
          *syn* <br/>
CLIENT<-----------Server <br/>
          *ack+syn* <br/>
CLIENT----------->Server<br/>
          *ack* <br/>
Connection complete! <br/>
______________________________________________ <br/>

* **Flags** <br/>
FIN - transmission finished <br/>
PSH - send buffer <br/>
URG - important packet <br/>
RST - Reset connection <br/> <br/>

* Read about a [**Christmas Tree packet**](https://en.wikipedia.org/wiki/Christmas_tree_packet).
<br/>
[NOTE : FIN & RST packets go through the firewall, but have no response] <br/> <br/>

* **Ports**  <br/>
1.Open  - that actively respond to incoming connection <br/>
2.Closed  - that respond but does not have any services running on that port (Firewall not present) <br/>
3.Filtered - (Firewall present) protected and prevents nmap from determining open/closed <br/>
4.Unfiltered  -  nmap can access but cannot determine open/closed <br/>
5.Open-filtered - nmap belives to be open but can not say <br/>
6.Close-filtered - nmap belives to be closed but can not say <br/> <br/>


### Staying Anonymous in Kali Linux
[How to stay anonmous](https://www.youtube.com/watch?v=VZMHfO9rOCg&list=PLBf0hzazHTGOh6JBKc8WkpyuZgDPW6yTk&ab_channel=HackerSploit)
