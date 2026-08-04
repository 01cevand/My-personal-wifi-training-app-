# WiFi Zone OS — mon parcours

Application personnelle qui regroupe toutes les formations WiFi Zone, Starlink et
MikroTik, avec la progression, les notes, le budget matériel et le calculateur de
rentabilité. Elle fonctionne hors ligne une fois installée.

---

## Contenu du dossier

```
index.html               ← toute l'application (design, données, logique)
manifest.webmanifest     ← ce qui la rend installable comme une vraie app
sw.js                    ← le mode hors ligne
icons/                   ← les icônes de l'app
```

---

## 1. La mettre en ligne (Vercel, gratuit)

C'est l'étape qui transforme ces fichiers en application accessible partout.

1. Va sur **vercel.com**, crée un compte gratuit.
2. Clique sur **Add New… → Project → Deploy without Git**.
3. Fais glisser le dossier `wifizone-app` complet.
4. Vercel te donne une adresse du type `wifizone-app.vercel.app`.

**Exemple concret :** tu ouvres cette adresse dans Chrome sur ton téléphone,
Chrome propose « Installer l'application », tu acceptes, et l'icône du ticket
apparaît sur ton écran d'accueil. Plus besoin de passer par le navigateur.

> Alternative sans compte : **netlify.com/drop** — tu déposes le dossier, tu as
> l'adresse en 20 secondes.

---

## 2. L'installer sur ton téléphone Android

1. Ouvre l'adresse dans **Chrome**.
2. Appuie sur le bouton orange **« Installer sur mon téléphone »** en haut.
   S'il n'apparaît pas : menu ⋮ → **Ajouter à l'écran d'accueil**.
3. L'app s'ouvre en plein écran, sans barre d'adresse.

Une fois installée, elle s'ouvre même sans connexion. Seuls les liens vers les
formations (YouTube, sites) ont besoin d'internet — ce qui est normal.

---

## 3. La publier sur Google Play (optionnel)

Pour un vrai fichier `.aab` acceptable par le Play Store :

1. Va sur **pwabuilder.com**.
2. Colle l'adresse de ton app.
3. Clique **Package for stores → Android**.
4. Télécharge le paquet et dépose-le sur la Google Play Console
   (compte développeur : 25 USD une seule fois).

**Exemple concret :** utile si tu veux plus tard vendre l'accès à ce parcours
à d'autres jeunes qui montent leur WiFi zone à Douala.

---

## 4. Modifier le contenu

Tout est dans `index.html`, en haut du bloc `<script>` :

- `MODULES` — les 7 étapes du parcours.
- `R` — la liste des formations. Pour en ajouter une, copie une ligne existante :

```js
{id:"p12", tab:"parcours", m:3, titre:"Titre de la formation",
 src:"Nom de la chaîne", lang:"FR", cout:"Gratuit",
 desc:"Une phrase qui dit à quoi ça sert.",
 url:"https://..."}
```

- `m:` = le numéro du module (0 = module 01, 3 = module 04…).
- `tab:` = `parcours`, `certif` ou `business`.
- `KIT` — la liste du matériel et les fourchettes de prix en FCFA.

Après modification, redépose le dossier sur Vercel ou Netlify.

---

## 5. Sauvegarder ta progression

Ta progression, tes notes et ton budget restent sur ton appareil uniquement.
En bas de l'app : **Exporter** crée un fichier `wifizone-progression.json`,
**Importer** le restaure. Fais-le avant de changer de téléphone.
