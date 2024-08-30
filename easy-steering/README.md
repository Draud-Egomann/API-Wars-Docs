# The Ship - Documentation

[home](../README.md)

## Documentation

### set target to fly to

```shell
$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": "idle"}'
{"kind": "success"}

$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": "stop"}'
{"kind": "success"}

$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": "Core Station"}'
{"kind": "success"}

$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": "station 1"}'
{"kind": "success"}

$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": "Vesta Station"}'
{"kind": "success"}

$ curl -XPOST http://192.168.100.13:2009/set_target --data '{"target": {"x": 100, "y": 100}}'
{"kind": "success"}
```

## Widget

```json
{
  "title": "Easy Steering",
  "group": "user",
  "width": 3,
  "height": 4,
  "content": {
    "kind": "stack",
    "content": [
      {
        "kind": "text",
        "text": "SpecialTarget.STOP"
      },
      {
        "kind": "button",
        "id": "{\"action\": \"idle\"}",
        "text": "idle",
        "pressed": false
      },
      {
        "kind": "button",
        "id": "{\"action\": \"stop\"}",
        "text": "stop",
        "pressed": true
      },
      {
        "kind": "button",
        "id": "{\"action\": \"goto\", \"name\": \"Core Station\"}",
        "text": "Core Station",
        "pressed": false
      },
      {
        "kind": "button",
        "id": "{\"action\": \"goto\", \"name\": \"Vesta Station\"}",
        "text": "Vesta Station",
        "pressed": false
      },
      {
        "kind": "button",
        "id": "{\"action\": \"goto\", \"name\": \"Azura Station\"}",
        "text": "Azura Station",
        "pressed": false
      }
    ]
  }
}
```
