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

## PROGRAM:
Find out the ip address of the attackers system

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/f013e0e5-2b31-4350-8e94-88cd32049e31)


Invoke msfconsole:

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/f079cb1a-2c6b-4175-b142-80b71389a7ae)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/28f1ed04-1b03-4a73-8598-18e239fdef17)


Port Scanning: Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/5ca23776-908f-4133-956b-da9dca54331f)


step4: use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/a74274cd-f6fa-4631-b1df-df16908e329f)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/a0f820d6-3656-4d10-b1a5-73054ec489a5)

Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/0f8b7a3b-5ff8-4e07-9888-474f2bf333e8)


The info command provides information regarding a module or platform,

## OUTPUT:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/1b9914b3-b9a5-4052-8614-443741ead9dd)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION:

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/97ec051f-b3ab-4807-980e-3f0abd824f05)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/6c7a087a-2a87-4220-a101-1203449d47eb)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/8cceab5c-dfce-4976-939b-3260d1e8a25c)

Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/c8bdb739-c290-4812-b884-1cd50e831a2f)

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/8c110344-5eeb-4a65-9f20-f728331dfd50)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![image](https://github.com/NAVEENMATHIVANAN/Metasploit-for-reconnaissance/assets/119394582/a048ba6a-1a49-4253-8f11-183a3f827fb1)

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
