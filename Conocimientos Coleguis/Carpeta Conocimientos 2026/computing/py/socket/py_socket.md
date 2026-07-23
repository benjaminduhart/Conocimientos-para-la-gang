---
author: Mindusting
corrected: false
tags:
  - Programming
  - Python
  - Module
  - Socket
  - NetWork
title: Módulo socket en Python
---

# SOCKET EN PYTHON

> [!fail]- ESTE APARTADO ESTÁ INCOMPLETO
> > [!todo] #TODO

> [!help]- REFERENCIAS WEB
> - [Python](https://docs.python.org/3/library/socket.html) #WWW/Python
> 
> YouTube:
> - [Tech With Tim](https://youtu.be/3QiPPX-KeSc) #WWW/YT/TechWithTim

Para comunicar procesos dentro de la misma máquina se puede usar `localhost`; para cuando son dos máquinas, el servidor tiene que tener el `HOST` `0.0.0.0` para escuchar desde todas las IPs y el cliente debe tener como `HOST` la IP del servidor.

```python
import socket
import threading
import struct


def main():
    PORT = 12345
    HOST = "localhost"

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((HOST, PORT))
    server_socket.listen()
    
    while True:
        client_data = server_socket.accept()

        thread = threading.Thread(
            target=lambda: handle_client(*client_data)
        )
        thread.start()


def handle_client(client_socket: socket.socket, address: str):

    def get_package():
        data = client_socket.recv(8)

        if not data:
            # Close conection
            return None

        package_size = struct.unpack("!Q", data)[0]

        print(package_size)

        return client_socket.recv(package_size)
    
    def send_message(data):
        package_size = struct.pack("!Q", len(data))

        client_socket.send(package_size)
        client_socket.send(data)

    print(f"Conectado por: {address}")

    while True:
        data = get_package()
        if data is None:
            break
        send_message(data)

    client_socket.close()


if "__main__" == __name__:
    main()
```

```python
import socket
import struct


def main():
    PORT = 12345
    HOST = "localhost"

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    client_socket.connect((HOST, PORT))

    def get_package():
        data = client_socket.recv(8)

        if not data:
            # Close conection
            return None

        package_size = struct.unpack("!Q", data)[0]

        print(package_size)

        return client_socket.recv(package_size)
    
    def send_message(data):
        package_size = struct.pack("!Q", len(data))

        client_socket.send(package_size)
        client_socket.send(data)

    data = b"Hello workd!"

    send_message(data)

    data = get_package()

    client_socket.close()

    print(f"Respuesta: {data!r}")


if "__main__" == __name__:
    main()
```
