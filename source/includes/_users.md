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

## Récupérer le pseudo depuis un UUID


```shell
curl "http://api.obsifight.net/user/from/uuid/<UUID>"
  -H "Authorization: TOKEN"
```

> L'API vous retournera le résultat suivant

```json
{
  "status": true,
  "data": {
    "username": "Eywek"
  }
}
```

Cette action vous donne le pseudo actuel de l'UUID fourni

### Requête HTTP

`GET http://api.obsifight.net/user/from/uuid/<UUID>`

### Paramètre

Paramètre | Description
--------- | ------- | -----------
UUID | Doit contenir l'UUID (avec tirets)

<aside class="success">
Note — cette action est privée, vous devez spécifiez un token.
</aside>

## Récupérer l'UUID depuis un pseudo


```shell
curl "http://api.obsifight.net/user/uuid/from/<username>"
  -H "Authorization: TOKEN"
```

> L'API vous retournera le résultat suivant

```json
{
  "status": true,
  "data": {
    "uuid": "84cb4e81-aac7-4938-9790-cf56103fa7c5"
  }
}
```

Cette action vous donne l'UUID du pseudo fourni

### Requête HTTP

`GET http://api.obsifight.net/user/uuid/from/<username>`

### Paramètre

Paramètre | Description
--------- | -------
username | Doit contenir le pseudo

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

## Récupérer le nombre de points boutique

```shell
curl "http://api.obsifight.net/user/<USERNAME>/money"
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": {
    "money": 6457
  }
}
```

Cette action vous donne le nombre de points boutique du joueur.

### Requête HTTP

`GET http://api.obsifight.net/user/<USERNAME>/money`

### Paramètre

Paramètre | Description
--------- | -----------
USERNAME | Le pseudo du joueur recherché

## Transférer des points boutique

```shell
curl -XPOST "http://api.obsifight.net/user/<USERNAME>/money/transfer"
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"amount": 10, "receiver": "Suertzz"}'
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "success": "Transfer successfully proceeded."
}
```

```json
{
  "status": false,
  "success": "User didn't have enough money."
}
```

Cette action vous permet d'échanger des points boutique entre deux joueurs.

### Requête HTTP

`POST http://api.obsifight.net/user/<USERNAME>/money/transfer`

### Paramètre

Paramètre | Description
--------- | -----------
USERNAME | Le pseudo du joueur qui envoit
amount | Le montant de la transaction
receiver | Le pseudo du joueur qui reçoit

## Informations sur les points boutique

```shell
curl "http://api.obsifight.net/user/<USERNAME>/money/timeline"
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": {
    "oldBalance": 6457,
    "current": 3941,
    "timeline": [
      {
        "date": "2017-01-08T21:25:40.000Z",
        "action_id": "purchase_item",
        "action_type": "remove",
        "action_message": "Buy Kit Minerai",
        "sold": "-249"
      },
      {
        "date": "2017-01-07T17:30:13.000Z",
        "action_id": "purchase_money_paysafecard",
        "action_type": "add",
        "action_message": "Pay with paysafecard",
        "sold": "+12"
      },
      {
        "date": "2017-01-07T15:30:00.000Z",
        "action_id": "refund",
        "action_type": "add",
        "action_message": "Refunded",
        "sold": "+2990"
      }
    ]
  }
}
```

Cette action vous donne toutes les actions effectués sur les points boutique du joueur de manière chronologique.

### Requête HTTP

`GET http://api.obsifight.net/user/<USERNAME>/money/timeline`

### Paramètre

Paramètre | Description
--------- | -----------
USERNAME | Le pseudo du joueur recherché

## Chercher un joueur

```shell
curl -XPOST 'http://api.obsifight.net/user/find'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"ip": "127.0.0.1", "mac": "00-00-00-00-00-00"}'
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": [
    {
      "username": "Eywek",
      "last_connection": "2017-01-23T18:50:21.000Z"
    }
  ]
}
```

Cette action vous donne tous les utilisateurs et leurs dernières connexion correspondant à l'IP ou à l'adresse MAC fournie

### Requête HTTP

`POST http://api.obsifight.net/user/find`

### Paramètre

Paramètre | Description
--------- | -----------
ip | L'ip du joueur recherché (optionnel si `mac` est fourni)
mac | L'ip du joueur recherché (optionnel si `ip` est fourni)

## Récupérer des pseudos

```shell
curl -XPOST 'http://api.obsifight.net/user/infos/username'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"ids": [1, 2]}'
```

```shell
curl -XPOST 'http://api.obsifight.net/user/infos/username'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
  -d '{"uuids": ["84cb4e81-aac7-4938-9790-cf56103fa7c5"]}'
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": {
    "users": {
      "1": "Eywek",
      "2": "yolo"
    }
  }
}
```

```json
{
  "status": true,
  "data": {
    "users": {
      "84cb4e81-aac7-4938-9790-cf56103fa7c5": "Eywek"
    }
  }
}
```

Cette action vous donne tous les pseudos des IDs/UUIDs fournis en paramètres.

### Requête HTTP

`POST http://api.obsifight.net/user/infos/username`

### Paramètre

Paramètre | Description
--------- | -----------
ids | Tableau contenant des IDs (doit être vide si `uuids` est rempli)
uuids | Tableau contenant des UUIDs (doit être vide si `ids` est rempli)

## Comparer des joueurs

```shell
curl -XGET 'http://api.obsifight.net/user/compare/<username 1>/<username 2>'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": {
    "commonIPPercentage": 40,
    "commonMACPercentage": 100
  }
}
```

Cette action vous donne le pourcentage d'adresses IP et MAC en commun entre les 2 joueurs fournis

### Requête HTTP

`GET http://api.obsifight.net/user/compare/<username 1>/<username 2>`

### Paramètre

Paramètre | Description
--------- | -----------
username 1 | Pseudo du joueur à comparer
username 2 | Pseudo du joueur à comparer

## Récupérer les stats

```shell
curl -XGET 'http://api.obsifight.net/user/<username>/stats'
  -H "Content-type: application/json"
  -H "Authorization: TOKEN"
```

> L'API vous retournera un des résultats suivants

```json
{
  "status": true,
  "data": {
    "ks": {
      "kills": 0,
      "deaths": 1,
      "ratio": 0
    },
    "history": {
      "kills": [],
      "deaths": [
        "JeSuisLeSIDA"
      ]
    }
  }
}
```

Cette action vous donne les stats d'un joueur (kills/deaths/ratio).

### Requête HTTP

`GET http://api.obsifight.net/user/<username>/stats`

### Paramètre

Paramètre | Description
--------- | -----------
username | Pseudo du joueur
