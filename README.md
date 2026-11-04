# 2a_Stop_and_Wait_Protocol

## AIM 
To write a python program to perform stop and wait protocol

## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program

## PROGRAM
**sender.py**
~~~
import socket

s = socket.socket()
s.connect(('localhost', 8000))

data = ["Frame 1", "Frame 2", "Frame 3", "Frame 4"]

for frame in data:
    print("Sending:", frame)
    s.send(frame.encode())

    ack = s.recv(1024).decode()
    print("Acknowledgement received:", ack)

s.close()
~~~

**receiver.py**
~~~
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Receiver is waiting...")
c, addr = s.accept()

while True:
    data = c.recv(1024).decode()

    if not data:
        break

    print("Received:", data)

    ack = "ACK"
    c.send(ack.encode())
    print("Acknowledgement sent:", ack)

c.close()
s.close()
~~~

## OUTPUT

<img width="812" height="226" alt="image" src="https://github.com/user-attachments/assets/604c07d3-810d-4e2d-a599-bec517cf8cb5" />

<img width="826" height="262" alt="image" src="https://github.com/user-attachments/assets/c2946506-8f3e-406b-afc8-8785f6af7c62" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
