# H3 Hello Lab   

## This week, you start building your own hacking lab. You learn hacking by hacking    
# x)    
## Karvinen 2021: Install Debian on Virtualbox – Updated 2024       
-   An installation guide from Tero Karvinen, explaining how to install Debian on a virtual machine to be able to test and use Linux.
-   Takes you through the steps of downloading the correct Debian ISO image as well as setting up a virtual machine, highlighting certain setting configurations to improve the experience and to avoid any potential installation issues.
-   It recommends installing Debian 64-bit, allocating 4GB of ram (or more) and creating 60 GB virtual hard disk, using “expert mode” for the extra configuration options and skipping the “unattended install” option to avoid any unnecessary problems.
-   The installation process starts by using the Debian ISO as a virtual CD-ROM with the virtual box and then booting the live desktop environment which can be used to test hardware functionality (mouse, keyboard, etc.) before going through with the installation.  
-   When using Calamares (the installer), it guides you through the process and recommends certain settings that need to be configured, such as recommending English, selecting your current location and keyboard layout, as well as choosing to erase the entire virtual disk for reliability reasons.
-   Encryption is optional for virtual machines but recommended for real computers.
-   The guide gives recommendations about user setup, giving helpful tips about security practices, suggesting the use of a strong password with at least 9 characters including letters, numbers and special characters and advises against using weak passwords or enabling automatic log in.
-   For any systems experiencing black screen issues after completing the installation, the guide provides troubleshooting solutions.



-   There are essential steps that are to be completed after completing the installation:
-   Updating the package list with the “sudo apt-get update” command
-   Installing the enabling UFW firewall for basic security
-   Rebooting so that all the updates can take effect properly.
-   Installing Virtualbox Guest Additions, which improves user experience by enabling proper screen resolution scaling and allows the user to copy/paste text between the host system and the Debian system and better integration features.  This is done by mounting the Guest Additions CD image and running the installation script through the terminal.
-   There is also a guide provided for users who are using Apple M1 or M2 macs.
-   I think the guide is straightforward, simple to understand and to follow, allowing users to have a fully functional Debian Linux system set up through a virtual machine, allowing the user to test out and experiment with Linux.

## Karvinen 2020: Command Line Basics Revisited
-   A tutorial of the basic command lines that covers the essentials that Linux users should get familiar with and use in the system through the terminal.
-   Basic navigation commands that are necessary for a user to navigate inside the Linux system:     
pwd to show your current location       
ls to list files      
cd to change directories     
-   File manipulation and management:     
nano for text editing    
mkdir for creating directories     
mv for moving or renaming directories            
cp -r for copying         
rm for deleting    
-   Remote access capabilities:    
ssh for secure remote shells    
scp for secure file transfers between systems     

To find files in Linux, you need to remember a few directories in the system which are defined in Filesystem Hierarchy Standard which are identical in all Linux systems    
/ is the root      
/home/ for user files     
/etc/ for system settings      
/media/ for removable devices     
/var/log/ for system logs      

Minimal privilege principle states that we do operations with the lowest level of privileges possible, to run high privilege operations, “sudo” is required.  Commands that affect the whole system require higher privileges, such as installing or removing software and creating users.     

## a)	Can’t fish.
I pinged 1.1.1.1 (Cloudfare DNS service) and google (8.8.8.8) to check whether or not the network connection was functioning properly, and the servers pinged back so this is how we know that I was connected.     
<img width="624" height="239" alt="image" src="https://github.com/user-attachments/assets/80a4cc37-0ce1-45e5-bd5c-ad5aba000537" />     
<img width="624" height="233" alt="image" src="https://github.com/user-attachments/assets/d8ecae24-7d52-4460-9309-78be2b9889b0" />

So I Disabled the network adapter and checked again to verify that I was disconnected, and this was the result.  “Destination Net Unreachable” is confirmation.        
<img width="624" height="147" alt="image" src="https://github.com/user-attachments/assets/110476cd-10f5-44e4-a6a3-5b60bf4ba7db" />     
<img width="975" height="252" alt="image" src="https://github.com/user-attachments/assets/282f574f-2c72-489f-8a62-c82f82454963" />     

 

## b) Local only
Port scanning shows me which networks services or running on my system, each service has its own port number and to scan, I installed and used nmap which is a network scanning tool.
I used the following command in the Linux terminal to install nmap: sudo-apt install nmap             
<img width="624" height="244" alt="image" src="https://github.com/user-attachments/assets/2cc05d80-8571-4984-a377-606255a2d38f" />      


Then to verify I was only scanning my local system, I first checked what my own IP address was using the command: ip addr show           
<img width="624" height="124" alt="image" src="https://github.com/user-attachments/assets/f0f88de7-5ea4-4dde-bf24-2c928fdd4bb6" />

Then    
<img width="975" height="232" alt="image" src="https://github.com/user-attachments/assets/d2651b59-af0d-4066-ad4b-973701988df0" />     

The results shows that:
The system is up and responding with a 0.000175 second latency.      
The scan was carried out on the localhost (127.0.0.1) which is my local machine.      
999 ports were scanned and found to be closed with only 1 port open.      
Port 631/tcp is open and running the IPP (Internet Printing Protocol) service which is a port typically used for managing printers.      
There are no unexpected network services running, and with only 1 port open out of the 1000 scanned, this is good from a security perspective as there are fewer potential entry points that can be used for any attack.      
## c) Daemon scan      
I installed a web server called Apache, using the following command in the terminal: sudo apt-get install apache2       
<img width="624" height="249" alt="image" src="https://github.com/user-attachments/assets/3550b782-433c-4a73-a89b-e4746b54bfba" />     

 
I then checked whether the server application was running properly by using the following command: sudo systemctl status apache2     
<img width="975" height="423" alt="image" src="https://github.com/user-attachments/assets/2ebb120c-43b7-414f-8839-6c7b818a1ff9" />     


 
We can see that it is ‘enabled’.      
I then proceeded to disconnect from the network to ensure that I was only portscanning my own system, and then did another scan.     
<img width="624" height="200" alt="image" src="https://github.com/user-attachments/assets/c8a9f7b0-35a6-4f34-a4df-15a265e65c63" />      


Now we can see that there is an additional port that has been opened, port 80/tcp.        
This is the standard port for HTTP (HyperText Transfer Protocol) which is used to browse the World Wide Web, and this was opened after installing the Apache web server.      
The first scan shows a secure baseline, what a basic and minimal Debian installation looks like, and the second scan shows how installing services can change your “attack surface” and make your system more vulnerable.     

## d) Bandit oh-five    

First I used the terminal to log into the game to complete task 0, using ssh (which I had installed previously).  I did this by using the information that was provided on the website.     
<img width="624" height="278" alt="image" src="https://github.com/user-attachments/assets/1036c3df-910a-472d-ac97-7fc3affdf238" />       

For the 1st level, the goal is to find the password that is found in a readme file.  First I used the ‘ls’ command to check whether there was a readme file in the directory.      
I then used the command: ‘cat readme’ to see the content of the readme file, which showed the password that we needed to complete the level.     
<img width="624" height="173" alt="image" src="https://github.com/user-attachments/assets/d0662b56-ad4b-456d-bd57-36a4ea8d2a67" />    

I then used the password given and ssh to connect to bandit1    
<img width="546" height="306" alt="image" src="https://github.com/user-attachments/assets/c6293410-27c3-4e33-bac3-7619c7eaded4" />     

The next task is to find file (-) stored in a directory, so like before I used the ‘ls’ command to list the directories and to verify that it is there.  
I tried to see the contents by using the ‘cat –‘ command but nothing showed up, but by using the ‘cat ./- ‘ command which successfully showed the content.    
<img width="342" height="149" alt="image" src="https://github.com/user-attachments/assets/749e6443-4188-4d89-953a-e260ca4cc13d" />      

The password shown in the previous level is what I used to log into the next level and continue.     

<img width="624" height="348" alt="image" src="https://github.com/user-attachments/assets/86b0b356-b8c9-4382-8d5c-fc15ab61bf4a" />   


The goal of this task is to find the password that is stored in a file called –spaces in this filename—which is in the home directory.     
For this task I followed a guide (linked in source) as I was stuck trying to find the contents of the directory and after a few attempts finally managed to get the password.    
The first ‘—’ tells cat to stop looking for options, everything after this is a filename.     
<img width="584" height="341" alt="image" src="https://github.com/user-attachments/assets/db138454-2e4b-4f48-b05d-aa99b9ec4eb9" />         

<img width="624" height="342" alt="image" src="https://github.com/user-attachments/assets/adc3abf1-0645-4a42-9a31-cf6d6fe7057c" />       


The task for this level is to access the password that is stored in a hidden directory called ‘inhere’.     
We find this password by using traversal, first we change directory to find the correct one and then list its content.          
<img width="566" height="438" alt="image" src="https://github.com/user-attachments/assets/d73887b7-c6dc-49f7-bd4b-cacf4340491e" />             

I found doing the overthewire:bandit excercises very interesting and quite complicated, but it was a new experience for me and I learned lots of new things about Linux, and will probably continue with the rest of the levels during my free time in the future.

## Sources:
https://mayadevbe.me/posts/overthewire/bandit/level2/
https://www.reddit.com/r/HowToHack/comments/lw5g90/noob_having_constant_permission_denied_error_on/
https://dev.to/xploitcore/detailed-guide-to-mastering-overthewire-bandit-game-1dac











