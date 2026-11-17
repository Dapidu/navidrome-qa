# Navidrome QA

Projet de tests (QA) sur [Navidrome](https://github.com/navidrome/navidrome), un serveur de streaming musical open source.

**Version testée : v0.64.2**

## Prérequis

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Git

## Installation

1. Cloner ce dépôt :
   ```bash
   git clone https://github.com/Dapidu/navidrome-qa.git
   cd navidrome-qa
   ```
2. Créer le fichier `.env` à partir du modèle, puis y choisir un mot de passe admin :
   ```bash
   cp .env.example .env
   ```
3. Démarrer Navidrome :
   ```bash
   docker compose up -d
   ```
4. Ouvrir http://localhost:4533 et se connecter avec l'utilisateur `admin` et le mot de passe du fichier `.env`.

Le compte `admin` est créé automatiquement au premier démarrage.

## Commandes utiles

| Action | Commande |
|---|---|
| Démarrer | `docker compose up -d` |
| Arrêter | `docker compose down` |
| Voir le journal | `docker compose logs -f` |
| Repartir de zéro | `docker compose down`, supprimer `navidrome-data/`, puis `docker compose up -d` |

## Organisation

| Élément | Rôle | Sur GitHub ? |
|---|---|---|
| `docker-compose.yml` | Décrit le conteneur Navidrome (version fixe 0.64.2) | Oui |
| `.env.example` | Modèle du fichier de configuration | Oui |
| `.env` | Mot de passe admin local | **Non** (secret) |
| `music/` | Fichiers audio à tester (lus par Navidrome) | Non |
| `navidrome-data/` | Base de données et cache de Navidrome | Non |
| `navidrome-src/` | Code source de Navidrome, à cloner à part (voir ci-dessous) | Non |

### Code source (facultatif)

Pour consulter le code de la version testée :

```bash
git clone https://github.com/navidrome/navidrome.git navidrome-src
cd navidrome-src
git checkout v0.64.2
```

## Environnement de test

- Navidrome est accessible uniquement depuis la machine locale (`127.0.0.1`).
- Le mot de passe admin est un mot de passe de test, à ne pas réutiliser ailleurs.
