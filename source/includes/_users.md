# Utilisateurs

## Récupérer les informations


```shell
curl "http://api.obsifight.net/user/<USERNAME>"
  -H "Authorization: TOKEN"
```

> L'API vous retournera le résultat suivant

```json
{
  "status": true,
  "data": {
    "ids": {
      "web": 2,
      "logblock": 19,
      "auth": 30
    },
    "usernames": {
      "histories": [],
      "current": "Eywek"
    },
    "uuid": "84cb4e81-aac7-9790-4938-cf56103fa7c5",
    "registerDate": "2015-10-16T12:04:50.000Z",
    "lastConnection": {
      "id": 330,
      "username": "Eywek",
      "ip": "127.0.0.1",
      "date": "2015-02-12T17:20:34.000Z",
      "mac_adress": null
    },
    "adresses": {
      "mac": [],
      "ip": [
        "127.0.0.1",
        "127.0.0.2"
      ]
    }
  }
}
```

Cette action vous donne les informations de bases d'un utilisateur.

<aside class="info">
Info - Si le pseudo spécifié est un ancien pseudo, le joueur correspondant à cet ancien pseudo sera retourné.
</aside>

### Requête HTTP

`GET http://api.obsifight.net/user/<USERNAME>`

### Paramètre

Paramètre | Par défaut | Description
--------- | ------- | -----------
USERNAME | '' | Doit contenir le pseudo ou l'ID (site)

<aside class="success">
Note — cette action est privée, vous devez spécifiez un token.
</aside>

## Vérifier les identifiants


```shell
curl -XPOST "http://api.obsifight.net/user/authenticate"
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"username": "Eywek", "password": "Mon mot de passe non encodé"}'
```

> L'API vous retournera le résultat suivant

```json
{
  "status": true,
  "data": {
    "user": {
      "id": 2,
    }
  }
}
```

Cette action vous retourne l'ID (web) de l'utilisateur correspondant aux identifiants transmis

### Requête HTTP

`POST http://api.obsifight.net/user/authenticate`

### Paramètre

Paramètre | Description
--------- | -------
username | Doit contenir le pseudo du joueur
password | Doit contenir le mot de passe du joueur (non encodé)

<aside class="success">
Note — cette action est privée, vous devez spécifiez un token.
</aside>

## Savoir si un joueur peut voter

```shell
curl "http://api.obsifight.net/user/<USERNAME>/vote/can"
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "success": "User can vote!"
}
```

```json
{
  "status": false,
  "success": "User can't vote!"
}
```

```json
{
  "status": true,
  "success": "User hasn't vote yet!"
}
```

```json
{
  "status": true,
  "success": "Admin hasn't config vote yet!"
}
```

Cette action vous indique si un joueur peut re-voter.
Si le `status` est à `true`, le joueur peut re-voter et inversément.

### Requête HTTP

`GET http://api.obsifight.net/user/<USERNAME>/vote/can`

### Paramètre

Paramètre | Description
--------- | -----------
USERNAME | Le pseudo du joueur recherché
