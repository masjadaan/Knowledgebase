# setup
* * *
- To check if ssh service is running
```
service --status-all | grep -i ssh
```

## Steps
### Remote Host
- You need OpenSSH Server
```
apt-get update
apt install openssh-server
systemctl enable ssh
systemctl start ssh
systemctl status ssh
nano /etc/ssh/sshd_config
	Port PortNr
	PubkeyAuthentication yes
	AuthorizedKeysFile      .ssh/authorized_keys
	PasswordAuthentication no
	PermitRootLogin no
systemctl restart sshd
```

### Local Host
- You need OpenSSH Client
- Generate the key pairs
```
ssh-keygen -t rsa -b 4096
# use -i to specify the location of private key
ssh-copy-id -p PortNr -i /path/to/privateKey remote@serverIP

# connect
ssh -p PortNr -i ~/.ssh/path/to/privateKey remote@serverIP
```
- if you want to use the config file
```
# Specify a remote server
Host server
        HostName ServerIP
        Port PortNr
        user userName
        IdentityFile ~/.ssh/path/to/privateKey
        StrictHostKeyChecking no
        UserKnownHostsFile /dev/null

```
