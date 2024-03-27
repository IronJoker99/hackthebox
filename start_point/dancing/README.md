# hack the box (dancing pwn)

	lets make the vulnarabiliry check the target

## nmap 
	
```bash
sudo nmap -sC -sV 10.129.17.209 > README.md
```
	Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-15 14:08 IST
Nmap scan report for 10.129.17.209
Host is up (0.33s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE       VERSION
135/tcp open  msrpc         Microsoft Windows RPC
139/tcp open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds?
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: 3h59m59s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-03-15T12:39:18
|_  start_date: N/A

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 46.00 seconds

	there is a smb cliant is running in microsoft-ds

we have to use a smbclient.

$smbclient -L myhost -U DOMAIN/user -W workgroup