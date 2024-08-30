# The Ship - Documentation

[home](../README.md)

## Documentation

### Read Current Position

```shell
$ curl http://192.168.100.13:2011/pos
{
  "kind": "success",
  "pos": {
    "x": 1,
    "y": 2,
    "angle": 3
  },
  "velocity": {
    "x": 0.0,
    "y": 0.0,
    "angle": 0.0
  }
}
```

### Get Near Stations

```shell
$ curl http://192.168.100.13:2011/stations_in_reach
{
  "kind": "success",
  "stations": {
    "station name": {
      "resources": {
        "GOLD": {
          "buy_price": 0,
          "sell_price": 100
        }
      },
      "items": {
        "nice item": {
          "buy_price": 1000
        }
      }
    }
  }
}
```

### Buy Resource from Station

```shell
$ curl -XPOST http://192.168.100.13:2011/buy --data '{"station": "Core Station", "what": "GOLD", "amount": 2}'
{
  "kind": "success"
}
```

### Sell Resource to Station

```shell
$ curl -XPOST http://192.168.100.13:2011/sell --data '{"station": "Core Station", "what": "IRON", "amount": 2}'
{
  "kind": "success"
}
```

### Buy Item from Station

```shell
$ curl -XPOST http://192.168.100.13:2011/buy_item --data '{"station": "Core Station", "what": "nice item"}'
{
  "kind": "success"
}
```

## Widget

```json
{
  "title": "Communication",
  "group": "user",
  "width": 4,
  "height": 10,
  "content": {
    "kind": "stack",
    "content": []
  }
}
```