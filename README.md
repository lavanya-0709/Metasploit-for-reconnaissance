# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="821" height="432" alt="image" src="https://github.com/user-attachments/assets/a4d64116-9f0d-4214-a986-93d92f17f2b3" />



Invoke msfconsole:
## OUTPUT:
<img width="742" height="770" alt="image" src="https://github.com/user-attachments/assets/f6005918-6164-4da3-ab3c-fe94a021819c" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="836" height="833" alt="image" src="https://github.com/user-attachments/assets/ca70f06b-4081-4f28-84da-a404c100eb44" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="916" height="873" alt="image" src="https://github.com/user-attachments/assets/c32d12f9-eb46-4a4c-8c92-22c60fb9b851" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="644" height="368" alt="image" src="https://github.com/user-attachments/assets/7c528149-eae0-45c7-8536-6c08e81e305d" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="747" height="455" alt="image" src="https://github.com/user-attachments/assets/41b0f2e1-ee5e-401d-a9da-10d88e999540" />




Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="903" height="909" alt="image" src="https://github.com/user-attachments/assets/85c01bc2-47a7-4aa0-bddb-19ef6b124020" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="863" height="872" alt="image" src="https://github.com/user-attachments/assets/a3d07f99-d48b-4ed7-ac22-5374122db4a6" />



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="702" height="405" alt="image" src="https://github.com/user-attachments/assets/9cb3df37-69e0-4e1a-bad3-35f62626340f" />
<img width="851" height="738" alt="image" src="https://github.com/user-attachments/assets/9cb30078-e817-4899-949a-4ccbc6ec63b4" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="846" height="808" alt="image" src="https://github.com/user-attachments/assets/014ecf55-e480-4d33-bd91-06839b205623" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="921" height="879" alt="image" src="https://github.com/user-attachments/assets/29b79d28-4a65-4e2e-9f8d-7f88ff4a4a15" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="831" height="208" alt="image" src="https://github.com/user-attachments/assets/bf4b7073-9db7-4ce9-bb6e-23fa914cf405" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
