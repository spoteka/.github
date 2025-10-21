<p align="center">
  <img src="https://raw.githubusercontent.com/spoteka/.github/main/profile/logo.png" width="120"/>
</p>

<h1 align="center">Spoteka Sénégal 🇸🇳</h1>

<p align="center">
  <em>L’appli qui redonne vie à tes objets.</em>
</p>



## 🌍 À propos

**Spoteka** est une marketplace mobile locale qui permet aux Sénégalais d’acheter et de vendre facilement des objets d’occasion, en toute confiance et proximité.

Notre mission :  
> Simplifier les échanges de biens entre particuliers, renforcer la confiance et digitaliser le marché de l’occasion au Sénégal.



## 🧩 Nos projets

| Projet | Description | Tech Stack |
|---------|--------------|------------|
| [spoteka-mobile](https://github.com/spoteka/spoteka-mobile) | Application mobile Flutter (Android & iOS) | Flutter, Dart |
| [spoteka-design](https://github.com/spoteka/spoteka-design) | L’identité visuelle et le système de design officiels du projet **Spoteka Sénégal 🇸🇳** | **Material Design 3 (Material You)** de Google
| [spoteka-api](https://github.com/spoteka/spoteka-api) | API & backend | Supabase, Neon (PostgreSQL), Node.js |
| [spoteka-admin](https://github.com/spoteka/spoteka-admin) | Tableau de bord d’administration | React, TailwindCSS |



## 👥 Équipe fondatrice

| Rôle | Nom | Responsabilités |
|------|------|----------------|
| 👩🏽‍💼 **CEO – Idrissa Abdou Maga Mounya** | Direction, stratégie, communication |
| 👨🏾‍💻 **CTO – Ali Houssene Silahi** | Développement, architecture, technique |



## ⚙️ Stack technique

- **Frontend mobile :** Flutter  
- **Backend :** Node.js / Supabase  
- **Base de données :** Neon PostgreSQL  
- **CI/CD :** GitHub Actions  
- **Design :** Figma  
- **Infra :** Railway / Render 


## 📫 Nous contacter

📧 spoteka.sn@gmail.com  
🌐 En développement : [spoteka.app](https://spoteka.app)  
📱 Instagram / TikTok : bientôt disponibles


<p align="center">💡 Spoteka – Redonne vie à tes objets, simplement.</p>



# 🧭 Charte Technique Spoteka  
> **Projet : Spoteka**  
> **Version : 1.0.0**  
> **Date : 2025-10-21**  
> **Rédigée par : Ali Houssene Silahi (CTO Spoteka)**



![Spoteka Banner](https://dummyimage.com/1200x300/00897b/ffffff&text=Spoteka+Technical+Charter)

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/spoteka/backend/ci.yml?label=CI/CD)
![License](https://img.shields.io/badge/license-MIT-blue)
![Python](https://img.shields.io/badge/python-3.11+-brightgreen)
![FastAPI](https://img.shields.io/badge/FastAPI-Framework-009688)
![Style](https://img.shields.io/badge/code%20style-black-000000.svg)


## 🎯 Objectifs

La présente charte définit les **règles techniques et organisationnelles** du projet **Spoteka**,  
pour garantir un code :
- **Lisible** et conforme aux standards Python (PEP8 + Black),
- **Sécurisé** et maintenable dans le temps,
- **Collaboratif**, grâce à un Git Flow clair et un CI/CD automatique.

Elle s’applique à **tous les projets de Spoteka** : backend (FastAPI), frontend (mobile/web) et infrastructure.


## 🧱 Structure Git (Git Flow Spoteka)

### Branches principales

| Branche | Description | Règles |
|----------|--------------|--------|
| `main` | Code de production stable | Merge uniquement depuis `release` |
| `develop` | Intégration des fonctionnalités validées | Merge depuis `feature/*` |
| `release/x.x.x` | Stabilisation avant déploiement | Merge vers `main` + tag version |
| `feature/*` | Nouvelle fonctionnalité ou refactor | Créée depuis `develop` |
| `fix/*` | Correctif mineur | Créée depuis `develop` |
| `hotfix/*` | Correctif critique en production | Créée depuis `main` |

### Nommage standard
```

feature/<module>-<action>
fix/<module>-<bug>
release/<version>

```

**Exemples :**
- `feature/auth-refresh-tokens`
- `feature/listings-upload-images`
- `fix/messages-read-status`
- `release/1.0.0`


## 🧩 Commits et messages

### Format
```

<type>(<scope>): <message clair>

````

**Types autorisés :**
- `feat` : nouvelle fonctionnalité
- `fix` : correction de bug
- `refactor` : amélioration de structure sans changement de logique
- `docs` : documentation
- `test` : ajout ou mise à jour de tests
- `chore` : maintenance, dépendances
- `style` : formatage (Black, isort)
- `perf` : optimisation de performance

**Exemples :**
```bash
feat(listings): implement cursor-based pagination
fix(auth): correct invalid refresh token logic
docs(api): add swagger examples for listings endpoints
````


## 🔁 Pull Requests (PR)

* **1 PR = 1 fonctionnalité complète et testée**
* PR doit contenir :

  * description claire
  * références d’issues (`Fixes #xx`)
  * captures ou exemples si applicable
* Revue obligatoire par **au moins 1 reviewer**
* Tests et lint doivent **passer sur GitHub Actions** avant merge

**Nommage :**

```
[feat] Implement messaging system
[fix] Correct image upload validation
```


## 🧠 Conventions de code (Python / FastAPI)

| Élément        | Standard                                |
| -------------- | --------------------------------------- |
| **Langage**    | Python 3.11+                            |
| **Framework**  | FastAPI                                 |
| **ORM**        | SQLModel (ou SQLAlchemy)                |
| **Style**      | PEP8 + Black                            |
| **Imports**    | isort                                   |
| **Lint**       | Ruff                                    |
| **Typing**     | 100% obligatoire                        |
| **Tests**      | pytest                                  |
| **Docstrings** | Style Google                            |
| **Config**     | via `.env` (jamais de secrets en clair) |

### Exemple :

```python
def create_listing(listing: ListingCreate, db: Session = Depends(get_db)) -> ListingRead:
    """
    Crée une nouvelle annonce.

    Args:
        listing (ListingCreate): Données de l'annonce.
        db (Session): Connexion à la base.

    Returns:
        ListingRead: L'annonce créée.
    """
    ...
```


## 📂 Structure du projet (Backend)

```
app/
 ├── main.py
 ├── core/          # config, sécurité, logging
 ├── models/        # SQLModel ORM
 ├── schemas/       # Pydantic schemas
 ├── routers/       # Routes API (auth, listings, users, etc.)
 ├── services/      # Logique métier
 ├── repositories/  # Abstraction DB
 ├── utils/         # helpers, pagination, exceptions
 ├── workers/       # tâches async (ex: notifications)
 └── tests/         # pytest + factories
```


## 🔐 Sécurité

* **Hash mot de passe** : bcrypt ou argon2
* **JWT access/refresh** avec rotation
* **CORS restreint** aux domaines Spoteka
* **Uploads sécurisés** : max 5 Mo, MIME vérifié
* **Logs structurés** : Loguru + Sentry
* **HTTPS obligatoire** en production
* **Rate-limit** sur login/register
* **Idempotency-Key** pour POST sensibles
* **Aucune donnée sensible dans les logs**


## 🧪 Tests & QA

* Tous les modules doivent avoir des **tests unitaires et d’intégration**
* Dossier `tests/` miroir de `app/`
* Couverture minimale : **80%**
* CI bloque le merge si :

  * Lint ou tests échouent
  * Couverture < 80%


## 🚀 CI/CD (GitHub Actions)

| Étape     | Description                 |
| --------- | --------------------------- |
| 🧹 Lint   | Black + isort + Ruff        |
| 🧠 Type   | mypy                        |
| 🧪 Tests  | pytest (unit + integration) |
| 🐳 Build  | Docker image                |
| 🚀 Deploy | Render / Railway / Fly.io   |

### Branches protégées

* `main` et `develop` ne peuvent pas recevoir de push direct
  → merge uniquement via PR validée et tests réussis


## 🧱 Déploiement

| Environnement  | Branche     | Plateforme     | Accès          |
| -------------- | ----------- | -------------- | -------------- |
| **Production** | `main`      | Render         | CTO uniquement |
| **Staging**    | `release/*` | Render staging | QA             |
| **Dev**        | `develop`   | Docker local   | Tous devs      |


## 📦 Versioning

Utiliser **SemVer (Semantic Versioning)** :

```
MAJOR.MINOR.PATCH
```

| Exemple | Signification           |
| ------- | ----------------------- |
| `1.0.0` | Première version stable |
| `1.1.0` | Nouvelle fonctionnalité |
| `1.1.1` | Correctif sans rupture  |


## 🧾 Documentation

* API auto-documentée via Swagger `/docs`
* Chaque router doit avoir un `summary` + `description`
* Fichiers à maintenir :

  * `README.md` → installation, lancement, env
  * `docs/charte-technique.md` → ce document
  * `SECURITY.md` → pratiques de sécurité
  * `CONTRIBUTING.md` → guide contributeur
  * `.env.example` → variables d’environnement


## 🔎 Code Review Checklist

| Critère          | Exigence                                     |
| ---------------- | -------------------------------------------- |
| ✅ Lisibilité     | Code clair, nommage cohérent                 |
| 🔒 Sécurité      | Pas d’injection, validations présentes       |
| 🧠 Logique       | Aucun effet de bord non prévu                |
| 🧪 Tests         | PR couverte par tests                        |
| 📘 Documentation | Docstring complète                           |
| 🚀 Performance   | Pas de requêtes lourdes, pagination correcte |


## 🧩 Bonnes pratiques Spoteka

* **KISS** – Garde le code simple et explicite
* **DRY** – Ne répète pas le code inutilement
* **Fail Fast** – Lever des erreurs explicites
* **Lisibilité > magie**
* **Commit petit et fréquent**
* **Documentation vivante**
* **Code Review systématique**


## 🧾 Validation avant merge

Avant toute fusion :

1. ✅ Tests passent sur CI/CD
2. ✅ Revue approuvée
3. ✅ Aucune faille de sécurité connue
4. ✅ Code conforme au style Spoteka
5. ✅ Documentation mise à jour


## 📜 Clause finale

> Tout contributeur de Spoteka s’engage à écrire du code :
>
> * clair, testé et documenté,
> * respectant cette charte,
> * et visant l’excellence technique.


### ✍️ Signé par :

| Nom                           | Rôle                          | Signature           |
| ----------------------------- | ----------------------------- | ------------------- |
| **Ali Houssene Silahi**       | CTO / Responsable technique   | ___________________ |
| **Idrissa Abdou Maga Mounya** | CEO / Responsable stratégique | ___________________ |



**© Spoteka 2025 — Tous droits réservés.**
*"Building the future of digital marketplaces in Africa."*

