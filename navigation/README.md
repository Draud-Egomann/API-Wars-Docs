# The Ship - Documentation

[home](../README.md)

## Documentation

### Get Position of the Ship

```sh
$ curl -XGET http://192.168.100.13:2010/pos
{
  "kind": "success",
  "pos": {
    "x": 0,
    "y": 100,
    "angle": 33
  },
  "velocity": {
    "x": 0,
    "y": 0,
    "angle": 0
  }
}
```

## Widget

| Navigation                              |
|-----------------------------------------|
| [doc](http://192.168.100.13:2000/doc/Navigation/0) | [max](http://192.168.100.13:2000/widget/Navigation/0) |

```json
{
  "title": "Navigation",
  "group": "auxiliary",
  "width": 2,
  "height": 1,
  "content": {
    "kind": "text",
    "text": "-9931.0/20713.0"
  }
}
