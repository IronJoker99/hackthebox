# hack the box "fawn" ctf challange

```bash
export IP=10.129.210.100
```
	let's make the directory, fawn in that lets check the any ports, vurnabilities etc,.

## Nmap

```bash
sudo nmap -sC -sV 10.129.210.100 intial/nmap
```
> nmap results
```
PORT   STATE SERVICE VERSION                                              │
21/tcp open  ftp     vsftpd 3.0.3                                         │
| ftp-anon: Anonymous FTP login allowed (FTP code 230)                    │
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt        │
| ftp-syst:                                                               │
|   STAT:                                                                 │
| FTP server status:                                                      │
|      Connected to ::ffff:10.10.15.219                                   │
|      Logged in as ftp                                                   │
|      TYPE: ASCII                                                        │
|      No session bandwidth limit                                         │
|      Session timeout in seconds is 300                                  │
|      Control connection is plain text                                   │
|      Data connections will be plain text                                │
|      At session startup, client count was 1                             │
|      vsFTPd 3.0.3 - secure, fast, stable                                │
|_End of status                                                           │
Service Info: OS: Unix
```
## FTP login

```bash
ftp $IP
```
	In the ftp login in anonymous we get the terminal of ftp, we got a flag.txt

```
035db21c881520061c53e0536e44f815
```