# Documentation de l'API

Cette documentation décrit toutes les commandes disponibles via l'API.

## Table des Matières

1. [Ajouter un Texte](#ajouter-un-texte)
2. [Voir un Texte](#voir-un-texte)
3. [Modifier le Titre d'un Texte](#modifier-le-titre-dun-texte)
4. [Modifier le Contenu d'un Texte](#modifier-le-contenu-dun-texte)
5. [Supprimer un Texte](#supprimer-un-texte)

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

Utilisez ces commandes pour interagir avec les textes du site et réaliser des opérations telles que l'ajout, la modification et la suppression de textes.
