<h1 align="center">Summary Diagram</h1>


<p align="center">
<br/>
<img width="950" alt="Portfolio" src="https://i.imgur.com/MYms91r.png">
<br />
</p>


<br />
<br />

<h1 align="center">Project walk-through</h1>

<br />
<br />

---
<a name="toc"></a>
**Table of Contents:**

- [Preparation](#preparation)
- [Ubuntu VM Setup](#ubuntu-vm-setup)
- [Windows VM Setup](#windows-vm-setup)
- [Configuring Windows Firewall](#configuring-windows-firewall)
- [Testing Connectivity](#testing-connectivity)
- [Installing Necessary Software](#installing-necessary-software)
- [Capturing Telnet Traffic](#capturing-telnet-traffic)


---

<h4>Tip: Any configuration options not mentioned in the walkthrough can be left at their default settings</h4>

---

[back to top](#toc)
## Preparation

<br />
<br />

 - Files to Prepare:
    - Oracle Virtual Box installed
    - Ubuntu disk file
    - Windows 10 or 11 disk file
    - Putty (portable version for Telnet, SSH) *(You will download during this tutorial(*
    - WireShark *(You will download during this tutorial(*

<br />
<br />



 - Open Virtual Box, click [New]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/n3chgsF.png">
<br />
<br />
<br />
<br />



 - Name the VM "Ubuntu" Pick Ubuntu ISO image, check [Skip Unattended Installation]. Click [Next]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/EnqTEcG.png">
<br />
<br />
<br />
<br />



 - Leave the processor & RAM setting as default. Click [Finish]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/Jp9b5Ay.png">
<br />
<br />
<br />
<br />

 - Go to VM setting, enable the second adapter and attach to "Internal Network"
 - Click [OK] and run the VM.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/zR2PTcp.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Ubuntu VM Setup

<br />
<br />

 - Pick [Try or Install Ubuntu] and hit ENTER.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/1uwpjm9.png">
<br />
<br />
<br />
<br />

 - Pick English, click [Install Ubuntu]

<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/NeYGKfz.png">
<br />
<br />
<br />
<br />


 - Set keyboard layout as [English(US)]. Click [Continue]

<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/CmRUbWv.png">
<br />
<br />
<br />
<br />

 - Uncheck [Download updates while installing Ubuntu] for minimum installation.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/XoNpeaT.png">
<br />
<br />
<br />
<br />

 - Pick [Erase disk and install Ubuntu]
Start Installing.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/vJnVHHY.png">
<br />
<br />
<br />
<br />

 - When asked about your geographical location, pick default and click [Continue]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/VKbGOJR.png">
<br />
<br />
<br />
<br />


 - Set up your user account. In this lab:
(username: soel, password: Password123)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/GdjXIJj.png">
<br />
<br />
<br />
<br />

 - Once the OS installation is complete, open up a terminal. *Note: We're skipping the* `sudo apt upgrade` *command for this lab.*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/B6neekT.png">
<br />
<br />
<br />
<br />

 - Go to Network Setting. The first adapter shows that this VM is NATed from our home router. Press the gear wheel icon on the second adapter, our internal network.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/M0Bsn4R.png">
<br />
<br />
<br />
<br />

 - Assign an IP address to our VM. Go to [IPv4] and select [IPv4 Method] as [Manual]. Assign IP address 192.168.50.100 with subnet mask 255.255.255.0.
 - Leave the DNS and Gateway blank. Click [Apply]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/hA81PLt.png">
<br />
<br />
<br />
<br />


 - Use the `ip a` command to check if the IP address is correctly assigned.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/8FSU6tW.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Windows VM Setup

<br />
<br />


 - Go to Virtual Box, click [New]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/MvLByj4.png">
<br />
<br />
<br />
<br />


 - Name this VM "Windows-10". Pick Windows ISO image, check [Skip Unattended Installation]. Click [Next]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/aphEO10.png">
<br />
<br />
<br />
<br />

 - Leave the processor & RAM setting as default. Click [Finish]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/KfnyUNK.png">
<br />
<br />
<br />
<br />


 - Go to VM setting, on the [General] tab, choose [Bidirectional] for both [Shared Clipboard] and [Drag'n'Drop]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/sxuRpYk.png">
<br />
<br />
<br />
<br />

 - Add the second adapter for our internal network.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/jy4JU6h.png">
<br />
<br />
<br />
<br />



 - Run the VM and start the installation.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/MD42kWn.png">
<br />
<br />
<br />
<br />



 - Make sure to pick [Windows 10 Pro] instead of [Windows 10 Home]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/1DkxSvo.png">
<br />
<br />
<br />
<br />

 - Pick Custom: Install Windows only - this means formatting the hard drive and installing from scratch.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/oPNAwxa.png">
<br />
<br />
<br />
<br />

 - Click [Offline Account] to avoid signing in. Skip all the extra feature offers.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ivT1HFD.png">
<br />
<br />
<br />
<br />


 - Set up the name of your User Account (in this lab, Soel_Lab)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/YIHmgx4.png">
<br />
<br />
<br />
<br />



 - Set up the password (in this lab, Password123)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ZfkUOib.png">
<br />
<br />
<br />
<br />


 - Once the OS installation is finished, click [Device] - [Insert Guest Additions CD image]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/YlFtIAa.png">
<br />
<br />
<br />
<br />


 - Double click your optical drive.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/9sk7v6N.png">
<br />
<br />
<br />
<br />


 - Click [VBoxWindowsAdditions-amd64] and proceed installation with default settings. Reboot your VM manually after installation.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/vfGEH35.png">
<br />
<br />
<br />
<br />


 - Go to network connection setting. Configure the second network adapter for our VM internal network.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/O8pctjU.png">
<br />
<br />
<br />
<br />


 - Click [Internet Protocol Version 4(TCP/IPv4)] - [Properties]. Set IP address: 192.168.50.50, subnetmask: 255.255.255.0
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/45a4lbE.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Configuring Windows Firewall

<br />
<br />

 - Shut down the firewall so our Ubuntu machine can ping the Windows 10 machine.
     - *(Note: This is only for lab environments, not for corporate settings!)*
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/LppYNpX.png">
<br />
<br />
<br />
<br />



 - Click [Windows Defender Firewall Properties] - [Public Profile]. Pick [Off] for [Firewall state]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/vZU9uKL.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Testing Connectivity

 - Go to Ubuntu machine and check if we can ping the Windows VM.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/EdluQDm.png">
<br />
<br />
<br />
<br />


 - Go to Command Prompt from the Windows machine, check if we can ping our Ubuntu machine.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/ann50dB.png">
<br />
<br />
<br />
<br />


---

[back to top](#toc)
## Installing Necessary Software

<br />
<br />

 - Download Wireshark Windows x64 Installer from the Wireshark webpage.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/k7UHXEu.png">
<br />
<br />
<br />
<br />


 - Go to putty.org, and click [Download PuTTy]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/6H99otN.png">
<br />
<br />
<br />
<br />

 - Use the portable version that does not require installation.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/kbPAjhm.png">
<br />
<br />
<br />
<br />



 - Install Wireshark with default setting.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/10dnLzY.png">
<br />
<br />
<br />
<br />



 - Install Telnet on Ubuntu VM using the command `sudo apt install telnetd`
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/WZMZo9t.png">
<br />
<br />
<br />
<br />


 - Verify Telnet installation with the command `sudo dpkg -l |grep telnetd`
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/0IZ753Q.png">
<br />
<br />
<br />
<br />

---

[back to top](#toc)
## Capturing Telnet Traffic

<br />
<br />


 - Open Wireshark in Windows 10 VM. Select our internal network (Ethernet 2)
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/8NfxLM9.png">
<br />
<br />
<br />
<br />


 - Open Putty.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/rsBH4dG.png">
<br />
<br />
<br />
<br />



 - Enter our Ubuntu VM IP address. Select [Telnet] for [Connection Type]. Click [Open]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/sa7Tnso.png">
<br />
<br />
<br />
<br />


 - As soon as we attempt to connect to Ubuntu VM, you will see Telnet traffic from Wireshark.
 - Enter the Ubuntu VM user ID and Password. Press Enter.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/gFL4JP1.png">
<br />
<br />
<br />
<br />

 - Check if the connection is successful with `whoami` command. We can see the Ubuntu VM username.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/5SsnhII.png">
<br />
<br />
<br />
<br />


 - Stop capturing the traffic.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/txzlh0A.png">
<br />
<br />
<br />
<br />


 - Try filtering with [telnet]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/pJQsItc.png">
<br />
<br />
<br />
<br />

 - Right-click any event. Click [Follow] - [TCP stream]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/C6yPRGE.png">
<br />
<br />
<br />
<br />


 - We can see all the plain text communication between the Windows VM and the Ubuntu VM. We can see the login ID [soel] and the password [Password123]
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/tj4fP5z.png">
<br />
<br />
<br />
<br />


 - We can even see the [whoami] command we used to check the connection status.
<p align="center">
<br/>
<img width="597" alt="Portfolio" src="https://i.imgur.com/M2spuly.png">
<br />
<br />
<br />
<br />

**Conclusion: Telnet is insecure due to its plain text communication. Threat actors can easily sniff the packets and retrieve all the communication!**

<br />
<br />

\<end\>

[back to top](#toc)

<br />
<br />
<br />

