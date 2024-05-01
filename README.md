# 4.Execution_of_NetworkCommands:
#### NAME: ESWANTH KUMAR K
#### REGISTER NO: 212223040046

## AIM :Use of Network commands in Real Time environment:
## Software : Command Prompt And Network Protocol Analyzer:
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

## PROGRAM:
## CLIENT:
```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
## SERVER;
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
## TRACEROUTE COMMAND:
```
from scapy.all import* 
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```

## Output:
## CLIENT:
![Screenshot (28)](https://github.com/eswanth2005/4.Execution_of_NetworkCommends/assets/164656722/67a332b0-acdf-4455-983b-58d1e6628ee2)

## SERVER:
![Screenshot (27)](https://github.com/eswanth2005/4.Execution_of_NetworkCommends/assets/164656722/bfb70911-a1a7-47ea-9e3c-c616bfe1a749)

## TRACEROUTE COMMAMD:
![image](https://github.com/eswanth2005/4.Execution_of_NetworkCommends/assets/164656722/6d12fea7-1741-47b5-9cd6-dc72c8a1b23b)

## Result:
Thus Execution of Network commands Performed.
