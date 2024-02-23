# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
 while(i<len(l)):
 st+=s
 c.send(str(l[i:st]).encode())
 ack=c.recv(1024).decode()
 if ack:
 print(ack)
 i+=s
```
### server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### client:
![image](https://github.com/ramyanarra07/2b_SLIDING_WINDOW_PROTOCOL/assets/152273259/81490a7e-ffdd-4c7d-9e68-7848ed6bf565)
### server:
![image](https://github.com/ramyanarra07/2b_SLIDING_WINDOW_PROTOCOL/assets/152273259/f659c0ce-4544-48f8-8316-7401211030c5)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
