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
## OUTPUT:

![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/b0793b25-6210-4594-9ec6-260bfe9bb597)


Invoke msfconsole:

![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/71b72d4e-5861-4d91-a979-9dde9845051b)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/1fd93514-be66-4d9f-8996-9e40a9f16927)



## Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/2682d1af-6c53-4ab1-9c4d-7707627f815e)


step4:  use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/abdec971-7ad0-42aa-bc9a-bfd04718691a)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/39211027-de16-4eb1-b006-079019eb1ebe)


Search is a powerful command in Metasploit that you can use to find what you want to locate.
msf >search name:google type:exploit
The info command provides information regarding a module or platform,

## OUTPUT
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/9dd4d6d4-072b-4a71-ae34-b81e74598c01)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/42272093-edd1-403b-9971-81b7c85aa309)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/edf93893-baae-4f39-9074-603bf47256b3)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/93bfa745-1533-445c-90e5-63fb9cc780e8)

Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/4fe34cd4-2f6a-4c36-a40b-f55732ee4981)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/db008d07-20f2-48af-a23b-5c6364704c9a)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true
![image](https://github.com/M-Nikhil20/Metasploit-for-reconnaissance/assets/118707852/bc3331d1-bd06-4198-9661-c14130cd8260)





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
