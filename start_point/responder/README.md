# hackthebox (responder)

	this responder has a best vurnarability check is 
	- WinRM
	- Custom Applications
	- Protocols
	- XAMPP
	- SMB
	- Responder
	- PHP
	- Reconnaissance
	- Password Cracking
	- Hash Capture
	- Remote File Inclusion
	- Remote Code Execution

host is : 10.129.157.141
export ip=10.129.157.141

## network scan


## For the host configure in this system is 
```bash
	sudo nano /etc/hosts
```
in, this file configure the host as `10.129.157.141 unika.htb`, let's check the web site for the furture.

	there is a top right cornner, there is option called language changer, en or fr or gm.
for that we can change the page also,
using this exploiting a Local File Include (LFI) vulnerability:

```
http://unika.htb/index.php?page=../../../../../../../windows/system32/drivers/etc/hosts
```
## Responder Challenge Capture
We know that this web page is vulnerable to the file inclusion vulnerability and is being served on a
Windows machine. Thus, there exists a potential for including a file on our attacker workstation. If we select
a protocol like SMB, Windows will try to authenticate to our machine, and we can capture the NetNTLMv2.

## What is NTLM (New Technology Lan Manager)?

NTLM is a collection of authentication protocols created by Microsoft. It is a challenge-response
authentication protocol used to authenticate a client to a resource on an Active Directory domain.
It is a type of single sign-on (SSO) because it allows the user to provide the underlying authentication factor
only once, at login.
The NTLM authentication process is done in the following way :
1. The client sends the user name and domain name to the server.
2. The server generates a random character string, referred to as the challenge.
3. The client encrypts the challenge with the NTLM hash of the user password and sends it back to the
server.
4. The server retrieves the user password (or equivalent).
5. The server uses the hash value retrieved from the security account database to encrypt the challenge
string. The value is then compared to the value received from the client. If the values match, the client
is authenticated.

A more detailed explanation of the working of NTLM authentication can be found here.

## NTLM vs NTHash vs NetNTMLv2
The terminology around NTLM authentication is messy, and even pros misuse it from time to time, so let's
get some key terms defined:

A hash function is a one-way function that takes any amount of data and returns a fixed size value.
Typically, the result is referred to as a hash, digest, or fingerprint. They are used for storing passwords
more securely, as there's no way to convert the hash directly back to the original data (though there
are attacks to attempt to recover passwords from hashes, as we'll see later). So a server can store a
hash of your password, and when you submit your password to the site, it hashes your input, and
compares the result to the hash in the database, and if they match, it knows you supplied the correct
password.

An NTHash is the output of the algorithm used to store passwords on Windows systems in the SAM
database and on domain controllers. An NTHash is often referred to as an NTLM hash or even just an
NTLM, which is very misleading / confusing.

When the NTLM protocol wants to do authentication over the network, it uses a challenge / response
model as described above. A NetNTLMv2 challenge / response is a string specifically formatted to
include the challenge and response. This is often referred to as a NetNTLMv2 hash, but it's not actually
a hash. Still, it is regularly referred to as a hash because we attack it in the same manner. You'll see
NetNTLMv2 objects referred to as NTLMv2, or even confusingly as NTLM.

get the [responder](https://github.com/SpiderLabs/Responder.git). in github.

