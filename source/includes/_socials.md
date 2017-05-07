# Réseaux sociaux

## Lier un compte Twitter


```shell
curl "http://api.obsifight.net/socials/twitter/authorization/request?userId=1&callback=https://obsifight.net/user/profile/social/twitter/link/success&notification=https://obsifight.net/user/profile/social/twitter/link/notification&authKey=967520ae23e8ee14888bae72809031b98398ae4a636773e18fff917d77679334"
```

> L'API va redirigé l'utilisateur vers Twitter pour demander l'autorisation puis vers le callback spécifié

Cette action permet de lier un compte Twitter à un utilisateur. Une fois que l'utilisateur a accepté l'authentification auprès de Twitter celui-ci est redirigé vers le callback spécifié avec comme informations `id` et `screen_name` en informations GET. Entre temps, l'API envoie une notification sur l'url de notification soumise avec comme informations `accessToken`, `accessSecret`, `userId`, `user`, `authKey`.

<aside class="info">
Info - Si l'utilisateur avait déjà lié un compte, celui-ci sera automatiqument dé-lié au profit du nouveau.
</aside>

### Requête HTTP

`GET http://api.obsifight.net/socials/twitter/authorization/request`

### Paramètre

Paramètre | Description
--------- | -------
userId | Doit contenir l'ID du joueur (site)
callback | Doit contenir une URL valide vers laquelle l'utilisateur sera redirigé
notification | Doit contenir une URL valide à laquelle sera envoyée les informations
authKey | Un hash en sha256 du mot de passe de l'utilisateur

<aside class="success">
Note — cette action est publique pour permettre aux utilisateurs d'y accéder en GET.
</aside>

## Obtenir les tweets "aimés"


```shell
curl "http://api.obsifight.net/socials/twitter/tweets/liked?count=1"
```

> L'API va retourner une liste de tweets comme ceci :

```json
{
  "status":true,
  "data":[
    {
      "id":860167413471555600,
      "text":"@ObsiFight Pas grave ;) Bon chance au développeur :p",
      "retweet_count":0,
      "retweeted":false,
      "created_at":"Thu May 04 16:21:07 +0000 2017",
      "user":{
        "id":728282238287220700,
        "name":"Northen_Flo",
        "screen_name":"NorthenFlo"
      }
    }
  ]
}
```

Cette action permet de récupérer les tweets aimé par le compte Twitter \@ObsiFight.

### Requête HTTP

`GET http://api.obsifight.net/socials/twitter/tweets/liked`

### Paramètre

Paramètre | Description
--------- | -------
count | Permet de limiter le nombre de résultat

<aside class="success">
Note — cette action est publique pour permettre aux utilisateurs d'y accéder en GET.
</aside>
