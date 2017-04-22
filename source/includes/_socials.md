# Réseaux sociaux

## Lier un compte Twitter


```shell
curl "http://api.obsifight.net/socials/twitter/authorization/request?userId=1&callback=https://obsifight.net/user/profile/social/twitter/link/success&authKey=967520ae23e8ee14888bae72809031b98398ae4a636773e18fff917d77679334"
```

> L'API va redirigé l'utilisateur vers Twitter pour demander l'autorisation puis vers le callback spécifié

Cette action permet de lier un compte Twitter à un utilisateur. Une fois que l'utilisateur a accepté l'authentification auprès de Twitter celui-ci est redirigé vers le callback spécifié avec comme informations `id` et `screen_name` en informations GET.

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
authKey | Un hash en sha256 du mot de passe de l'utilisateur

<aside class="success">
Note — cette action est publique pour permettre aux utilisateurs d'y accéder en GET.
</aside>
