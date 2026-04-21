# APC_base-Process-Injection-Tool

> [!CAUTION]
> **This tool is for educational purposes only. Read the [DISCLAIMER](DISCLAIMER.md) before use.**

### 💡 What is this? (In simple words)
This tool is a way to "sneak" a small piece of code into another program that is already running (like NotePad). Instead of opening a brand new window or starting a new task (which Anti-Virus usually blocks), this tool "hijacks" a task the program was already doing and adds its own code to the end of the list. It's a key technique used to understand how malware stays hidden in regular apps!

---

This tool is a Process Injection Tool ( 32-bit ) using the APC technique where instead of creating new Threads ( which are more likely to be flagged by EDR and AVs ) , it Hijacks existing thread and Inject the code in its queue..... It is not applicable for 64-bit architectured windows as Irvine32 Library is used in it as it is for 32-bit architecture and if I want to make it 64-bit than Irvine64 will be used and whole code has to be changed as 64-bit architecture has registers RAX,RBX,RCX etc. unlike 32-bit architectured windows that has EAX,EAB,ECX etc. registers 

This project was made just for educational purpose to demonstrate working of APC ( Asynchronous Procedure Call ) attack as it is stealthier than simple Process inejction ... In my project , to evade signature obfuscation , i have implemented XOR encryption with the malware file so that its signature gets changes and it become able to bypass static analysis of AntiViruses and EDRs . My tool uses 2 modes (simple malware injection , encrypted malware injection ) . 

### 🔥 New UPDATES :
1) **Auto Process Discovery**: u don't have to find PID in task manager anymore ... just type the process name (like notepad.exe) and the tool will find it for u automatically.
2) **Architecture Safety Check**: added a check to see if the program u are injecting in is 64-bit ... if it is 64-bit than it will stop and tell u instead of crashing the program because this tool is 32-bit and it won't work with 64-bit stuff.

STEPS TO USE IT :

1) First of all install VISUAL STUDIO IDE in your computer. It can be downloaded from https://visualstudio.microsoft.com/
2) Download Irvine32 library from github repo https://github.com/Eazybright/Irvine32
3) Configure Visual studio for your project and configure Irvine32 library 
4) Now U can take a look to this youtube video for configuring Irvine32 library : https://youtu.be/4XH_iEehGZ0?si=KEcz2RCsm3Av1cKk
5) After completing all that stuff , get this code and paste it in your project .
6) As this encryption tool is separate tool and injection tool is separate so u have to create separate projects in visual studio .
7) Now Copy-Paste these codes in your project files in visual studio and compile and start injection ...

NOTE : This is online compatible to 32-bit windows . If you tried to inject code to 64-bit windows via this tool , it will likely crash your Program in which you have injected. ( **Update**: the tool now checks this itself so it won't crash stuff anymore ! )

To make your project work successfully , some points you have to keep in mind :
1) Every time you reboot your system , its APIs memory addresses changes so if you reboot your system and tried to inject previous code , your code may not work properly or it probably crashes the program.....
2) This project fetches the process running in background at that specific time , If you started injection and opened the target application after , then  injection may not work because it haven't captured the process in which you are trying to inject....
3) Even tho I added safety checks , try to inject the malware in 32-bit programs only like old notepad or 32-bit apps , it works best that way .......
