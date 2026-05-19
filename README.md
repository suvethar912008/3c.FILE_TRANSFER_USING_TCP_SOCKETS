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
```
## Server:
import socket

def start_server():
    host = '127.0.0.1'
    port = 6000

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)
    print(f"Server listening on {host}:{port}")

    conn, addr = server_socket.accept()
    print(f"Connected by {addr}")

    filename = "received_file.txt"
    with open(filename, "wb") as f:
        while True:
            data = conn.recv(1024)
            if not data:
                break
            f.write(data)

    print(f"File saved as {filename}")
    conn.close()
    server_socket.close()

if __name__ == "__main__":
    start_server()
## Client:

import socket

def send_file():
    host = '127.0.0.1'
    port = 6000

    # Create a small test file automatically
    with open("sample.txt", "w") as f:
        f.write("Hello, this is a test file.\nLine 2 of the file.\n")

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    with open("sample.txt", "rb") as f:
        data = f.read(1024)
        while data:
            client_socket.send(data)
            data = f.read(1024)

    print("File sent successfully.")
    client_socket.close()

if __name__ == "__main__":
    send_file()
```



## OUPUT

Server:

<img width="485" height="150" alt="image" src="https://github.com/user-attachments/assets/67d4cd44-737c-4a9d-97b5-04e4a42631bb" />

Client:

<img width="342" height="71" alt="image" src="https://github.com/user-attachments/assets/ae5e38a3-96b7-485a-bf2c-d1a96d845981" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
