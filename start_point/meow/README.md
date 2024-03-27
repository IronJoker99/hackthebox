# hack the box meao walkthrough

	In the hack the box we are going to check the vernability and port scans

export IP=10.129.151.232

	Lets make nmap scan to check the port

```bash
nmap -sC -sV 10.129.151.232
```
there are one open open port is there it is a tcp/telnet

lets connect the telnet using command with username
```bash
telnet 10.129.151.232
```
it shows a password we dont know the password
	lests try with root.
```bash
telnet 10.129.151.232 -l root
```
it give the terminal.
there is flag text file
 		b40abdfe23665f766f9c61ecba8a4c19