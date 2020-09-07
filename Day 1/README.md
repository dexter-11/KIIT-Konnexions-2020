# Day 1 [Introduction to Ethical Hacking | Linux Basics | Networking]

## Software Requirments

1. VirtualBox - 6.1.4 [ [Download](https://download.virtualbox.org/virtualbox/6.1.14/VirtualBox-6.1.14-140239-Win.exe) ]
2. Kali Linux 64-Bit - 2020.3 [ [Download](https://cdimage.kali.org/kali-2020.3/kali-linux-2020.3-installer-amd64.iso) | [Torrent](https://images.kali.org/kali-linux-2020.3-installer-amd64.iso.torrent) ]
3. Metasploitable2 [ [Download](https://nchc.dl.sourceforge.net/project/metasploitable/Metasploitable2/metasploitable-linux-2.0.0.zip) ]
4. Burp Suite Community Edition [ [Download](https://portswigger.net/burp/releases/professional-community-2020-9-1) ]

## Hardware Requirements

1. Laptop :)
2. External WiFi Adapter [Should support Monitor mode & Packet Injection] - Only if you wish to do WiFi hacking (Demo will be shown)

## Installation

1. [Youtube Tutorial](https://www.youtube.com/watch?v=zE3EhEJYQ-I) to install Kali Linux in VirtualBox.
https://www.youtube.com/watch?v=yH4plWQ5UbE&ab_channel=OSDock
2. Kali Regular Repo : **`deb http://http.kali.org/kali kali-rolling main non-free contrib`**
3. Make sure your **/etc/apt/sources.list** has the above entry, if it doesn't add it and save the file.
4. After booting up Kali, add yourself to the sudoer's list. Run the command **sudo usermod -a -G $USER root**. Check sudo rights - **sudo -l**
5. From Kali 2020.1 onwards, Kali discarded the default root-user policy. Enable it [Here](https://itsfoss.com/kali-linux-root-user/).
6. Ensure Virtualbox Guest Additions is properly installed [Here](https://www.kali.org/docs/virtualization/install-virtualbox-guest-additions-kali/)
7. Issue with Shared Folder access permissions [Solution](https://innovativebeast.com/shared-folder-permission-denied-issue-in-virtualbox/)

## Resources

1. [Introduction to Ethical Hacking](http://wiki.cas.mcmaster.ca/index.php/Ethical_Hacking)
2. [Basic Kali Linux Commands](https://github.com/dexter-11/Konnexions-2020/blob/master/Day%201/Kali-Linux_Command_List.txt)
3. [Linux essentials for Hackers - Hackersploit](https://hackersploit.org/linux-essentials-for-hackers/)
4. [Nullbyte](https://null-byte.wonderhowto.com/how-to/linux-basics/)
