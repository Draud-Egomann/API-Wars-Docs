# The Ship - Documentation

[home](../README.md)

## Documentation

### Example use

```sh
curl -XPUT http://192.168.100.13:2003/thruster --data '{"thrust_percent": 0}'
curl -XPUT http://192.168.100.13:2003/thruster --data '{"thrust_percent": 50}'
curl -XPUT http://192.168.100.13:2003/thruster --data '{"thrust_percent": 100}'
```

### Widget

| Thruster back    |                      |
|------------------|----------------------|
| doc              | max                  |
| **0.0%**         |                      |
| **Boost**        |                      |

```json
{
  "title": "Thruster back",
  "group": "auxiliary",
  "width": 1,
  "height": 2,
  "content": [
    {
      "kind": "stack",
      "content": [
        {
          "kind": "text",
          "text": "0.0%"
        },
        {
          "kind": "button",
          "id": "boost",
          "text": "Boost",
          "pressed": false
        }
      ]
    }
  ]
}
