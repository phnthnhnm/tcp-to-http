# TCP to HTTP Server Project

This project demonstrates a multi-protocol server system that includes TCP, UDP, and HTTP/1.1 servers. Each server is
implemented to showcase different types of network communication and functionality.

## Project Overview

The project consists of three main components:

1. **HTTP Server**: A custom HTTP/1.1 server that handles various routes and provides responses or proxies requests to
   external services.
2. **TCP Listener**: A TCP server that listens for incoming connections and parses HTTP-like requests.
3. **UDP Sender**: A UDP client that sends messages to a specified UDP server.

## Features

### HTTP Server

- **Port**: `42069`
- **Routes**:
    - `/httpbin/*`: Proxies requests to [httpbin.org](https://httpbin.org).
    - `/video`: Serves a static video file (`assets/vim.mp4`).
    - `/yourproblem`: Returns a `200 OK` response with a success message.
    - `/myproblem`: Returns a `500 Internal Server Error` response with an error message.
    - Any other route: Returns a `200 OK` response with a default success message.

#### Running the HTTP Server

```bash
go run cmd/httpserver/main.go
```

The server will start on `http://localhost:42069`.

#### Example Routes

- Proxy: `http://localhost:42069/httpbin/get`
- Video: `http://localhost:42069/video`
- Success: `http://localhost:42069/yourproblem`
- Error: `http://localhost:42069/myproblem`

---

### TCP Listener

- **Port**: `42069`
- **Functionality**: Listens for incoming TCP connections, parses HTTP-like requests, and logs the request details.

#### Running the TCP Listener

```bash
go run cmd/tcplistener/main.go
```

The server will start listening for TCP traffic on `localhost:42069`.

#### Example Usage

Use tools like `telnet` to test the TCP listener:

```bash
telnet localhost 42069
```

Send an HTTP-like request:

```
GET /example HTTP/1.1
Host: localhost
```

The server will log the parsed request details, including the method, target, headers, and body.

---

### UDP Sender

- **Functionality**: Sends messages to a UDP server running on `localhost:42069`.

#### Running the UDP Sender

```bash
go run cmd/udpsender/main.go
```

The client will prompt you to type messages. Press `Enter` to send each message.

#### Example Usage

1. Start the UDP sender.
2. Type a message and press `Enter`.
3. The message will be sent to the UDP server.

---

## Project Structure

```
tcp-to-http/
├── cmd/
│   ├── httpserver/
│   │   └── main.go       # HTTP server implementation
│   ├── tcplistener/
│   │   └── main.go       # TCP listener implementation
│   └── udpsender/
│       └── main.go       # UDP sender implementation
├── internal/
│   ├── headers/          # HTTP headers utilities
│   ├── request/          # HTTP request parsing
│   ├── response/         # HTTP response construction
│   └── server/           # HTTP server utilities
└── assets/
    └── vim.mp4           # Video file served by the HTTP server
```

---

## Prerequisites

- Go 1.19 or later
- Internet connection (for proxying requests to `httpbin.org`)

---

## Building and Running

1. Clone the repository:

   ```bash
   git clone https://github.com/phnthnhnm/tcp-to-http.git
   cd tcp-to-http
   ```

2. Run the desired server:

    - HTTP Server: `go run cmd/httpserver/main.go`
    - TCP Listener: `go run cmd/tcplistener/main.go`
    - UDP Sender: `go run cmd/udpsender/main.go`

---