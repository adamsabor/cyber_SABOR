
## OWASP_Mission1
[SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT  
Bloc3 (BTS - SIO) 13/06/2024

### Q1

#### J'ai configuré burp comme demandée mais malheureusement il est entré en conflit avec mon navigateur
![Capture d’écran 2024-06-13 à 17 45 53](https://github.com/adamsabor/cyber_SABOR/assets/156083054/8e38573d-63e4-485d-b62e-f3552ded47a9)


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
	![Capture d’écran 2024-06-13 à 17 45 53](https://github.com/adamsabor/cyber_SABOR/assets/156083054/8e38573d-63e4-485d-b62e-f3552ded47a9)
	



### Q3. Positionner le niveau de sécurité du code à 0 (Hosed)

1. **Sur la page d'accueil de Mutillidae :**
   - J'ai cherché le lien "Toggle Security" et cliqué dessus pour définir le niveau de sécurité à "0 (Hosed)".
   
<img width="834" alt="Capture d’écran 2024-06-13 à 20 50 19" src="https://github.com/adamsabor/cyber_SABOR/assets/156083054/55ef4588-c4a4-48b7-a6b5-2e158983d0fb">

## Découverte de la Sensibilité SQLi

### Q1. Tester une détection manuelle de la sensibilité SQLi

1. **Accéder à la page de connexion :**
   - J'ai vérifié que le niveau de sécurité est réglé à 0 (Hosed).
   - J'ai saisi sa (') dans le champ mot de passe.
   - J'ai cliqué sur le bouton "Login".![Capture d’écran 2024-06-27 à 17 59 20](https://github.com/adamsabor/cyber_SABOR/assets/156083054/39c99ed2-a36b-4570-afe6-34001b3937fd)


2. **Observer l'erreur SQL :**
   - Une erreur SQL est apparue, on peut voir "exception occurred" et aussi le message en haut de la page, donc il y a des failles.![Capture d’écran 2024-06-27 à 18 02 16](https://github.com/adamsabor/cyber_SABOR/assets/156083054/51c90be4-61fc-41e9-8de2-fe4d4a44f201)

   

## À vous de jouer

### Premier Défi : Extraction de Données

1. **Accéder à la page d'extraction de données :**
   - J'ai navigué vers OWASP 2017 


2. **Tester une injection SQL :**
   - Dans le champ du nom d'utilisateur, j'ai mis : admin.
   - Dans le champ du mot de passe, j'ai mis : ' or username='admin.
   - J'ai obtenu cette liste donc cela a fonctionné :
   
     ![Capture d’écran 2024-06-27 à 18 07 01](https://github.com/adamsabor/cyber_SABOR/assets/156083054/83794852-b696-43a4-9cca-9db52b5c6463)
  - donc cela a fonctionné


### Deuxième Défi : Passer Outre l'Authentification

1. **Accéder à la page de connexion :**
   - J'ai navigué vers OWASP 2017 > A1 – Injection (SQL) > SQLi – Bypass Authentication > Login.



2. **Tester une injection SQL :**
   - Dans le champ du nom d'utilisateur, j'ai entré : admin.
   - Dans le champ du mot de passe, j'ai entré : ' or username='admin.
   - J'ai cliqué sur "Login" pour m'authentifier en tant qu'administrateur.
   - J'ai obtenu cela :
![Capture d’écran 2024-06-27 à 18 08 08](https://github.com/adamsabor/cyber_SABOR/assets/156083054/443bd91b-f866-4992-8fb4-3f1260c4988d)



- j'ai reussi a me connecter a admin comment on peut le voir en haut a gauche


#### Reporter sur votre documentation les injections testées
- Injection pour l'extraction de données : ' or ('a' = 'a') or '.
- Injection pour passer outre l'authentification : ' or username='admin.

## Contre-mesures

### Q1. Modifier le niveau de sécurité et vérifier que les tests d'exploitation des failles SQLi échouent

1. **Modifier le niveau de sécurité :**
   - J'ai cliqué sur le lien "Toggle Security" pour augmenter le niveau de sécurité.
   


2. **Tester à nouveau les injections :**
   - J'ai réessayé les injections précédentes pour vérifier qu'elles échouent. Effectivement, elles ont bien échoué.



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

