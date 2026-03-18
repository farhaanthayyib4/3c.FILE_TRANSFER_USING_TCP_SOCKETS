# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
PROGRAM
server.py
```
import socket
HOST="0.0.0.0"   
PORT=5001
BUFFER_SIZE=4096
server=socket.socket()
server.bind((HOST, PORT))
server.listen(1)
print("Server listening on port", PORT)
conn, addr=server.accept()
print("Connected from", addr)
filename=conn.recv(BUFFER_SIZE).decode()
print("Receiving file:", filename)
with open("received_" + filename, "wb") as file:
    while True:
        data=conn.recv(BUFFER_SIZE)
        if not data:
            break
        file.write(data)
print("File received successfully.")
conn.close()
server.close()
```
client.py
```

import socket
import os
SERVER_IP="127.0.0.1" 
PORT=5001
BUFFER_SIZE=4096
filename=input("Enter file name to send: ")
if not os.path.exists(filename):
    print("File not found!")
    exit()
client=socket.socket()
client.connect((SERVER_IP, PORT))
client.send(filename.encode())
with open(filename, "rb") as file:
    while True:
        data=file.read(BUFFER_SIZE)
        if not data:
            break
        client.send(data)
print("File sent successfully.")
client.close()
```
## OUPUT
<img width="1055" height="337" alt="image" src="https://github.com/user-attachments/assets/e838368c-2fc3-4a81-812e-65ab61c4a6e0" />
<img width="939" height="419" alt="image" src="https://github.com/user-attachments/assets/2e0ee10e-b46d-4729-a808-862abbc3e2e2" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
