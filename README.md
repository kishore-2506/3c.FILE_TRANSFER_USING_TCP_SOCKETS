
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

## CLIENT
```
import socket
s=socket.socket()
host=socket.gethostname()
port=60000
s.connect((host,port))
s.send("Hello server!".encode())
with open('received_file','wb')as f:
  print('receiving data....')
  while True:
    data=s.recv(1024)
    print('data=%s',data)
    if not data:
       break
    f.write(data)
print('Successfully received the file')
s.close()
print('connection closed')
```
## SERVER
```
import socket
port=60000
s=socket.socket()
host=socket.gethostname()
s.bind((host,port))
s.listen(5)
print("Server listening on port",port)
while True:
  conn,addr=s.accept()
  print("Connected to",addr)
  data=conn.recv(1024)
  print('Server received',repr(data))
  filename = r'C:\Users\admin\Desktop\CN\assignment.txt'
  with open(filename,'rb') as f:
   l=f.read(1024)
   while l:
     conn.send(l)
     print('sent',repr(l))
     l=f.read(1024)
print("Done sending")
conn.send('Thank you for connecting'.encode())
conn.close()
```
## OUPUT


## CLIENT
![Screenshot 2024-10-17 153803](https://github.com/user-attachments/assets/31ad428f-6599-4a14-9f82-67713a12f5bb)

## SERVER
![Screenshot 2024-10-17 153831](https://github.com/user-attachments/assets/a9a15377-0e34-47a0-8ad1-8bb0c82c88fd)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
