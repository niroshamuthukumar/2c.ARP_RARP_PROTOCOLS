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

## server:
```
 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
   ip=input("Enter logical Address : ") 
   s.send(ip.encode()) 
   print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
![alt text](<simulating arp .png>)
## PROGRAM - RARP

## server:
```
 
import socket 
s=socket.socket() 
s.connect(('localhost',8080)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## client:
```
 
import socket 
s=socket.socket() 
s.bind(('localhost',8080)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode()) 
```
## OUPUT -RARP
![alt text](rarp.png)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
