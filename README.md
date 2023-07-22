# IronCorp
Here is my Python exploit to explore the SSRF vulnerability in the IronCorp machine on TryHackMe. 

You can read my post about this machine at: https://medium.com/@gutierrematheus/iron-corp-tryhackme-iron-corp-walkthrough-eng-88b0f263275

How to execute: Just open 9001 port using nc and execute the exploit.py. It will do all the necessary validations (validate if you remembered to listen on port 9001 , generate shell.ps1 with your VPN IP that it will get by itself, check which port it can use to open a web server for the target to download shell.ps1, among others.)

My discord: gutierre0x80
