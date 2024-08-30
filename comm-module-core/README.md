# The Ship - Documentation

[Home](../README.md)

## Documentation

Die Core Station nutzt ReST zur Kommunikation.

```bash
$ curl -XPOST http://192.168.100.13:2027/send --data '{"source": "Core Station", "message": "dGVzdAo="}'
{ "kind": "success" }
```

```bash
$ curl -XPOST http://192.168.100.13:2027/receive
{ "kind": "success", "received_messages": [{"target": "Core Station", "data": "dGVzdAo="}] }
```

## Widget

```json
{
  "title": "Comm Module Core",
  "group": "status-only",
  "width": 1,
  "height": 1,
  "content": {
    "kind": "stack",
    "content": [
      {
        "kind": "text",
        "text": "ready"
      }
    ]
  }
}
```
