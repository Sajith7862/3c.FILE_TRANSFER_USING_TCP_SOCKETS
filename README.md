# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
### SERVER:
```
NAME: MOHAMED HAMEEM SAJITH J
REG NO: 212223240090

import socket
s = socket.socket()
port = 60000
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print(f"Connected to {addr}")
    data = conn.recv(1024)
    print(f'Server received: {repr(data)}')

    filename = "C:/Users/admin/Documents/19cs406 computer_networks/testing_file.txt" 
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print(f'Sent: {repr(l)}')
            l = f.read(1024)

    print("Done sending")
    conn.send("Thank you for connecting".encode())
    conn.close()


```
### CLIENT :

```
NAME: MOHAMED HAMEEM SAJITH J
REG NO: 212223240090

import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    print("Receiving data...")
    while True:
        data = s.recv(1024)
        print(f'data={data}')
        if not data:
            break
        f.write(data)
print("Successfully received the file")
s.close()
print("Connection closed")

```
## OUPUT :

### SERVER :

![image](https://github.com/user-attachments/assets/ca393fb5-1451-49ed-b196-07bdfd0e65fe)


### CLIENT :

![image](https://github.com/user-attachments/assets/9432ae9e-c7af-41fc-8c7e-db31bbc21397)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
