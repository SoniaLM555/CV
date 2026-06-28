# CV en ligne - Karim LADHARI

Application web de CV développée avec Symfony 7 et déployée sur Clever Cloud.

## Présentation

CV en ligne développé pour présenter le parcours professionnel de Mr LADHARI.
L'application utilise le système de templates Twig pour générer les vues et Bootstrap 5 pour le design responsive.

## Stack technique

- **Framework** : Symfony 7
- **Moteur de templates** : Twig
- **Frontend** : HTML5, CSS3, Bootstrap 5, Bootstrap Icons
- **Langage** : PHP >= 8.2
- **Déploiement** : Clever Cloud (PaaS)

## Prérequis

- PHP >= 8.2
- Composer
- Un compte Clever Cloud

## Installation en local

```bash
git clone https://github.com/SoniaLM555/CV.git
cd CV
composer install
symfony serve
```

## Déploiement sur Clever Cloud

### 1. Créer l'application

- Créer un compte sur [Clever Cloud](https://www.clever-cloud.com/)
- Créer une nouvelle application PHP
- Connecter le dépôt GitHub

### 2. Configurer les variables d'environnement
Dans l'interface Clever Cloud, ajouter dans "Environnement variables" les variables suivantes et leur valeur:
- APP_ENV=prod
- CC_PHP_VERSION=8
- CC_COMPOSER_VERSION=2

### 3. Créer le fichier de configuration Clever Cloud
Créer `clevercloud/php.json` :
```json
{
  "deploy": {
    "webroot": "/public"
  },
  "hooks": {
    "postBuild": "php bin/console cache:clear --env=prod && php bin/console assets:install"
  }
}
```

### 4. Configurer Apache
Créer `public/.htaccess` :
```bash
DirectoryIndex index.php
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>
```

### 5. Déployer
```bash
git add .
git commit -m "Configuration Clever Cloud"
git push origin main
```

Le déploiement se lance automatiquement à chaque push.

## URL de production
https://app-48315744-af80-44f7-8713-1c52dcfcae28.cleverapps.io/
