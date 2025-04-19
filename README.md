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
client:
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
server:
```
import socket
s = socket.socket()
s.connect(('localhost', 8000)) 
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT
![Screenshot 2025-04-19 075657](https://github.com/user-attachments/assets/b4c94066-766e-4278-a254-ddbb1a57baa2)
![Screenshot 2025-04-19 075714](https://github.com/user-attachments/assets/5551bea2-4438-4835-8865-8fa9f8cc4710)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
