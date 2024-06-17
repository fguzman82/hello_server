# Hello Server

## Project Overview

The `hello_server` project is a simple web server designed to demonstrate the basics of handling HTTP requests and responses using Python. This server responds with a "Hello, World!" message, making it an excellent starting point for those new to web development and server-side programming.

## Features

- **Simple HTTP Server:** Implements a basic HTTP server that responds with a "Hello, World!" message.
- **Python Implementation:** Utilizes Python's built-in libraries to handle HTTP requests.
- **Educational Purpose:** Ideal for beginners to understand the fundamentals of web server operations and HTTP protocol.

## Requirements

- Python 3.x

## Installation

1. **Clone the Repository:**
    ```sh
    git clone https://github.com/fguzman82/hello_server.git
    cd hello_server
    ```

2. **Run the Server:**
    ```sh
    python hello_server.py
    ```

3. **Access the Server:**
    Open your web browser and navigate to `http://localhost:8080`. You should see the message "Hello, World!".

## Code Explanation

The main code for the server is located in the `hello_server.py` file. Here's a brief overview:

```python
import http.server
import socketserver

PORT = 8080

class MyHandler(http.server.SimpleHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header("Content-type", "text/html")
        self.end_headers()
        self.wfile.write(b"Hello, World!")

with socketserver.TCPServer(("", PORT), MyHandler) as httpd:
    print(f"Serving at port {PORT}")
    httpd.serve_forever()
