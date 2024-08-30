# The Ship - Documentation

[home](../README.md)

## Documentation

Der Laser ist ein gefährliches Stück Hardware. Um ihn einsetzen zu können, muss ein Techniker sich zuerst einloggen.
Dies ist über diese URL möglich: [http://192.168.100.13:2018/login](http://192.168.100.13:2018/login).

Das Login verwendet OAuth2 und muss zuerst konfiguriert werden:

```sh
$ curl -XPOST http://192.168.100.13:2018/configure_oauth --data '{"client_secret": "XXX", "authorize_url": "http://XXX:2015/authorize", "token_url": "http://XXX:2015/token"}'
{
  "kind": "success"
}
```

Nützliche Links:

- [https://www.redhat.com/architect/oauth-20-authentication-keycloak](https://www.redhat.com/architect/oauth-20-authentication-keycloak)

Nach der Aktivierung:

```sh
$ curl -XPOST http://192.168.100.13:2018/activate
{
  "kind": "success"
}

$ curl -XPOST http://192.168.100.13:2018/deactivate
{
  "kind": "success"
}

$ curl -XPUT --data '{"angle": 42 }' http://192.168.100.13:2018/angle
{
  "kind": "success"
}

$ curl http://192.168.100.13:2018/state
{
  "kind": "success",
  "is_active": true,
  "is_cooling_down": false,
  "is_mining": true
}
```

## Widget

| Laser |
|-------|
| [doc](http://192.168.100.13:2000/doc/Laser/0) | [max](http://192.168.100.13:2000/widget/Laser/0) |

Aktueller Status: Freigeschaltet, aktiv und aktiv am Abbauen

```json
{
  "title": "Laser",
  "group": "status-only",
  "width": 2,
  "height": 2,
  "content": {
    "kind": "stack",
    "content": [
      {
        "kind": "text",
        "text": "Aktueller Status: Freigeschaltet, aktiv und aktiv am Abbauen"
      }
    ]
  }
}
