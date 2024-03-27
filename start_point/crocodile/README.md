# hack the box (crocodile)

## overview

	lets check what are this vurnarabalities in this machine. in this machine we are checking 
	- Custom Applications
	- Protocols
	- Apache
	- FTP
	- Reconnaissance
	- Web Site Structure Discovery
	- Clear Text Credentials
	- Anonymous/Guest Access


`sudo nmap -sC -sV 10.129.246.250`
```
Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-22 20:58 IST
Nmap scan report for 10.129.246.250
Host is up (0.36s latency).
Not shown: 996 closed ports
PORT      STATE    SERVICE VERSION
21/tcp    open     ftp     vsftpd 3.0.3
80/tcp    open     http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Smash - Bootstrap Business Template
843/tcp   filtered unknown
16018/tcp filtered unknown
Service Info: OS: Unix

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 159.69 seconds


```
after this network scan, let's check the directories in it
`dirb 10.129.246.250`
we got
- /dashboard
- /assets
- /css

there is ftp server also running it we can enter the anonymous user,
we got 

userlist and password lists.

in this we need the admin user, the password is `rKXM59ESxesUFHAd`

we are login to server that gives the flag : c7110277ac44d78b6a9fff2232434d16	

thankyou