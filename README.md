# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
server.py
```
import socket

HOST = "127.0.0.1"
PORT = 8000

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind((HOST, PORT))
server.listen(1)

print("Server is waiting for connection...")

conn, addr = server.accept()
print("Connected with:", addr)

while True:
    data = conn.recv(1024).decode()

    if not data or data.lower() == "exit":
        print("Client disconnected.")
        break

    print("Client >", data)

    message = input("Server > ")
    conn.send(message.encode())

    if message.lower() == "exit":
        break

conn.close()
server.close()
```
client.py
```
import socket

HOST = "127.0.0.1"
PORT = 8000

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect((HOST, PORT))

print("Connected to server. Type 'exit' to quit.")

while True:
    message = input("Client > ")
    client.send(message.encode())

    if message.lower() == "exit":
        break

    data = client.recv(1024).decode()

    if not data:
        break

    print("Server >", data)

client.close()
```
## OUPUT
<img width="1049" height="328" alt="image" src="https://github.com/user-attachments/assets/f79f9648-9be5-4ea1-9b84-e47b47512a7f" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
