## OWASP_Mission2A NON FINI
[SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT  
Bloc3 (BTS - SIO) 13/06/2024

### Premier Défi : Énumération des logins

#### Q1. Commencer par installer l’extension Wsdler en réalisant les manipulations décrites dans l’étape n°1. Puis, positionner le niveau de sécurité à 0.

**Réponse :**
1. **Installer l'extension Wsdler :**
   - J'ai lancé BurpSuite et accédé à l'onglet "Extender", puis "Bapp Store".
   - J'ai sélectionné l'extension Wsdler et l'ai installée.

2. **Positionner le niveau de sécurité à 0 :**
   - J'ai accédé à la page d'accueil de Mutillidae.
   - J'ai cliqué sur "Toggle Security" pour définir le niveau de sécurité à "0 (Hosed)".

#### Capture de la configuration de l'extension Wsdler et de la sécurité à 0 :

![Capture d’écran 2024-06-27 à 18 42 59](https://github.com/adamsabor/cyber_SABOR/assets/156083054/61a1b453-bebc-46d8-8387-3c2891211e53)
![Capture d’écran 2024-06-27 à 18 43 58](https://github.com/adamsabor/cyber_SABOR/assets/156083054/ee0eea2b-1e19-426b-92b6-acb30ef46073)



### Q2. Tester un exemple de requête et de réponse à l’aide d’un login non valide en réalisant les manipulations décrites dans l’étape n°2 (parse de la page WSDL, envoi au répéteur, génération de la réponse et envoi au comparateur).

**Réponse :**
1. **Tester un login non valide :**
   - J'ai ouvert la page "Username Enumeration" : OWASP 2017 => A2 : Broken Authentication and Session Management => Username Enumeration => Lookup User (SOAP Web Service).
   - J'ai positionné le proxy à "intercept on" dans BurpSuite et cliqué sur "View the WSDL".
   - J'ai fait un clic droit dans la fenêtre de capture et sélectionné "Extensions > Wsdler > Parse WSDL".
   - J'ai cliqué sur "getUser" et observé le code de la requête.
   - J'ai envoyé cette requête au "Repeater" de BurpSuite.
   - J'ai cliqué sur "Send" pour observer la réponse et l'envoyer au "Comparer".


![Capture d’écran 2024-06-27 à 21 54 48](https://github.com/adamsabor/cyber_SABOR/assets/156083054/ce9a1324-6815-4394-8327-8a41346b28af)


### Q3. Tester un exemple de requête et de réponse à l’aide d’un login valide en réalisant les manipulations décrites dans l’étape n°3 (parse de la page WSDL, envoi au répéteur, modification avec un login valide, génération de la réponse et envoi au comparateur).

**Réponse :**
1. **Créer des utilisateurs :**
   - J'ai créé deux utilisateurs sous Mutillidae nommés "utilisateur1" et "utilisateur2".

2. **Tester un login valide :**
   - J'ai répété les manipulations précédentes avec un login valide.
   - J'ai comparé les réponses obtenues entre un login valide et un login inexistant.



![Capture d’écran 2024-06-27 à 22 11 31](https://github.com/adamsabor/cyber_SABOR/assets/156083054/9270ca85-ac77-4261-bb83-06b3ed37175f)
![Capture d’écran 2024-06-27 à 22 15 01](https://github.com/adamsabor/cyber_SABOR/assets/156083054/7e718d54-ad0e-4c92-bf33-04ed8381adb4)

### Q4. Créer un dictionnaire de login sur votre machine cliente. Pour cela, ouvrir un éditeur de texte et saisir des logins les uns en dessous des autres et enregistrer votre fichier.

**Réponse :**
1. **Créer un dictionnaire de login :**
   - J'ai ouvert un éditeur de texte et saisi des logins les uns en dessous des autres. Puis, j'ai enregistré le fichier.
![Capture d’écran 2024-06-27 à 22 24 49](https://github.com/adamsabor/cyber_SABOR/assets/156083054/c6750a87-bc96-4301-b913-8739418e1eae)

### Q5. Lancer l’énumération et relever les logins valides en réalisant les manipulations décrites dans l’étape n°4.

**Réponse :**
1. **Lancer l’énumération :**
   - Dans l'onglet Repeater de BurpSuite, j'ai envoyé la requête avec un login correct à l'Intruder.
   - J'ai sélectionné la valeur du login comme variable dans l'onglet "Positions".
   - J'ai chargé le dictionnaire de login dans l'onglet "Payload".
   - J'ai ajouté un filtre pour détecter les logins corrects (chaîne de caractère "Results for").
   - J'ai lancé l'attaque en cliquant sur "Start Attack".

Malheureuresement se message c'est affichait donc je n'ai pas pu voir l'attaque malgré le fait que j'ai realise toute les etapes

```![Capture d’écran 2024-06-27 à 22 45 29](https://github.com/adamsabor/cyber_SABOR/assets/156083054/3f24da61-3daa-4694-ab1e-0356d4e2ffee)


### Q6. A l’aide du comparateur, expliquer quelles sont les lignes de la réponse sur lesquelles l’attaquant a pu s’appuyer pour lancer l’attaque ?

**Réponse :**
1. je n'ai pas pu faire la question comme je ne peux pas faire d'attaque

### Travail à faire 2 : Énumération des logins en mode sécurisé et analyse du code source

#### Q1. Fermer puis relancer BurpSuite. Positionner le niveau de sécurité à 5 et relancer l’attaque en suivant les étapes 2 à 4.

**Réponse :**
1. **Positionner le niveau de sécurité à 5 :**
   - J'ai fermé puis relancé BurpSuite.
   - J'ai positionné le niveau de sécurité à 5 dans Mutillidae.
   - J'ai essayé relancé l'attaque en suivant l' étapes 2 du travail à faire 1. mais je ne peux pas faire le reste comme vu precedemment .

![Capture d’écran 2024-06-27 à 22 50 45](https://github.com/adamsabor/cyber_SABOR/assets/156083054/1e60d597-11bb-401a-a3b9-fcc6b32880ff)

### Q2. Les informations affichées par le comparateur sont-elles exploitables pour tenter une énumération ?

**Réponse :**
je trouve ce message d'erreur que je ne rencotrai pas en toggle 1
![Capture d’écran 2024-06-27 à 22 54 05](https://github.com/adamsabor/cyber_SABOR/assets/156083054/8fad2a85-967d-420a-ad1b-166f75319c56)

### Q3. Chercher dans le code source de la page `ws-user-account.php` (située dans `/var/www/html/mutillidae/webservices/soap/`) le codage mis en place permettant d’obtenir un encodage sécurisé. Expliquer le rôle de l’instruction EncodeforHTML.
**Réponse :**
1. **Analyser le code source :**
   - J'ai cherché le fichier `ws-user-account.php` situé dans `/var/www/html/mutillidae/webservices/soap/`.a l'ai
   - L'instruction `EncodeforHTML` encode les caractères spéciaux en  HTML, sa empêche l’injection de code et sécurise les réponses .



