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



### apres avoir recommencer et reussi a me donner les bon accés voici l'état de mon terminal j'ai du batailler etant donné que j'avais de gros probléme d'accés .
<img width="1080" alt="Capture d’écran 2024-06-13 à 09 52 46" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/2bcdf839-c30c-4ed3-b74a-4d32b295dc85">


j'ai rencontré toute ces erreur avant de configurer la data base  
"arning: fsockopen(): php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known in /home/sabordev/www/mutillidae/src/database-offline.php on line 59

Warning: fsockopen(): Unable to connect to mysql-sabordev.alwaysdata.net/:3306 (php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known) in /home/sabordev/www/mutillidae/src/database-offline.php on line 59

Warning: mysqli::__construct(): php_network_getaddresses: getaddrinfo for mysql-sabordev.alwaysdata.net/ failed: Name or service not known in /home/sabordev/www/mutillidae/src/classes/MySQLHandler.php on line 258

Warning: fsockopen(): Unable to connect to 127.0.0.1:389 (Connection refused) in /home/sabordev/www/mutillidae/src/database-offline.php on line 105"
### j'ai enfin reussi a arriver a cette etape apres avoir configuer ma base de donnée
<img width="1270" alt="Capture d’écran 2024-06-27 à 14 38 58" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/52737e2c-1f2d-4a60-bf54-5f4c03cddeb5">


###  enfin j'ai  installer burp suite 

il se peut que certaine chose soit trouble cela est due au parcours atypique que j'ai du réalisée durant l'installation.
