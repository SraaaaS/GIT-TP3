# ENV.md - Configuration des variables d'environnement

Ce fichier décrit les variables d'environnement nécessaires au bon fonctionnement de l'application.


### Variables d’environnement requises

| Nom de la variable | Description | Valeur par défaut | Obligatoire |
|--------------------|-------------|-------------------|-------------|
| `image`          | Nom de l'image | `null` | Oui |
| `dockerfile`     | Chemin au dockerfile pour construire l'image | `null` | Oui |
| `PORT`           | Port utilisé par le serveur | `8585` |  Oui |
| `DATABASE_URL`   | URL de connexion à la base de données | `postgres://user:pass@localhost:5432/db` |  Oui |
| `API_KEY`        | Clé API pour les services externes | `null` |  Oui |
| `DEBUG_MODE`     | Active le mode debug (`true` ou `false`) | `false` |  Non |


### Chargement des variables

Dans un environnement local, vous pouvez charger ces variables en installant `python-dotenv` :

```bash
 pip install python-dotenv
```

### 📄 Exemple de fichier `.env`

Un fichier `.env.example` est fourni pour vous aider à configurer rapidement votre environnement :

```bash
test.env.example
```

### Notes et recommandations
- **Ne jamais commit votre fichier `.env` dans Git:** Ajoutez-le plutot à `.gitignore` 
- Utilisez des gestionnaires de secrets comme AWS Secrets Manager.


