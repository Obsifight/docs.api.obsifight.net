# Sanctions

## Récupérer les banissements

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

Paramètre | Description
--------- | -----------
limit | Le nombre de ban a récupérer (facultatif)

## Ajouter un banissement

```shell
curl -XPOST -H "Content-type: application/json"
-d '{"reason": "Ma raison", "server": "(global)", "type": "user", "user": {"username": "Eywek"}}'
'http://api.obsifight.net/sanction/bans'
```

> L'API vous retournera un résultat de ce type si le banissement a bien été modifié

```json
{
  "status": true,
  "success": "Ban has been successfuly added!"
}
```

Cette action vous permet d'ajouter un banissement (IP ou joueur).

### Requête HTTP

`POST http://api.obsifight.net/sanction/bans`

### Paramètre

Paramètre | Description
--------- | -----------
reason | La raison du banissement
server | Le serveur du banissement (nom bungeecord)
type | Le type du banissement (`user`, ou `ip`)
user | Les informations du joueur a bannir si le type du banissement est 'user' (objet contenant `username` ou `uuid`)
ip | L'IP a bannir si le type du banissement est 'ip'
end_date | La date de fin du banissement (facultatif)

<aside class="warning">
Important — le paramètre `user.uuid` doit être un UUID valide sans les tirets (exemple: `21bee8e06a1d1724acbaded7cce84401`)
</aside>
<aside class="info">
Note — en configurant le paramètre `server` à '(global)', le joueur ou l'IP sera banni(e) sur tous les serveurs
</aside>


## Modifier un banissement

```shell
curl -H "Content-type: application/json"
-d '{"end_date": "2016-11-28 19:20:01"}' 'http://api.obsifight.net/sanction/bans/<id>'
```

> L'API vous retournera un résultat de ce type si le banissement a bien été modifié

```json
{
  "status": true,
  "success": "Ban has been successfuly edited!"
}
```

Cette action vous permet de modifier la date de fin d'un banissement ou de le débannir.

### Requête HTTP

`PUT http://api.obsifight.net/sanction/bans/<id>`

### Paramètre

Paramètre | Description
--------- | -----------
id | L'ID du bannissement a modifier
end_date | La date de find de bannissement (facultatif)
remove_reason | La raison du dé-banissement (facultatif)

<aside class="warning">
Important — le paramètre `end_date` ne doit pas être utilisé pour débannir un utilisateur
</aside>
<aside class="info">
Note — en utilisant le paramètre `remove_reason` vous dé-bannierais le joueur instantanément, le statut du bannissement, la date de dé-banissement et votre pseudo seront automatiquement ajouté.
</aside>
