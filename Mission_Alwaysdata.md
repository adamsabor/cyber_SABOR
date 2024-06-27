## Mission 0 : Déploiement sur un serveur distant avec AlwaysData 
 [SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT
 Bloc3 (BTS - SIO) 17/04/2024










## Etape 0 : Créer un espace sur Alwaysdata

Créer un compte sur Alwaysdata gratuit (100 Mo).

1)Quels services sont offerts par Alwaysdata ?   
Alwaysdata propose de l'hebergement web pour plusieurs langageet base de données


2) Quels services seront nécessaires pour déployer un site web (HTML, CSS, JS et PHP) ?

- Hébergement Web : Pour stocker et servir les fichiers de mon site.

- Accès FTP : Pour uploader vos fichiers sur le serveur.

3) Quel est le nom de domaine choisi pour le déploiement de votre site ? (**Attention** : choisir un nom sans `-`(tiret du 6)).   
SaborTech
 
## Etape 1 : Activer SSH

Pour ajouter les fichiers de votre site web à votre espace, il faut activer votre accès ssh.

1. Expliquer l'intérêt du protocole SSH. Sur quel port est-il actif par défaut ?   

- Intérêt du protocole SSH : SSH (Secure Shell) est un protocole réseau qui permet une communication sécurisée entre deux systèmes via un réseau non sécurisé. Il sert principalement à accéder à distance à des serveurs, exécuter des commandes, et transférer des fichiers, tout en assurant la confidentialité et l'intégrité des données.

2- Quel autre protocole semble avoir les mêmes fonctionnalités ? Que fait SSH qui n'est pas possible avec le 2e ?      

- SSH et FTPS sont deux protocoles utilisés pour le transfert de fichiers de manière sécurisée. Tous deux chiffrent la connexion pour protéger les données transférées.  en revanche FTPS, se limite principalement au transfert de fichiers et ne supporte pas ces fonctionnalités avancées.

3- Activer un accès au serveur via ce protocole. Quelles étapes sont nécessaires ?      

-  j'ai du cherche la cle publique a l'aide du terminal et la copier dans alwaysdata j'ai trouver cela **ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIMVZTa+x4gDTqi1OFBlShSRL3+vJD+8KY45ELzIcDXid saboradam@MacBook-Air-de-sabor.local**


4- Se connecter à votre espace dédié sur le serveur via ce protocole. Quelle est la ligne de commande nécessaire pour y arriver ?  
 
ssh adamsabor@ssh-adamdev.alwaysdata.net

  
  5- Dans quel repertoire faut-il déposer vos fichiers du site si vous voulez le voir en ligne ? (chemin complet sur le serveur)    
   
- /home/sabordev/ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIMVZTa+x4gDTqi1OFBlShSRL3+vJD+8KY45ELzIcDXid saboradam@MacBook-Air-de-sabor.local

## Etape 2 : Copier notre contenu sur Alwaysdata

Ajouter les fichiers du site sauvegardé en local au répertoire distant dédié.

1 - Quel est le chemin local absolu pour accéder à votre site ?  

- /Users/saboradam/Desktop/MonSite

2 - Quel est le chemin absolu du repertoire dédié sur le serveur    Alwaysdata ?   

- /home/sabordev/. 
 
3- Les commandes `scp` et `rsync` peuvent être d'une grande aide à cette étape. Pourquoi ? 

-  scp (secure copy) permet de copier des fichiers de manière sécurisée entre des machines sur un réseau en utilisant le protocole SSH.
rsync est utilisé pour synchroniser des fichiers et des répertoires entre deux emplacements sur un réseau de manière efficace, en transférant uniquement les modifications.
Ces commandes sont utiles pour transférer vos fichiers du site local au serveur de manière sécurisée et efficace.

4- Quelle est la différence entre les deux commandes ?

- scp copie simplement les fichiers d'un point à un autre et n'offre pas de mécanisme pour la synchronisation des modifications ou la reprise de transferts interrompus.
rsync permet une synchronisation avancée, la reprise de transferts, et optimise les transferts en ne déplaçant que les parties de fichiers qui ont changé.

5- Quelle est la commande complète pour ajouter les fichiers sauvegardés en local sur le serveur dédié ?
	scp -r /Users/saboradam/Desktop/Portfolio saboradam@ssh-sabordev.alwaysdata.net:/home/sabordev/www

- Comment vérifier que l'ajout a bien été effectué ? Détailler la procédure et les résultats attendus.
- Quelle URL permet de voir votre site en ligne ? 

## Etape 3 - Gestion de paires de clés privée et publique

On souhaiterait se connecter avec une paire de clés privée/public au service SSH accessible sur AlwaysData.

Voici des liens pour vous y aider : 
- <https://www.remipoignon.fr/authentification-ssh-par-cle-privee/>

- Expliciter dans vos mots ce principe d'authentification
- Notez les avantages à se connecter avec une paire de clé privée et publique vs se connecter avec mot de passe
- Noter les étapes nécessaires pour y parvenir
- Notez les étapes pour en tester le bon fonctionnement 


## Etape 4 - Gestion des accès à un dossier privé sur un serveur web

à venir...