# setup
* * *
- To check if ssh service is running
```
service --status-all | grep -i ssh
```

## Steps
### <span style="color: #7f7fff">Remote host</span>
- You need OpenSSH Server
```
apt-get update
apt install openssh-server
systemctl enable ssh
systemctl start ssh
systemctl status ssh
nano /etc/ssh/sshd_config
	Port 2020
	PubkeyAuthentication yes
	AuthorizedKeysFile      .ssh/authorized_keys
	PasswordAuthentication no
	PermitRootLogin no
systemctl restart sshd
```

### <span style="color: #7f7f00">Local host</span>
- You need OpenSSH Client
- Generate the key pairs
```
ssh-keygen -t rsa -b 4096
# /home/mj/.ssh/rsa_homeServer
# because I changed the default name of the keys, I have to use -i
ssh-copy-id -p 2020 -i rsa_homeServer remote@serverIP

# connect
ssh -p 2020 -i ~/.ssh/rsa_homeServer remote@serverIP
```
- if you want to use the config file
```
# my server at home
Host server
        HostName 192.168.178.29
        Port 2020
        user msbit
        IdentityFile /home/mj/.ssh/rsa_homeServer
        StrictHostKeyChecking no
        UserKnownHostsFile /dev/null

```
