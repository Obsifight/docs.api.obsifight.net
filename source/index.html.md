---
title: Docs - ObsiFight API

language_tabs:

toc_footers:
  - <a href='http://api.obsifight.net'>Accéder à l'API</a>
  - <a href='https://obsifight.net'>Revenir sur le site</a>
  - "<em style=\"position:absolute;bottom:5px;\">Version de l'API : 1.0.1</em>"

includes:
  - users
  - sanctions
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
