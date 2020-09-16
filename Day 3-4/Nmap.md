# NMAP
```
             Timing templates
               |
nmap   -sS   -T2   192.168.2.1   -oN
        |                         |
     Scanning option            Output options
        
 
nmap -O <target_ip>              _OS Scan
          -sS                    _scan all ports (never complete 3-way TCP handshake) - STILL SCAN    
          -sV                    _port and service versions on target 
          -v                     _verbose output
          -A                     _aggressive scan ( -O and -sV together)
          -sP                    _All Live hosts in the network                         ...Alternative - "netdiscover"
          -sT                    _full TCP connection made -TCP SCAN
          -sU                    _access UDP port (expect to recieve reply back from system that port is open/closed)  -UDP SCAN
          -sA                    _determine if port is filtered / unfiltered (Check for firewall !) 
          -f                     _A typical nmap scan sends 24 bytes of TCP packet by DEFAULT (8 byte/fragment=3 fragments), So each of this command adds 8 bytes=1 fragment to the Default sent packet.
          -iL <ip.txt>           _Scans a list of ip addressess from a file
          -sN                    _Ping scan, disable port scan
          
                       -T0          _Paranoid Scan [IDS Aversion]
                       -T1          _Sneaky Scan [IDS Aversion]
                       -T2          _Polite Scan [Uses quite less bandwidth]
                       -T3          _Normal Scan [DEFAULT]
                       -T4          _Agressive Scan [Speeds up scan, Take more bandwidth]
                       -T5          _Insane Scan [Assumes fast network, Takes most bandwidth and give up some accuracy for speed]
                             -oN        _Normal Output [Create text file that can be used for evaluation or into another command]
                             -oX        _XML Output [Input into different apps]
                             -oG        _Greppable Output [Most used by Pen-testers to allow further investigation using grep or other tools like AWK, ACD, DIFF]
                             -oS        _Script Kiddies Output
                                                    
                                   --packet-trace     _you can see the exact packets being sent and received and learn how it really works.                             
```

**cd /usr/share/nmap/scripts ~#**        _contains all default Nmap scripts

#### Filter scripts by use-case
ls | grep ftp
```sh
    nmap -v --script=ftp-anon.nse <target_ip>
    nmap -v --script=ftp-vsftpd-backdoor.nse <target_ip>
```

#### NMAP Script in Python

Another script for Nmap using the above ip list we filtered. Such scripts are mostly used in Ethical Hacking for fast results:
*FAST ONE-LINE Script*
```python
for ip in $(cat iplist.txt) ; do nmap -sS -p 80 -T4 $ip & done
```
(running all ip's through the loop ; Nmap stealth scan, port 80, speed check, and give out IP )


### MOST POPULAR SCANS

**_Network_ Scan**
```sh
nmap -T3 -sP <ip i.e. 192.168.0.0-255 (ip range) OR 192.168.0.0/24 (subent range)>       
```

**_Port_ Scan**   
```sh
nmap -T4 -p <port range i.e. 1-1000 OR single port> <ip address>     
                 (Range b/w  0-65535)
                 -p- (All ports)      
```

**Using _Output_ options**
```sh
nmap -sA -T4 -p 1-1000 <ip i.e. 192.168.0.106> -oN <output file w/ location i.e /root/myfile/scan.txt>
```

**No _Ping_ Scan** - Basically firewall blocks ping requests from nmap so it Bypasses that.
```sh
nmap -T4 <ip> -Pn
```
