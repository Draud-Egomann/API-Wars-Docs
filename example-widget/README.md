# The Ship - Documentation

[home](../README.md)

## Documentation

```python
#!/usr/bin/python3
import socket
import os
import json

with open(__file__, 'r') as f:
    this_file = f.read()
doc = f'''```python
{this_file}
```'''

#https://realpython.com/python-sockets/
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((os.environ['K8S_HOST'], 2002))
    s.sendall(
        json.dumps(
            {
                'kind': 'update_widget',
                'widget': {
                    'title': 'Example widget',
                    'group': 'auxiliary',
                    'width': 2,
                    'height': 2,
                    'content': {
                        'kind': 'text',
                        'text': 'This is an example widget. Please see the doc',
                    },
                }
            }
        ).encode('utf-8')
    )

    s.sendall(b'\0')  # null-byte -> end of message
    s.sendall(json.dumps({
        'kind': 'update_doc',
        'doc': doc,
    }).encode('utf-8'))
    s.sendall(b'\0')  # null-byte -> end of message
    buffer = bytes()
    while True:
        received = s.recv(1)
        if len(received) == 0:
            print('disconnected')
            break
        if received == b'\0':
            print(buffer)
            s.sendall(json.dumps({'kind': 'keepalive'}).encode('utf-8'))
            s.sendall(b'\0')  # null-byte -> end of message
            buffer = bytes()
        else:
            buffer += received
```

## Widget

```json
{
    "title": "Example widget",
    "group": "auxiliary",
    "width": 2,
    "height": 2,
    "content": {
        "kind": "text",
        "text": "This is an example widget. Please see the doc"
    }
}
```
