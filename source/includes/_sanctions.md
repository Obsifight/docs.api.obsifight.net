# Sanctions

## Récupérer les bans

```shell
curl "http://api.obsifight.net/sanction/bans"
```

> L'API vous retournera un résultat de ce type

```json
{
  "status": true,
  "data": {
    "bans": [
      {
        "id": 3889,
        "reason": "cc",
        "ban": "(global)",
        "date": "2016-11-23T14:21:16.000Z",
        "staff": {
          "username": "yelrambec"
        },
        "end_date": null,
        "state": 1,
        "duration": "PERMANENT",
        "remove_date": null,
        "remove_staff": null,
        "remove_reason": null,
        "ip": "77.132.218.165",
        "ban_type": "ip"
      },
      {
        "id": 3890,
        "reason": "cc",
        "ban": "(global)",
        "date": "2016-11-23T14:21:24.000Z",
        "staff": {
          "username": "yelrambec"
        },
        "end_date": null,
        "state": 1,
        "duration": "PERMANENT",
        "remove_date": null,
        "remove_staff": null,
        "remove_reason": null,
        "user": {
          "uuid": "7fbdeb5e8e9e4decabdd3d5d0b7bc178",
          "username": "lebgdu74"
        },
        "ban_type": "user"
      }
    ]
  }
}
```

Cette action vous liste les bans dans l'ordre décroissant.

### Requête HTTP

`GET http://api.obsifight.net/sanction/bans?limit=<limit>`

### Paramètre

Parameter | Description
--------- | -----------
limit | Le nombre de ban a récupérer (facultatif)
