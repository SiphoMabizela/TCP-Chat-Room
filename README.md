# Python Socket Chat Application

## Overview

This project is a simple real-time chat application built using Python's `socket` and `threading` libraries. It demonstrates how multiple clients can connect to a central server and exchange messages instantly over a local network using TCP sockets.

The application consists of a **server** that manages connections and message distribution, and a **client** that allows users to join the chat and communicate in real time.

---

## Features

- Multiple clients can connect to the server simultaneously
- Real-time message broadcasting to all connected users
- Username identification for each client
- Notification when users join or leave the chat
- Multithreaded client handling for smooth communication
- Simple command-line interface

---

## How It Works

### Server (`server.py`)

The server is responsible for managing all connected clients and broadcasting messages.

It performs the following tasks:

- Creates a TCP socket server bound to `127.0.0.1:55555`
- Listens for incoming connections
- Requests usernames from clients
- Stores active clients and usernames in lists
- Broadcasts messages to all connected clients
- Handles client disconnections and removes them from active lists
- Uses threading to handle each client independently

### Key Server Functions:

- `broadcast(message)`
  - Sends a message to all connected clients

- `handle(client)`
  - Receives messages from a specific client
  - Broadcasts messages to others
  - Removes client if disconnected

- `receive()`
  - Accepts new client connections
  - Assigns usernames
  - Starts a new thread for each client

---

### Client (`client.py`)

The client allows a user to connect and interact with the chat server.

It performs the following tasks:

- Connects to the server at `127.0.0.1:55555`
- Prompts the user for a username
- Sends username to the server when requested
- Continuously receives and displays messages
- Sends user-typed messages to the server
- Uses threading to send and receive messages simultaneously

### Key Client Functions:

- `receive()`
  - Listens for messages from the server
  - Sends username when requested
  - Displays messages to the user
  - Handles errors and disconnects safely

- `write()`
  - Reads user input
  - Sends messages to the server in real-time

---

## Technologies Used

- Python 3
- Socket Programming (TCP/IP)
- Threading (Concurrency)

---

## Setup Instructions

### 1. Clone or Download the Project

```bash
git clone <your-repo-url>
cd <your-project-folder>

#-----------------------------------------------------------------------------------------------

2. Run the Server
Start the server first:
python server.py

The server will start listening on:
127.0.0.1:55555

#-----------------------------------------------------------------------------------------------

3. Run the Client(s)
Open a new terminal for each user:
python client.py

Enter a username when prompted and start chatting.

#-----------------------------------------------------------------------------------------------

4. Example Usage
Please choose a username: Sipho
Connected to the server!
John joined the chat!
Sipho: Hello everyone!
John: Hey Sipho!
John has left the chat!

#-----------------------------------------------------------------------------------------------

Project Structure
project/
│
├── server.py   # Handles connections, messaging, and broadcasting
├── client.py   # Handles user input and message receiving
└── README.md   # Project documentation

#-----------------------------------------------------------------------------------------------
Key Concepts Demonstrated:

TCP socket communication
Client-server architecture
Multithreading in Python
Real-time message broadcasting
Handling client connections and disconnections
Basic networking fundamentals

