# The Ship - Documentation

[home](../README.md)

## Documentation

### Dependencies

- Advanced Message Queuing Protocol (AMQP) Broker (e.g. [RabbitMQ](https://www.rabbitmq.com/)), to publish the found objects

### Examples

These examples use [pika](https://pypi.org/project/pika/). The server uses an exchange for Publish/Subscribe. This tutorial may be of interest: <https://www.rabbitmq.com/tutorials/tutorial-three-python.html>.

```python
import pika
import json

connection = pika.BlockingConnection(pika.ConnectionParameters(host="192.168.100.13", port=2014))
channel = connection.channel()

channel.exchange_declare(exchange='scanner/detected_objects', exchange_type='fanout')
result = channel.queue_declare(queue='', exclusive=True)
queue_name = result.method.queue
channel.queue_bind(exchange='scanner/detected_objects', queue=queue_name)

for method_frame, properties, body in channel.consume(queue=queue_name, auto_ack=True):
    print(json.loads(body.decode('utf-8')))
```

**Result:**

```sh
$ ./example.py
[{'name': 'Core Station', 'pos': {'x': 0.0, 'y': 0.0}}]
[{'name': 'Core Station', 'pos': {'x': 0.0, 'y': 0.0}}]
...
```

### Widget

| Scanner                              |
|--------------------------------------|
| [doc](#)                             | [max](#)                             |
| Status: rabbitmq: could not connect to 192.168.100.13:2014 |
| **name**     | **pos**               |

```json
{
  "title": "Scanner",
  "group": "auxiliary",
  "width": 3,
  "height": 4,
  "content": {
    "kind": "stack",
    "content": [
      {
        "kind": "text",
        "text": "Status: rabbitmq: could not connect to 192.168.100.13:2014"
      },
      {
        "kind": "table",
        "header": [
          {
            "kind": "text",
            "text": "name"
          },
          {
            "kind": "text",
            "text": "pos"
          }
        ],
        "rows": []
      }
    ]
  }
}
