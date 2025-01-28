
# Socket Programming Lab Project

## Overview

This lab project is designed to provide hands-on experience with client-server socket programming. Through the project, you will learn to implement a two-way chat, process a secret code, and perform file transfers using Python's `socketserver` framework. The project is divided into three main parts, each focusing on different aspects of socket communication.

## Instructions

### Part 1: Netcat TCP Chat

In this part, you will use the `netcat` utility to create a two-way chat over a network between two machines: R3 (server) and Kali (client). This part helps you understand the basics of setting up a chat server and client using TCP.

#### Steps:
1. **On R3 (Server):**
   ```bash
   nc -l <port>  # Use a non-reserved port (e.g., 5000)
   ```

2. **On Kali (Client):**
   ```bash
   nc <server IP> <port>
   ```

3. Type messages in each terminal window, and they should be visible in both R3 and Kali's terminals. Modify the chat to include usernames (e.g., "R3" and "KALI") to identify each message's sender.

4. **Commands for personalized chat:**
   - On R3 (Server):
     ```bash
     mawk -W interactive '$0="R3: "$0' | nc -l -p <port_number>
     ```
   - On Kali (Client):
     ```bash
     mawk -W interactive '$0="KALI: "$0' | nc <server IP> <port_number>
     ```

### Part 2: Client-Server with Secret Code

In this part, you will write two Python files: `echo_tcp_server.py` (on R3) and `echo_tcp_client.py` (on Kali). The client will send a string to the server, and the server will process the string. If the string contains the secret code "SECRET", the server will return all digits in the string and their count. If not, the server will return a "Secret code not found" message.

#### Expected Behavior:
- The server will check if the string contains the secret code and return the appropriate response.
- The client will receive the output from the server.

### Part 3: Client-Server with File Transfer

In this part, you will write two Python files: `tcp_file_transfer_server.py` (on R3) and `tcp_file_transfer_client.py` (on Kali). The client will send a file to the server, and the server will write the received data to a new file. The files should match exactly after the transfer.

#### Expected Behavior:
- The client will send a file containing text to the server.
- The server will receive and write the file to its local system.

### Part 4: Questions

1. **In netcat, you specified the port on which the server should listen but did not specify the port the server should use to send a message to the client. Which client port does your netcat server send to? Use Wireshark to answer the question and include a screenshot.**
2. **Briefly explain your code from Part 2 and Part 3. Focus on the TCP communication establishment and flow.**
3. **What does the `socket` system call return?**
4. **What does the `bind` system call return? Who calls `bind` (client/server)?**
5. **Suppose you wanted to send an urgent message from a remote client to a server as fast as possible. Would you use UDP or TCP? Why? (Hint: compare RTTs.)**
6. **What is Nagle’s algorithm? What problem does it aim to solve and how?**
7. **Explain one potential scenario in which delayed ACK could be problematic.**


This lab project offers practical experience in socket programming and network communication. By implementing a simple TCP chat, handling secret code messages, and performing file transfers, you will deepen your understanding of how networked systems communicate. These skills are fundamental in building scalable and reliable network applications, making this project an essential part of your learning in networking and distributed systems.

---
*Feel free to reach out for any clarifications or help during the lab process.*
