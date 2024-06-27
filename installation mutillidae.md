## installation mutillidae
 [SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT
 Bloc3 (BTS - SIO) 13/06/2024


# Configuration de MUTILLIDAE sur Alwaysdata

## Étape 1 : Préparation

### Sur le terminal

#### Connexion via SSH
J'ai ouvert mon terminal et me suis connecté à mon serveur Alwaysdata :
```bash
ssh sabordev@ssh-sabordev.alwaysdata.net
```
![Connexion SSH]( /mnt/data/Capture d’écran 2024-06-12 à 18.40.14.png)

#### Naviguer vers le répertoire de travail
J'ai changé le répertoire pour aller à l'endroit où je voulais installer MUTILLIDAE :
```bash
cd /home/sabordev/www/
```

#### Supprimer le dossier existant (si nécessaire)
J'ai supprimé le dossier `mutillidae` existant pour repartir de zéro :
```bash
rm -rf mutillidae
```

#### Cloner le dépôt GitHub de MUTILLIDAE
J'ai cloné le dépôt MUTILLIDAE depuis GitHub :
```bash
git clone https://github.com/webpwnized/mutillidae.git
```
![Cloner le dépôt]( /mnt/data/Capture d’écran 2024-06-12 à 18.45.02.png)

### Sur Alwaysdata

#### Accéder à l'interface de gestion Alwaysdata
Je me suis connecté à mon compte Alwaysdata via mon navigateur web.

#### Créer une base de données MySQL dédiée et configurer un utilisateur
- Je suis allé dans la section "Bases de données".
- J'ai créé une nouvelle base de données appelée `sabordev_mutillidae`.
- J'ai créé un nouvel utilisateur avec le nom `sabordev_mutilliuser` et le mot de passe `mutillipwd`.
- J'ai donné à cet utilisateur tous les droits sur la base de données `sabordev_mutillidae`.

## Étape 2 : Créer et Configurer la Base de Données

### Sur le terminal

#### Créer le dossier includes si nécessaire
```bash
mkdir /home/sabordev/www/mutillidae/includes
```

#### Créer le fichier database-config.inc
```bash
touch /home/sabordev/www/mutillidae/includes/database-config.inc
```

#### Donner les permissions correctes au fichier database-config.inc
```bash
chmod 644 /home/sabordev/www/mutillidae/includes/database-config.inc
```
![Permissions fichier]( /mnt/data/Capture d’écran 2024-06-12 à 19.00.43.png)

#### Modifier le fichier de configuration pour ajouter les informations de la base de données
J'ai édité le fichier de configuration :
```bash
nano /home/sabordev/www/mutillidae/includes/database-config.inc
```

J'ai ajouté les informations de la base de données dans le fichier :
```php
<?php
// Database configuration
$DB_HOST = 'localhost';
$DB_USER = 'sabordev_mutilliuser';
$DB_PASS = 'mutillipwd';
$DB_NAME = 'sabordev_mutillidae';
?>
```
J'ai sauvegardé et quitté nano en appuyant sur `Ctrl + X`, puis `Y` et `Entrée`.

## Étape 3 : Vérification des Permissions et Fichiers

### Sur le terminal

#### Assurer que les permissions des fichiers et des dossiers sont correctes
```bash
chmod -R 755 /home/sabordev/www/mutillidae
chmod -R 644 /home/sabordev/www/mutillidae/*
```

#### Créer ou modifier le fichier .htaccess
J'ai ouvert le fichier .htaccess :
```bash
nano /home/sabordev/www/mutillidae/.htaccess
```

J'ai ajouté les lignes suivantes pour permettre l'accès :
```apache
Options -Indexes
<Directory "/home/sabordev/www/mutillidae">
    Require all granted
</Directory>
```
J'ai sauvegardé et quitté nano en appuyant sur `Ctrl + X`, puis `Y` et `Entrée`.

## Étape 4 : Vérification de l'Application MUTILLIDAE

### Sur le navigateur

J'ai rechargé l'application et vérifié son fonctionnement en allant à l'adresse :
```bash
https://sabordev.alwaysdata.net/mutillidae
```
![Vérification application]( /mnt/data/Capture d’écran 2024-06-12 à 19.55.23.png)

### Si l'erreur persiste

#### Vérifier les logs du serveur pour plus d'informations
J'ai accédé aux logs du serveur sur Alwaysdata via mon compte Alwaysdata.

## Contact du Support Technique

### Accéder à l'interface de support Alwaysdata

Je me suis connecté à mon compte Alwaysdata.
J'ai trouvé la section "Support" ou "Assistance".
J'ai créé une nouvelle demande d'assistance.

### apres avoir recommencer et reussi a me donner les bon accés voici l'état de mon terminal
<img width="290" alt="Capture d’écran 2024-06-13 à 10 55 15" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/6d7c638b-cd2e-4e35-849c-d00df5234322">
### j'arrive donc dans cette etape de l'installation <img width="1275" alt="Capture d’écran 2024-06-13 à 10 55 47" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/c06c022a-d7c9-4bb6-8eb4-21df5e1dd488">
j'ai suivi ces etapes sur le terminal
<img width="854" alt="Capture d’écran 2024-06-13 à 11 06 27" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/1605c9be-e3d8-49f8-a32c-8eba1d64c6e9">
j'ai rencontré toute ces erreur avant de configurer la data base  
"arning: fsockopen(): php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known in /home/sabordev/www/mutillidae/src/database-offline.php on line 59

Warning: fsockopen(): Unable to connect to mysql-sabordev.alwaysdata.net/:3306 (php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known) in /home/sabordev/www/mutillidae/src/database-offline.php on line 59

Warning: mysqli::__construct(): php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known in /home/sabordev/www/mutillidae/src/classes/MySQLHandler.php on line 258

Warning: fsockopen(): Unable to connect to 127.0.0.1:389 (Connection refused) in /home/sabordev/www/mutillidae/src/database-offline.php on line 105"
### j'ai enfin reussi a arriver a cette etape apres avoir configuer ma base de donnée
<img width="1280" alt="Capture d’écran 2024-06-13 à 11 35 37" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/507a15ee-657f-4dd8-825b-d8c3496cb5c2">

###  enfin j'ai  installer burp suite 
<img width="754" alt="Capture d’écran 2024-06-13 à 11 56 16" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/18cfc486-68f1-405d-9c48-d73e44055e5b">
