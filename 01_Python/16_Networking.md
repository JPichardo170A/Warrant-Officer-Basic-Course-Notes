# 🌐 Networking with Python

*Module 01 — Python | Day 8*

---

## 🎯 Learning Objectives

- Understand socket programming concepts
- Create TCP client and server sockets
- Use `socket.socket()`, `bind()`, `listen()`, `accept()`, `connect()`
- Send and receive data over network connections

---

# Networking Terminology

- **Socket**: "An endpoint for communication."

- **Server**: Generally a service on a remote server waiting to recieve connections.

- **Client**: Depending on the context, it can be either the device or the application (i.e. a web browser) being used to connect to a server.

- **Stream Socket**: Performs like streams of information. There are no record lengths or character boundaries between data, so communicating processes must agree on their own mechanisms for distinguishing information (i.e. connection oriented). Stream sockets are most common because the burden of transferring the data reliably is handled by TCP/IP, rather than by the application.

- **Datagram Socket**: The datagram socket is a connectionless service. Datagrams are sent as independent packets. The service provides no guarantees. Data can be lost or duplicated, and datagrams can arrive out of order. The size of a datagram is limited to the size able to be sent in a single transaction.

- **User Datagram Protocol (UDP)**. Connectionless communication method; sends datagrams.

- **Transmission Control Protocol (TCP)**. Connection oriented communication method; sends a data stream.

## Primary Socket Methods

The table below outlines some of the common methods used when creating sockets with python. This is not an all inclusive list. More information about socket methods can be found at:

[PythonDocs](https://docs.python.org/3.10/library/socket.html)


|Method | Explanation |
|---|---|
| `.accept()` | Accepts a connection. The socket must be bound to an address and listening for connections. The return value is a pair (conn, address) where conn is a new socket object usable to send and receive data on the connection, and address is the address bound to the socket on the other end of the connection.|
|`.bind(address)`| Bind the socket to address. The socket must not already be bound.|
|`.close()`|Mark the socket closed. The remote end will receive no more data (after queued data is flushed).|
|`.connect(address)`|Connect to a remote socket at address.|
|`.listen()`|Enables server to accept connections|
|`.recv(bufsize)`|Receive data from the socket. The return value is a bytes object representing the data received. The maximum amount of data to be received at once is specified by bufsize. This is a synchronous function.|
|`.recvfrom(bufsize)`|Receive data from the socket. The return value is a pair (bytes, address) where bytes is a bytes object representing the data received and address is the address of the socket sending the data. This is a synchronous function.|
|`.send(bytes)`|TCP Method. Sends data to the socket. The socket must be connected to the remote socket.|
|`.sendall(bytes)`|TCP Method. Unlike send(), this method continues to send data from bytes until either all data has been sent or an error occurs. None is returned on success.|
|`.sendto(bytes, address)`|UDP Method. Sends data to the socket. The socket should not be connected to a remote socket, since the destination is specified by address.|
|`socket.socket(family=AF_INET, type=SOCK_STREAM, proto=0, fileno=None)`|The Socket Object. Described in the next section|

## SOCKETS

` socket.socket(family=AF_INET, type=SOCK_STREAM, proto=0, fileno=None) `

1. The address family (`AF_*` constants) indicates the protocol used. AF_UNIX is used for interprocess communication. AF_INET and AF_INET6 for IPv4 and v6, respectively. This parameter loosely corresponds to the link and internet layers. For our course, we will only concern ourselves with IPv4 sockets, the default choice.

2. type (`SOCK_*` constants) indicates whether the socket will be streaming or datagram based (`SOCK_STREAM`, `SOCK_DGRAM`). This parameter loosely corresponds to the transport layer protocol. TCP vs UDP.

3. We will be using the `proto` and `fileno` default values and they can be ignored. `proto` is an option to change to a different protocol family, and `fileno` is a method of feeding in the socket information through a file descriptor.

    Only `SOCK_STREAM` and `SOCK_DGRAM` appear to be generally useful. 

### UDP Sockets

- Example #1
    - This server will NOT stay active after it receives a datagram. It is designed to receive one large chunk of data and then send it back to the sender once. The next example shows how to add persistence to the sever.

```python
# socket() - socket library function that creates a socket object
# .bind() - socket object Method; binds a socket to a socket address (ip address and port)
# recvfrom() - socket object Method; UDP Only; receives data incoming to the socket; optional argument is max data to receive in bytes
# sendto() - socket object Method; UDP only; sends data through a socket to a remote socket address (ip address, port)

import socket
def udp_echo_service():
    
    # set up the socket, and bind it to a port
    s = socket.socket(type=socket.SOCK_DGRAM)
    s.bind(('127.0.0.1',12345))

    # waiting to receive data; a blocking call
    print('receiving...')
    data, address = s.recvfrom(4096)

    # Received something!
    print('received',data,'from',address)

    # Now we echo it back to sender
    s.sendto(data,address)
    print('sent',data)
```

```python
import socket
def udp_echo_client():

    # set up the socket, no need to bind
    s = socket.socket(type=socket.SOCK_DGRAM)

    # Send something to the server
    print('sending...')
    s.sendto(b'Hello World',('127.0.0.1',12345))

    # Waiting to received data; a blocking call
    print('receiving...')
    data,address = s.recvfrom(4096)
    
    # Received something!
    print(data,'received from',address)
```

- Example #2
    - The addition of a `while True` loop keeps the server 'alive.' This allows the function and server to continuously accept data from a user and echo it back.

```python
import socket

def udp_echo_service():
    s = socket.socket(type=socket.SOCK_DGRAM)
    s.bind(('127.0.0.1',12345))
    
    # the loop keeps the service alive
    while True:
        data, address = s.recvfrom(4096)
        print('received',data,'from',address)
        s.sendto(data,address)
```

```python
# .encode() - String method that encodes data according to a specific scheme
# .decode() - String method that decodes data according to a specific scheme


import socket
def udp_echo_client():
    s = socket.socket(type=socket.SOCK_DGRAM)

    # the sendto was changed to prompt the user for input
    # Note the encoding; remember we have to send a bytes object
    
    s.sendto(input("Text to send: ").encode("ascii"),('127.0.0.1',12345))
    data,address = s.recvfrom(4096)
    print(data,'received from',address)
```

### TCP Sockets

TCP - the connection oriented protocol

- Example: Quote of the Day Service

```python
# .listen() - socket object method; TCP Only; enables server to accept connections
# .accept() - socket object method; TCP Only; returns a tuple of client socket and ip address
# .send() - socket object method; TCP Only; sends data to a connected socket; application must ensure that all data is sent
# .close() - socket object method; TCP Only; closes a connected socket

import socket

def tcp_qotd_service():
    s = socket.socket()
    s.bind(('',12345))
    s.listen()
    
    # the loop makes it work continously; i.e. it is now a "service"

    while True:
        client_socket, address = s.accept()
        quote = b'Object oriented programs are offered as alternatives to correct ones.'

        # .sendall() will divide up your message if it is larger than the buffer,
        # it sends until complete
        
        client_socket.sendall(quote)
        client_socket.close()
```

- Note that the server seen above is responsible for terminating or closing the connection with the client socket (seen below)

```python
# .connect() - socket object Method; TCP Only; connects local socket to a remote socket address (ip address, port)
# .recv() - socket object Method; TCP Only; receives data from a connected socket; optional argument is max data to receive in bytes

import socket

def tcp_qotd_client():
    s = socket.socket()
    s.connect(('127.0.0.1',12345))
    msg = bytearray() # <- A bytearray to store the parts of message
    chunk = s.recv(4) # <- Receive the first message piece
    while chunk:
        print(msg) # <- To see the message grow
        msg.extend(chunk) # <- adds to bytearray
        chunk = s.recv(4) # <- receives next chunk of msg
    print(msg) # <- prints the completed message
```

## More with sockets

### Sockets with exceptions

It is important to note that it is NOT mandatory to use error handling/exceptions when building sockets. The code below simply provides an example of how you could implement a `try` and `except` statement when building a UDP server.

```python
import socket

with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as s:
   try:
       s.bind(('127.0.0.1',12345))
       s.settimeout(3)
       data, addr = s.recvfrom(1024)
       print ("received:",addr)
       print ("obtained:", data)
   except socket.timeout :
       print ("No connection!")
```

### Port Scanning with Python

[PythonProgramming.net](https://pythonprogramming.net/python-port-scanner-sockets/) provides an example of a simple port scanning script. It is important to note that port scanning is a form of reconnaissance and when performed without permission can be taken as a form of attack which could land you in legal trouble. **NEVER PERFORM A PORT SCAN UNLESS YOU HAVE WRITTEN EXPLICIT INSTRUCTION FROM THE NETWORK OWNERS TO DO SO**


---

[⬆️ Back to Module Index](../README.md)
