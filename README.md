# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

PROGRAM
Client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
Server
```
import socket
import os

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")

c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    hostname = c.recv(1024).decode('utf-8')
    if not hostname or hostname.lower() == 'exit':
        print("Client disconnected.")
        break

    try:
        # Use system ping command
        response = os.popen(f"ping -n 4 {hostname}").read()  # Use -c 4 for Linux/Mac
        c.send(response.encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

```
## Output
Client


<img width="684" height="99" alt="508557594-a575ab82-0a41-4f19-a443-83f4df548fee" src="https://github.com/user-attachments/assets/3c1aa5b5-0078-406a-b95d-398ad4183969" />

Server

<img width="1343" height="765" alt="508557575-0372e4b4-fcbc-4cdf-910a-55a7a6fd661e" src="https://github.com/user-attachments/assets/595541d8-d836-4304-beb1-d4c694db1863" />


## Result
Thus Execution of Network commands Performed 
