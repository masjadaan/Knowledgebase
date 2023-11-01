# GoBuster
***

## Installation
```
sudo apt install gobuster
```

## Usage
### Dir Mode
```
# Dirbuster has a "dir" mode that allows the user to enumerate website directories
gobuster dir -u http://IP -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x.html
  # -x	File extension(s) to search for
  # -P Password for Basic Auth
  # -U Username for Basic Auth
  # -k Skip TLS certificate verification
```

### DNS Mode
```
# This allows Gobuster to brute-force subdomains.
gobuster dns -d http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

### Vhost Mode
```
# This allows Gobuster to brute-force virtual hosts.
   ◇ gobuster vhost -u http://webenum.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```
