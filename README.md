# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
## Server.py:
```python
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server waiting for connection...")
c, addr = s.accept()
print("Connected to", addr)
data = c.recv(4096)
with open("received.txt", "wb") as f:
    f.write(data)
print("File received successfully")
file = open("received.txt", "rb")
c.send(file.read())
file.close()
c.close()
s.close()
```

## Client.py:
```python
import socket
s = socket.socket()
s.connect(('localhost', 8000))
file = open("example.txt", "rb")
data = file.read()
s.send(data)
file.close()
received = s.recv(4096)
with open("downloaded.txt", "wb") as f:
    f.write(received)
print("File uploaded and downloaded successfully")
s.close()
```
## OUTPUT

## Server:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0207533a-2c8e-454e-a1b2-0b5ed2b5c989" />


## Client:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7f52f72f-92e0-4c9f-9a22-27011fb7f160" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
