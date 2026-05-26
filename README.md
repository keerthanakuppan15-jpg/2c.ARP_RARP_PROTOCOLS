# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
**CLIENT**
```
#Developed by:KEERTHANA K
#Reg no: 212225230137
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True:
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
** Server**

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
     ip=input("Enter logical Address : ") 
     s.send(ip.encode()) 
     print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1821" height="848" alt="image" src="https://github.com/user-attachments/assets/a28db889-d6a5-4bbf-94d1-da6d1a5b8f7a" />
<img width="1619" height="560" alt="image" src="https://github.com/user-attachments/assets/367a3f67-7481-4ae4-9b19-3fe2670c81fc" />

## PROGRAM - RARP
```
**Client**

import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
  c.send(address[ip].encode())
 except KeyError:
  c.send("Not Found".encode())

**Server**

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
<img width="949" height="713" alt="image" src="https://github.com/user-attachments/assets/77b65d36-0ef6-4398-8ebb-abac9bd6b239" />
<img width="891" height="715" alt="image" src="https://github.com/user-attachments/assets/85484658-3d24-4da5-9a1c-1fbcda103600" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
