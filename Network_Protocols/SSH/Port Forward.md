# Port Forward
* * *

## <span style="color: #41de7f">Local Port Forwarding</span>
### Tester Machine (Local)
- when you make a request on Tester machine to port testerPort, the request will be forwarded to server on port servicePort
```
ssh -L <testerPort>:<serviceIP>:servicePort user@serverIP
```
#### Example
- Server running internal web service on
	- IP: 127.0.0.1
	- Port <span style="color: #ff7f7f">80</span>
- Tester
	- Port <span style="color: #7fd57f">8080</span>
- execute:
```sh
ssh -L 8080:127.0.0.1:80 user@192.168.100.100 -N -f
	# -N disable execution of a remote command
	# -f ssh goes to background
```
- on Tester machine's browser
```
http://localhost:8080 # request will be forwarded to 10.0.0.1:80 on server
```



## <span style="color: #7f7fe9">Remote Port Forwarding</span>

### Tester Machine (remote)
- When server makes a request to serverPort, the request will be forwarded to Tester machine on testerPort
```sh
ssh -R serverPort:testerIP:testerPort user@serverIP
```

#### Example
- Server
	- IP: 10.0.0.1
	- Port: <span style="color: #ff7f7f">80</span>
- Tester
	- IP 192.168.0.111
	- Port: <span style="color: #7fd57f">8080</span>
- Execute the following command on Tester machine
```sh
ssh -R 80:192.168.0.11:8080 user@10.0.0.1 -N -f
	# -N disable execution of a remote command
	# -f ssh goes to background
```
