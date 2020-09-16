# Day 3-4 [Scanning and Enumeration]

### Setting up NAT Network in Virtual Box (Optional)
```sh
VBoxManage natnetwork add --netname Konnexions --network "10.20.14.0/24" --enable
VBoxManage dhcpserver add --netname Konnexions --ip 10.20.14.3 --netmask 255.255.255.0 --lowerip 10.20.14.200 --upperip 10.20.14.250 --enable
```

## SCANNING

### What Is Scanning?

Scanning is a process that involves engaging and probing a target network with the intent
of revealing useful information and then using that information for later phases of the
pen test. Armed with a knowledge of network fundamentals, a scanner, and the results of
a thorough footprinting, it is possible to get a decent picture of a target.

### Types of Scans 

1. Port Scanning
2. Network Scanning
3. Vulnerability Scanning 

### Flags in TCP

1. **SYN** : Initiates a connection between two hosts to facilitate communication.
2. **ACK** : Acknowledges the receipt of a packet of information.
3. **URG** : Indicates that the data contained in the packet is urgent and should be processed immediately.
4. **PSH** : Instructs the sending system to send all buffered data immediately.
5. **FIN** : Tells the remote system that no more information will be sent. In essence, this gracefully closes a connection.
6. **RST** : Resets a connection.

### The Family Tree of Scans

1. **Full Open Scan** : Completes 3 way handshake. (DETECTABLE) (-sT)
2. **Half Open Scan** (SYN Scan) : Instead of the final ACK packet, RST is send by source. (LESS NOISY) (-sS)
3. **XMAS Tree Scan**: a single packet is sent to the client with URG, PSH, and FIN all set to on. (DETECTABLE) (-sX)
4. **FIN Scan** :  Sends a FIN packet. Goes undetected through firewalls. (UNDETECTED) (-sF)
5. **Null Scan** : No flags set, thus easily detected by firewalls and IDS. (-sN)
6. **Idle Scan** : Spoofs source ip to scan victim. (Completely Undetected) (-sI <spoof> <target>)
7. **ACK Scan** : To detect Firewalls (-sA). If firewall fragment packet with -f flag in  nmap.
8. **UDP Scan** : To scan for UPD Ports/Services (-sU)

### OS Fingerprinting

OS Fingerprinting attempt to identify systems a bit better. Behind those open and closed ports is an operating system, to confirm the nature of the operating system OS Fingerprinting is performed. There are 2 types of OS Fingerprinting :
1. **Active** : The attacker sends specially crafted packets to gain info about the OS (DETECTABLE). (-O)
2. **Passive** : The attacker sniffs packets from the network.(UNDETECTED)

### Banner Grabbing

Banner grabbing is designed to determine information about the services running on a
system and is extremely useful to ethical hackers during their assessment process.
Typically, the technique is undertaken using Telnet to retrieve banner information about
the target that reveals the nature of the service.

### Vulnerability Scanning

1. Searchsploit
2. Nesus
3. OpenVas

### Idle Scan Hands On

1. Nmap Version :
```sh
nmap -P0 -p <port> -sI <zombie IP> <target IP>
```
2. HPing3: 
```sh
hping3 -S <zombie> 
hping3 --spoof <zombie> -S <target> -p <port> -c 1
hping3 -S <zombie>
```

### Further Reading

1. [NMAP by Konnexions](https://github.com/dexter-11/Konnexions-2020/edit/master/Day%203-4/Nmap.md)
2. [NMAP Official Guide](https://nmap.org/book/man.html)

## ENUMERATION

### What is Enumeration ?

Enumeration is defined as a process which establishes an active connection to the target hosts to discover potential attack vectors in the system, and the same can be used for further exploitation of the system.

Enumeration is used to gather the below

1. Usernames, Group names
2. Hostnames
3. Network shares and services
4. IP tables and routing tables
5. Service settings and Audit configurations
6. Application and banners
7. SNMP and DNS Details

### Common Tools For Enumeration

1. nbtstat **[windows enumeration]**
2. enum4linux **[linux enumeration]**

### Further Reading

1. [Enumeration](https://resources.infosecinstitute.com/what-is-enumeration/)

