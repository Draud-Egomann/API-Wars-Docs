# The Ship - Documentation

[home](../README.md)

## Documentation

Der Permastore braucht einen S3 Storage, damit die Daten abelegt werden können.

Die Konfiguration ist hardcodiert:

|          |                                  |
|----------|----------------------------------|
| **host** | [http://192.168.100.13:2016](http://192.168.100.13:2016) |
| **bucket** | theship-permastore               |
| **access key** | theship                      |
| **secret key** | theship1234                  |

Der Permastore benötigt:

- Ein Universal Coupler Module (das müsst ihr selber implementieren)
- für Station das dazugehörige Comm-Module

## Permastore Interface

Der Permastore kann verwendet werden, um Daten, die eine Station an eine andere senden würde, zwischenzuspeichern. Ein Beispiel:

```sh
# at Elyse Terminal
$ curl -XPOST http://192.168.100.13:2019/download --data '{"source": "Elyse Terminal", "destination": "Artemis Station"}'
{"kind": "success"}

# at Artemis Station
$ curl -XPOST http://192.168.100.13:2019/upload --data '{"source": "Elyse Terminal", "destination": "Artemis Station"}'
{"kind": "success"}
```

## Universal Coupler Module

Das Universal Coupler Module muss eine JSON HTTP Schnittstelle implementieren:

```sh
$ curl -XPOST 'http://192.168.100.13:2023/Artemis%20Station/receive'
{"kind": "success", "messages": [{"destination": "Shangris Station", "data": [0, 1, 2, 3, 4]}]}
```

```sh
$ curl -XPOST 'http://192.168.100.13:2023/Artemis%20Station/send' --data '{"source": "Shangris Station", "data": [0, 1, 2, 3]}'
{"kind": "success"}
```

## Widget

| Permastore                              |
|-----------------------------------------|
| [doc](http://192.168.100.13:2000/doc/Permastore/0) | [max](http://192.168.100.13:2000/widget/Permastore/0) |

```json
{
  "title": "Permastore",
  "group": "status-only",
  "width": 3,
  "height": 2,
  "content": {
    "kind": "stack",
    "content": []
  }
}
