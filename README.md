# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:

### Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.

### Server:
1. Start the program.
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP:

### ARP Client:
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter Logical Address (IP): ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

### ARP Server:
```python
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("ARP Server is listening on port 8000...")
c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    print(f"Received IP: {ip}")
    mac = address.get(ip, "Not Found")
    c.send(mac.encode())
```
## PROGRAM - RARP:

### RARP Client:
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter Logical Address (IP): ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

### RARP Server:
```python
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening on port 8001...")
c, addr = s.accept()

address = {
    "6A:08:AA:C2": "165.165.80.80",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())
```

## OUPUT - ARP:

### CLIENT:

<img width="843" height="286" alt="ARP Client" src="https://github.com/user-attachments/assets/04cc9470-b71e-4ecd-abf0-7672ae8c987b" />

### SERVER:

<img width="838" height="272" alt="ARP server" src="https://github.com/user-attachments/assets/d9993d33-b675-4cc0-a19e-162b8c7aa5c0" />

## OUPUT -RARP:

### CLIENT:

<img width="866" height="282" alt="RARP Client" src="https://github.com/user-attachments/assets/999eeebb-5035-4c36-aa85-08cb755ab92a" />

### SERVER:

<img width="848" height="255" alt="RARP Server" src="https://github.com/user-attachments/assets/b438678a-2715-4548-85e1-0bc55f7c7409" />


## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
