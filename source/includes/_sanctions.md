# Sanctions

## Récupérer les banissements

```shell
curl "http://api.obsifight.net/sanction/bans"
  -H "Authorization: TOKEN"
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
        "server": "(global)",
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
        "server": "(global)",
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

## Récupérer un banissement

```shell
curl "http://api.obsifight.net/sanction/bans/<id>"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un résultat de ce type

```json
{
  "status": true,
  "data": {
    "ban": {
      "id": 3889,
      "reason": "cc",
      "server": "(global)",
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
    }
  }
}
```

Cette action vous affiche les informations du ban demandé.

### Requête HTTP

`GET http://api.obsifight.net/sanction/bans/<id>`

### Paramètre

Paramètre | Description
--------- | -----------
id | L'ID du ban a récupéré

## Ajouter un banissement

```shell
curl -XPOST 'http://api.obsifight.net/sanction/bans'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"reason": "Ma raison", "server": "(global)", "type": "user", "user": {"username": "Eywek"}}'
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
curl -XPUT 'http://api.obsifight.net/sanction/bans/<id>'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"end_date": "2016-11-28 19:20:01"}'
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

## Récupérer les mutes

```shell
curl "http://api.obsifight.net/sanction/mutes"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un résultat de ce type

```json
{
  "status": true,
  "data": {
    "mutes": [
      {
        "id": 3889,
        "reason": "cc",
        "server": "(global)",
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
        "mute_type": "ip"
      },
      {
        "id": 3890,
        "reason": "cc",
        "server": "(global)",
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
        "mute_type": "user"
      }
    ]
  }
}
```

Cette action vous liste les bans dans l'ordre décroissant.

### Requête HTTP

`GET http://api.obsifight.net/sanction/mutes?limit=<limit>`

### Paramètre

Paramètre | Description
--------- | -----------
limit | Le nombre de mute a récupérer (facultatif)

## Récupérer un mute

```shell
curl "http://api.obsifight.net/sanction/mutes/<id>"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un résultat de ce type

```json
{
  "status": true,
  "data": {
    "mute": {
      "id": 3889,
      "reason": "cc",
      "server": "(global)",
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
      "mute_type": "ip"
    }
  }
}
```

Cette action vous affiche les informations du mute demandé.

### Requête HTTP

`GET http://api.obsifight.net/sanction/mutes/<id>`

### Paramètre

Paramètre | Description
--------- | -----------
id | L'ID du mute a récupéré

## Ajouter un mute

```shell
curl -XPOST 'http://api.obsifight.net/sanction/mutes'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"reason": "Ma raison", "server": "(global)", "type": "user", "user": {"username": "Eywek"}}'
```

> L'API vous retournera un résultat de ce type si le banissement a bien été modifié

```json
{
  "status": true,
  "success": "Mute has been successfuly added!"
}
```

Cette action vous permet d'ajouter un mute (IP ou joueur).

### Requête HTTP

`POST http://api.obsifight.net/sanction/mutes`

### Paramètre

Paramètre | Description
--------- | -----------
reason | La raison du mute
server | Le serveur du mute (nom bungeecord)
type | Le type du mute (`user`, ou `ip`)
user | Les informations du joueur a bannir si le type du mute est 'user' (objet contenant `username` ou `uuid`)
ip | L'IP a mute si le type du mute est 'ip'
end_date | La date de fin du mute (facultatif)

<aside class="warning">
Important — le paramètre `user.uuid` doit être un UUID valide sans les tirets (exemple: `21bee8e06a1d1724acbaded7cce84401`)
</aside>
<aside class="info">
Note — en configurant le paramètre `server` à '(global)', le joueur ou l'IP sera mute sur tous les serveurs
</aside>


## Modifier un mute

```shell
curl -XPUT 'http://api.obsifight.net/sanction/mutes/<id>'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"end_date": "2016-11-28 19:20:01"}'
```

> L'API vous retournera un résultat de ce type si le mute a bien été modifié

```json
{
  "status": true,
  "success": "Mute has been successfuly edited!"
}
```

Cette action vous permet de modifier la date de fin d'un mute ou de le dé-mute.

### Requête HTTP

`PUT http://api.obsifight.net/sanction/mutes/<id>`

### Paramètre

Paramètre | Description
--------- | -----------
id | L'ID du mute a modifier
end_date | La date de find de mute (facultatif)
remove_reason | La raison du dé-mute (facultatif)

<aside class="warning">
Important — le paramètre `end_date` ne doit pas être utilisé pour dé-mute un utilisateur
</aside>
<aside class="info">
Note — en utilisant le paramètre `remove_reason` vous dé-muterais le joueur instantanément, le statut du mute, la date de dé-mute et votre pseudo seront automatiquement ajouté.
</aside>

## Récupérer les sanctions d'un joueur

```shell
curl "http://api.obsifight.net/user/<username>/sanctions"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un résultat de ce type

```json
{
  "status": true,
  "data": {
    "bans": [
      {
        "id": 2433,
        "reason": "Ma super raison",
        "server": "(global)",
        "date": "2016-07-13T21:12:54.000Z",
        "staff": {
          "username": "dem0niak"
        },
        "end_date": null,
        "state": 0,
        "duration": "PERMANENT",
        "remove_date": "2016-07-21T09:33:46.000Z",
        "remove_staff": {
          "username": "IceGamingFr"
        },
        "remove_reason": "Ma raison de déban",
        "user": {
          "uuid": "56dab2e660a7497f804c9d436b317d03",
          "username": "roumi1996"
        },
        "ban_type": "user"
      }
    ],
    "kicks": [
      {
        "id": 636,
        "reason": "Ma raison",
        "server": "(global)",
        "date": "2016-04-03T12:58:07.000Z",
        "staff": {
          "username": "CONSOLE"
        },
        "user": {
          "uuid": "56dab2e660a7497f804c9d436b317d03",
          "username": "roumi1996"
        }
      }
    ],
    "mutes": [
      {
        "id": 7207,
        "reason": "La raison du mute",
        "server": "(global)",
        "date": "2016-05-28T21:19:59.000Z",
        "staff": {
          "username": "Bachi"
        },
        "end_date": "2016-05-28T21:21:59.000Z",
        "state": 0,
        "duration": 120,
        "remove_date": "2016-05-28T21:20:04.000Z",
        "remove_staff": {
          "username": "roumi1996"
        },
        "remove_reason": "La raison du dé-mute",
        "user": {
          "uuid": "56dab2e660a7497f804c9d436b317d03",
          "username": "roumi1996"
        },
        "mute_type": "user"
      }
    ]
  }
}
```

Cette action vous liste les sanctions d'un joueur dans un ordre décroissant

### Requête HTTP

`GET http://api.obsifight.net/user/<username>/sanctions?limit=<limit>`

### Paramètre

Paramètre | Description
--------- | -----------
username | Le pseudo du joueur
limit | Le nombre de ban a récupérer (facultatif)
