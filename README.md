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
<img width="680" height="391" alt="image" src="https://github.com/user-attachments/assets/459ddfc7-2119-4546-bfa2-769fb24803de" />

Invoke msfconsole:
## OUTPUT:
<img width="541" height="476" alt="image" src="https://github.com/user-attachments/assets/0eef847e-0e6b-4176-b7da-0d91977a1c96" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1273" height="511" alt="image" src="https://github.com/user-attachments/assets/f5996298-c9e1-4cb1-9ebf-bc96177292a5" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="1281" height="463" alt="image" src="https://github.com/user-attachments/assets/e04b63c8-8689-4f93-88c5-c917327ee888" />

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
<img width="704" height="75" alt="image" src="https://github.com/user-attachments/assets/00c96197-36d1-485a-9cdc-2bcc403a5144" />

cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
https://github.com/Jeyapriya2810/Metasploit-for-reconnaissance/blob/main/image-7.png


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="732" height="213" alt="image" src="https://github.com/user-attachments/assets/3faafeda-9a56-4c70-ab65-a6de635ec406" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="1260" height="546" alt="image" src="https://github.com/user-attachments/assets/fc1baeb4-31a1-45a9-82dc-aeaa1a6a4e1b" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="776" height="105" alt="image" src="https://github.com/user-attachments/assets/c39df00f-0027-419e-8470-382058d937a7" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="1255" height="520" alt="image" src="https://github.com/user-attachments/assets/ed645b66-b2e5-4f3c-b24d-5d9f227e198b" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="1137" height="244" alt="image" src="https://github.com/user-attachments/assets/ae509d19-c252-4e25-b93e-92451ed8c6ef" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
