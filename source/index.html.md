---
title: Docs - ObsiFight API

language_tabs:

toc_footers:
  - <a href='http://api.obsifight.net'>Accéder à l'API</a>
  - <a href='https://obsifight.net'>Revenir sur le site</a>

includes:
  - errors

search: true
---

# Introduction

Bienvenue sur la documentation de l'API des services d'ObsiFight !

Cette documentation est destinée aux développeurs d'ObsiFight, elle a pour but d'expliquer le fonctionnement et comment utiliser l'API HTTP d'ObsiFight.

# Authentication

Pour utiliser l'API et certaines routes privées, vous devez vous authentifier à l'aide d'un __pseudo__ et d'un __mot de passe__ qui vous serons founis.
Pour éviter d'utiliser votre mot de passe et votre pseudo lors de chaque requête, vous utiliserez un __token__.

## Récupérer le token d'authentification

> Contenu de la requête pour s'authentifier

```json
{
  "username": "Votre pseudo",
  "password": "Votre mot de passe"
}
```

> La requête doit être fait en POST pour pouvoir envoyer les données

> Vous recevrez une réponse de ce type

```json
{
  "status": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6..."
  }
}
```

Il vous faut appeler l'URL <code>POST http://api.obsifight.net/authenticate</code> en spécifiant dans le corps de la requête vos identifiants en JSON.

<aside class="notice">
Le token obtenu est valable 5 minutes.
</aside>

## Une fois le token récupéré

Pour vous authentifier, au cours des requêtes vous devrez spécifier dans un header (_Authorization_) le token que vous aurez récupéré.

`Authorization: TOKEN`

<aside class="notice">
Vous devez remplacer <code>TOKEN</code> par votre token obtenu précédemment.
</aside>

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

### Requête HTTP

`GET http://api.obsifight.net/user/<USERNAME>`

### Paramètres

Paramètre | Par défaut | Description
--------- | ------- | -----------
USERNAME | '' | Doit contenir le pseudo ou l'ID (site)

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
  "status": true,
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

### HTTP Request

`GET http://api.obsifight.net/user/<USERNAME>/vote/can`

### URL Parameters

Parameter | Description
--------- | -----------
USERNAME | Le pseudo du joueur recherché
