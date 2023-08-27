# List of tools and command

## nmap
Nmap is a utility for network exploration or security auditing. It supports ping scanning, many port scanning techniques, version detection and TCP/IP fingerprinting.

```bash
sudo nmap -sS -A -v -sC $IP_ADDRESS
```

See: https://www.kali.org/tools/nmap/

## gobuster
Gobuster is a tool used to brute-force URIs including directories and files as well as DNS subdomains.

```bash
gobuster dir -u http://$DOMAIN/ -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -k --append-domain
```

```bash
Available Commands:
  completion  Generate the autocompletion script for the specified shell
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode. Replaces the keyword FUZZ in the URL, Headers and the request body
  gcs         Uses gcs bucket enumeration mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  tftp        Uses TFTP enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode (you most probably want to use the IP address as the URL parameter)
```

See: https://www.kali.org/tools/gobuster/

## netstat and ss command
Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships and dump socket statistics on Linux systems.

```bash
netstat -tulpen
```
```bash
ss -lntp
```

See: https://www.kali.org/tools/net-tools/#netstat


## seclists
SecLists is a collection of multiple types of lists used during security assessments. List types include usernames, passwords, URLs, sensitive data grep strings, fuzzing payloads, and many more.

See: https://www.kali.org/tools/seclists/

## chisel
This package contains a fast TCP/UDP tunnel, transported over HTTP, secured via SSH. Single executable including both client and server. Chisel is mainly useful for passing through firewalls, though it can also be used to provide a secure endpoint into your network.

on host:
```bash
chisel server -p $PORT --reverse
```
on server:
```bash
./chisel client $SERVER_IP:$SERVER_PORT R:$FORWARD_PORT:$CLIENT_IP:$CLIENT_PORT R:$CLIENT_PORT2:$CLIENT_IP2:$FORWARD_PORT2
```	
Example:
```bash
./chisel client 10.10.14.199:50505 R:3000:127.0.0.1:3000 R:8001:127.0.0.1:8001
```

See: https://github.com/jpillora/chisel

## Other commands
## ssh tunnel
open ssh tunnel
```bash
ssh -L$PORT:$IP_ADDRESS:$PORT2 $USER@$IP_ADDRESS
```

Example
```bash
ssh -L50505:127.0.0.1:3000 john@only4you.htb
```	

## grep
find ports and its service with grep and hide the errors

```bash
grep -R $PORT /etc 2>/dev/null
```
