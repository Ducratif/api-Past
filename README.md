# Documentation de l'API

Cette documentation décrit toutes les commandes disponibles via l'API.

## Table des Matières

1. [Ajouter un Texte](#ajouter-un-texte)
2. [Voir un Texte](#voir-un-texte)
3. [Modifier le Titre d'un Texte](#modifier-le-titre-dun-texte)
4. [Modifier le Contenu d'un Texte](#modifier-le-contenu-dun-texte)
5. [Supprimer un Texte](#supprimer-un-texte)
6. [API Utilisateur](#api-utilisateur)

---

### Ajouter un Texte

Permet d'ajouter un nouveau texte avec son titre.

**URL** : `/api/add_text.php`

**Méthode HTTP** : `POST`

**Paramètres de la Requête** :
- `title` : Le titre du texte.
- `content` : Le contenu du texte.

**Exemple de Requête** :

```bash
curl -X POST http://votresite.com/api/add_text.php \
-H "Content-Type: application/json" \
-d '{"title": "Nouveau Texte", "content": "Contenu du nouveau texte."}'
```

**Réponse en Cas de Succès :**

```json
{
    "message": "Text added successfully"
}
```

### **Voir un Texte**
Permet de visualiser un texte en le recherchant par identifiant ou par titre.

URL : `/api/view_text.php`

Méthode HTTP : `GET`

Paramètres de la Requête :

Soit `id` : L'identifiant du texte à visualiser.
Soit `title` : Le titre du texte à visualiser.

**Exemple de Requête par ID :**
```bash
curl http://votresite.com/api/view_text.php?id=1
```

**Exemple de Requête par Titre :**
```bash
curl http://votresite.com/api/view_text.php?title=Nouveau%20Texte
```

**Réponse en Cas de Succès :**
```json
{
    "id": 1,
    "title": "Nouveau Texte",
    "content": "Contenu du nouveau texte."
}
```

### **Modifier le Titre d'un Texte**
Permet de modifier le titre d'un texte en le recherchant par identifiant.

URL : `/api/update_title.php`

Méthode HTTP : `POST`

Paramètres de la Requête :

`id` : L'identifiant du texte à modifier.
`new_title `: Le nouveau titre du texte.

**Exemple de Requête :**
```bash
curl -X POST http://votresite.com/api/update_title.php \
-H "Content-Type: application/json" \
-d '{"id": 1, "new_title": "Titre Modifié"}'
```

*Réponse en Cas de Succès :*
```bash
{
    "message": "Title updated successfully"
}
```

### **Modifier le Contenu d'un Texte**
Permet de modifier le contenu d'un texte en le recherchant par identifiant.

URL : `/api/update_text.php`

Méthode HTTP : `POST`

Paramètres de la Requête :

`id` : L'identifiant du texte à modifier.
`new_content` : Le nouveau contenu du texte.

**Exemple de Requête :**
```bash
curl -X POST http://votresite.com/api/update_text.php \
-H "Content-Type: application/json" \
-d '{"id": 1, "new_content": "Contenu Modifié"}'
```

**Réponse en Cas de Succès :**
```json
{
    "message": "Content updated successfully"
}
```


### **Supprimer un Texte**
Permet de supprimer un texte en le recherchant par identifiant.

URL : `/api/delete_text.php`

Méthode HTTP : `POST`

Paramètres de la Requête :

`id` : L'identifiant du texte à supprimer.
**Exemple de Requête :**
```bash
curl -X POST http://votresite.com/api/delete_text.php \
-H "Content-Type: application/json" \
-d '{"id": 1}'
```

**Réponse en Cas de Succès :**
```json
{
    "message": "Text deleted successfully"
}
```


### **API Utilisateur**
Voici un cadeau. Du fait que j'ai ajouter un system de connexion, j'ai aussi fait une API pour que vous puissiez augmenter votre utilisation avec cette fonctionnalité que je vous propose.


**Structure du Projet**

```arduino
votre_dossier/
├── api/
│   ├── register.php
│   ├── login.php
│   ├── change_pin.php
│   ├── get_user_info.php
├── db.php
└── sql/
    └── database.sql
```



**Endpoints RESTful :**

`register.php:` Inscription d'un nouvel utilisateur avec les informations fournies.
`login.php:` Connexion de l'utilisateur avec vérification du mot de passe.
`change_pin.php:` Modification du PIN de l'utilisateur après vérification du mot de passe.
`get_user_info.php:` Récupération des informations de l'utilisateur (sauf le mot de passe et le PIN).


**Sécurité et Validation :**

Utilisation de `password_hash` et `password_verify` pour sécuriser les mots de passe.
Utilisation de JSON pour la communication entre le client et le serveur.


**Gestion des Erreurs :**

Réponses JSON avec des messages d'erreur clairs pour faciliter le débogage et l'intégration côté client.
Utilisation de l'API
Pour tester cette API, vous pouvez utiliser des outils comme curl ou des clients REST comme Postman.

**Exemple de Requête d'Inscription avec curl**
```sh
curl -X POST http://your-server/api/register.php \
-H "Content-Type: application/json" \
-d '{"username": "testuser", "email": "testuser@example.com", "password": "password123", "pin": "1234"}'
```


**Exemple de Requête de Connexion avec `curl`**
```sh
curl -X POST http://your-server/api/login.php \
-H "Content-Type: application/json" \
-d '{"username": "testuser", "password": "password123"}'
```


**Conclusion**
Cette API vous offre une base pour interagir avec les données utilisateur de votre site. Vous pouvez étendre cette API pour inclure d'autres fonctionnalités, comme la gestion des fichiers à télécharger, en utilisant des endpoints supplémentaires. Assurez-vous d'ajouter des mesures de sécurité adéquates avant de déployer en production.


Utilisez ces commandes pour interagir avec les textes du site et réaliser des opérations telles que l'ajout, la modification et la suppression de textes.
