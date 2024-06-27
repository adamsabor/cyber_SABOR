
## OWASP_Mission1
[SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT  
Bloc3 (BTS - SIO) 13/06/2024

### Q1

#### J'ai configuré burp comme demandée mais malheureusement il est entré en conflit avec mon navigateur
![Capture d’écran 2024-06-13 à 17 45 53](https://github.com/adamsabor/cyber_SABOR/assets/156083054/21a64a72-2fdb-4022-9c7c-438c38abd063)

#### Je suis donc passé sur Firefox qui est apparemment plus permissif et j'ai téléchargé le certificat Burp pour que cela fonctionne
1. **Configurer le proxy Burp Suite :**
   - J'ai ouvert Burp Suite et créé un projet temporaire en utilisant les paramètres par défaut.
   - J'ai cliqué sur l'onglet "Proxy" puis sur "Options".
   - J'ai noté l'adresse IP et le port par défaut (127.0.0.1 et port 8080)
   
   2. **Configurer le navigateur pour utiliser Burp Suite comme proxy :**
   - J'ai accédé aux paramètres réseau et configuré le proxy manuel avec l'adresse IP et le port de Burp     	Suite.

3. **Capturer les requêtes de connexion :**
   - J'ai activé le proxy dans Burp Suite en cliquant sur "Intercept is off" pour le changer en "Intercept 	is on".
   - J'ai accédé à la page de connexion sur Mutillidae et saisi un nom d'utilisateur et un mot de passe 	fictif.
   - J'ai cliqué sur "Login" et observé la requête interceptée dans Burp Suite.
   - J'ai cliqué sur "Forward" pour voir les paramètres de la requête, révélant les noms des champs de 	formulaire.
	#### Voilà ce que Burp intercepte de mon Mutillidae après avoir simulé un login et mot de passe
	![Capture d’écran 2024-06-13 à 20 31 01](https://github.com/adamsabor/cyber_SABOR/assets/	156083054/01a8fd51-bcf3-4a4c-82b1-28df82dc7b0e)



### Q3. Positionner le niveau de sécurité du code à 0 (Hosed)

1. **Sur la page d'accueil de Mutillidae :**
   - J'ai cherché le lien "Toggle Security" et cliqué dessus pour définir le niveau de sécurité à "0 (Hosed)".
   
<img width="834" alt="Capture d’écran 2024-06-13 à 20 50 19" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/55ef4588-c4a4-48b7-a6b5-2e158983d0fb">

## Découverte de la Sensibilité SQLi

### Q1. Tester une détection manuelle de la sensibilité SQLi

1. **Accéder à la page de connexion :**
   - J'ai vérifié que le niveau de sécurité est réglé à 0 (Hosed).
   - J'ai saisi sa (') dans le champ mot de passe.
   - J'ai cliqué sur le bouton "Login".

<img width="1219" alt="Capture d’écran 2024-06-13 à 20 51 37" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/3bdb8484-74ec-4ee1-8581-f7bc83bcc854">

2. **Observer l'erreur SQL :**
   - Une erreur SQL est apparue, on peut voir "exception occurred" et aussi le message en haut de la page, donc il y a des failles.
   
<img width="644" alt="Capture d’écran 2024-06-13 à 20 54 17" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/b132dda3-4069-4200-8b35-3a028dc67b33">

![Capture d’écran 2024-06-13 à 20 55 29](https://github.com/adamsabor/cyber_SABOR/assets/156083054/5d8d12ca-31ac-4a6b-a73d-f8c5467ca46b)

## À vous de jouer

### Premier Défi : Extraction de Données

1. **Accéder à la page d'extraction de données :**
   - J'ai navigué vers OWASP 2017 dans cette page.
   
![Capture d’écran 2024-06-13 à 20 59 20](https://github.com/adamsabor/cyber_SABOR/assets/156083054/bf02069b-0635-41ef-9676-3db0726bfec6)

2. **Tester une injection SQL :**
   - Dans le champ du nom d'utilisateur, j'ai mis : admin.
   - Dans le champ du mot de passe, j'ai mis : ' or username='admin.
   - J'ai obtenu cette liste donc cela a fonctionné :

![Capture d’écran 2024-06-13 à 21 13 42](https://github.com/adamsabor/cyber_SABOR/assets/156083054/b9f246c7-f869-402a-b417-cb67c7a9abaa)

### Deuxième Défi : Passer Outre l'Authentification

1. **Accéder à la page de connexion :**
   - J'ai navigué vers OWASP 2017 > A1 – Injection (SQL) > SQLi – Bypass Authentication > Login.

![Capture d’écran 2024-06-13 à 21 14 59](https://github.com/adamsabor/cyber_SABOR/assets/156083054/8ca27412-1c18-4741-9d10-e9befffa4843)

2. **Tester une injection SQL :**
   - Dans le champ du nom d'utilisateur, j'ai entré : admin.
   - Dans le champ du mot de passe, j'ai entré : ' or username='admin.
   - J'ai cliqué sur "Login" pour m'authentifier en tant qu'administrateur.
   - J'ai obtenu cela :

![Capture d’écran 2024-06-13 à 21 15 57](https://github.com/adamsabor/cyber_SABOR/assets/156083054/66a7246b-66c3-457d-be16-06c1bd9235a1)

- Cette erreur indique que la syntaxe SQL est incorrecte.
- Cela montre que l'application ne valide pas correctement les entrées, ce qui permet les injections SQL.

#### Reporter sur votre documentation les injections testées
- Injection pour l'extraction de données : ' or ('a' = 'a') or '.
- Injection pour passer outre l'authentification : ' or username='admin.

## Contre-mesures

### Q1. Modifier le niveau de sécurité et vérifier que les tests d'exploitation des failles SQLi échouent

1. **Modifier le niveau de sécurité :**
   - J'ai cliqué sur le lien "Toggle Security" pour augmenter le niveau de sécurité.
   
![Capture d’écran 2024-06-13 à 21 23 08](https://github.com/adamsabor/cyber_SABOR/assets/156083054/06b1253e-972a-4133-a90a-dca1892e4cdc)

2. **Tester à nouveau les injections :**
   - J'ai réessayé les injections précédentes pour vérifier qu'elles échouent. Effectivement, elles ont bien échoué.

![Capture d’écran 2024-06-13 à 21 25 13](https://github.com/adamsabor/cyber_SABOR/assets/156083054/a3506db1-4f52-42da-9bc1-81e00d6f436d)
![Capture d’écran 2024-06-13 à 21 26 22](https://github.com/adamsabor/cyber_SABOR/assets/156083054/c1d614b3-3e18-42be-bf58-02431673974f)

### Répondre aux questions suivantes en utilisant le fichier user-info.php

1. **Quel niveau de sécurité est nécessaire pour protéger contre cette attaque ?**
   - Un niveau de sécurité qui implémente des contrôles de validation côté serveur.

2. **À ce niveau, quels sont les contrôles réalisés ?**
   - Les contrôles incluent la validation des entrées et l'utilisation de requêtes préparées.

3. **Est-ce que le contrôle HTML aurait suffi à protéger contre cette injection SQL ?**
   - Non, les contrôles HTML ne suffisent pas, car

 les attaques SQLi se produisent côté serveur.

4. **Comment la validation JavaScript est-elle déclenchée ?**
   - La validation JavaScript est déclenchée lors de la soumission du formulaire.

5. **Quels sont les contrôles réalisés par la validation JavaScript ?**
   - Les contrôles incluent la vérification de la longueur et des caractères des champs de formulaire.
+++

