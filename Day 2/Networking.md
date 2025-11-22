
[Link to ChatGPT Chat](https://chatgpt.com/share/6921f55d-6aa4-8003-bee5-db48d9199727)

# The O.S.I Model:

OSI stands for *Open System Interconnection* and it is a 7 layer model used to explain how data moves across a network. 

## 1º Layer : The Physical Layer:

This layer is responsible for transmitting raw bits through cables, radios, and NIC (network interface cards).

## 2º Layer: The Data Layer:

This layer is responsible for moving frames of data between devices on the same network. It is responsible for handling MAC addresses and uses devices like Switches.

## 3º Layer: The Network Layer:

This layer is responsible for moving packets across different networks. It uses devices like routers with IP routing tables to do so.

## 4º Layer: The Transport Layer:

This layer is responsible for end to end communication between processes.
It uses TCP/UDP protocols and port numbers to do so.

## 5º Layer: The Session Layer:

This layer manages, creates and eds sessions
Think of this as “keeping track of a conversation.”

- Who’s talking to whom
- When to resume a connection
- Managing multiple streams inside the same connection
    
Modern protocols often don't label a specific “session layer protocol,” but behaviors like **TLS session resumption**, **RPC conversations**, or even **WebSocket session handling** fit the vibe.

## 6º Layer: The Presentation Layer:
This is the “make the data readable” step.

- Encryption/decryption
- Compression
- Serialization formats (JSON, XML, protobuf, etc.)
- Character encoding (UTF-8, ASCII)

In reality, these functions get embedded inside application protocols rather than being a separate layer, but the idea is still useful.

## 7º Layer: The Application Layer:
This is basically the part the user or app interacts with.

- HTTP
- DNS
- SMTP
- FTP
- APIs
- Browsers, apps, servers, all sitting right here

This layer is about the rules that app-level software uses to exchange actual information humans care about, not how to transport it.

# **📘 TCP vs UDP**

|Feature|**TCP**|**UDP**|
|---|---|---|
|Reliability|Reliable|Not reliable|
|Order of packets|Guaranteed|Not guaranteed|
|Speed|Slower|Faster|
|Connection|Connection-oriented (3-way handshake)|Connectionless|
|Use cases|Web browsing, emails, file transfer|Gaming, VoIP, video streaming, DNS|

🔑 **Summary**

- **TCP** = “accurate but slower”
- **UDP** = “fast but may lose some packets”