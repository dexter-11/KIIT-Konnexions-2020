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
4. Linux essentials for Hackers - [Hackersploit](https://hackersploit.org/linux-essentials-for-hackers/) || [Nullbyte](https://null-byte.wonderhowto.com/how-to/linux-basics/)


# Day 1a [Handy commands and actions]

### Your handy shortcuts!
   *Ctrl+C* Terminates a job/process
   *Ctrl+Shift+C* Copy
   *Ctrl+Shift+V* Paste

### Keep system and applications up-to-date
   **`sudo apt-get update && sudo apt-get upgrade`** OR **`sudo apt update && sudo apt full-upgrade`**    -> Update the kali repositories

   **`sudo apt-get install <application_name>`** -> Install/update git community repositories
