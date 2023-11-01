# Fuzz Faster U Fool FFUF
***
```
# minumum required command
ffuf - u http://IP/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt

#To fuzz file extension
ffuf -u http://10.10.131.38/indexFUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/web-extensions.txt

# To specify extensions and filter code fc
ffuf -u http://10.10.131.38/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-words-lowercase.txt -e .php, .txt -fc 403

# Directories and match code -mc
ffuf -u http://10.10.131.38/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-directories-lowercase.txt -mc 200

# In cas and API key is required:
ffuf -d ‘{"key":"key_value"}’ - u http://IP/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt 
```
