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
```
[Insérez ici une capture d'écran de la configuration de l'extension Wsdler et de la sécurité à 0]
```

### Q2. Tester un exemple de requête et de réponse à l’aide d’un login non valide en réalisant les manipulations décrites dans l’étape n°2 (parse de la page WSDL, envoi au répéteur, génération de la réponse et envoi au comparateur).

**Réponse :**
1. **Tester un login non valide :**
   - J'ai ouvert la page "Username Enumeration" : OWASP 2017 => A2 : Broken Authentication and Session Management => Username Enumeration => Lookup User (SOAP Web Service).
   - J'ai positionné le proxy à "intercept on" dans BurpSuite et cliqué sur "View the WSDL".
   - J'ai fait un clic droit dans la fenêtre de capture et sélectionné "Extensions > Wsdler > Parse WSDL".
   - J'ai cliqué sur "getUser" et observé le code de la requête.
   - J'ai envoyé cette requête au "Repeater" de BurpSuite.
   - J'ai cliqué sur "Send" pour observer la réponse et l'envoyer au "Comparer".

#### Capture de la requête et réponse pour un login non valide :
```
[Insérez ici une capture d'écran de la requête et réponse pour un login non valide]
```

### Q3. Tester un exemple de requête et de réponse à l’aide d’un login valide en réalisant les manipulations décrites dans l’étape n°3 (parse de la page WSDL, envoi au répéteur, modification avec un login valide, génération de la réponse et envoi au comparateur).

**Réponse :**
1. **Créer des utilisateurs :**
   - J'ai créé deux utilisateurs sous Mutillidae nommés "utilisateur1" et "utilisateur2".

2. **Tester un login valide :**
   - J'ai répété les manipulations précédentes avec un login valide.
   - J'ai comparé les réponses obtenues entre un login valide et un login inexistant.

#### Capture de la réponse pour un login valide :
```
[Insérez ici une capture d'écran de la réponse pour un login valide]
```

### Q4. Créer un dictionnaire de login sur votre machine cliente. Pour cela, ouvrir un éditeur de texte et saisir des logins les uns en dessous des autres et enregistrer votre fichier.

**Réponse :**
1. **Créer un dictionnaire de login :**
   - J'ai ouvert un éditeur de texte et saisi des logins les uns en dessous des autres. Puis, j'ai enregistré le fichier.

### Q5. Lancer l’énumération et relever les logins valides en réalisant les manipulations décrites dans l’étape n°4.

**Réponse :**
1. **Lancer l’énumération :**
   - Dans l'onglet Repeater de BurpSuite, j'ai envoyé la requête avec un login correct à l'Intruder.
   - J'ai sélectionné la valeur du login comme variable dans l'onglet "Positions".
   - J'ai chargé le dictionnaire de login dans l'onglet "Payload".
   - J'ai ajouté un filtre pour détecter les logins corrects (chaîne de caractère "Results for").
   - J'ai lancé l'attaque en cliquant sur "Start Attack".

#### Capture des résultats de l'énumération des logins :
```
[Insérez ici une capture d'écran des résultats de l'énumération des logins]
```

### Q6. A l’aide du comparateur, expliquer quelles sont les lignes de la réponse sur lesquelles l’attaquant a pu s’appuyer pour lancer l’attaque ?

**Réponse :**
1. **Analyse des réponses :**
   - J'ai utilisé le comparateur de BurpSuite pour comparer les réponses entre un login valide et un login inexistant.
   - Les différences dans les messages affichés ont permis d'identifier les logins valides. Les réponses contenant la chaîne de caractère "Results for" indiquent un login valide.

#### Capture des résultats de l’analyse :
```
[Insérez ici une capture d'écran des résultats de l’analyse]
```

### Travail à faire 2 : Énumération des logins en mode sécurisé et analyse du code source

#### Q1. Fermer puis relancer BurpSuite. Positionner le niveau de sécurité à 5 et relancer l’attaque en suivant les étapes 2 à 4.

**Réponse :**
1. **Positionner le niveau de sécurité à 5 :**
   - J'ai fermé puis relancé BurpSuite.
   - J'ai positionné le niveau de sécurité à 5 dans Mutillidae.
   - J'ai relancé l'attaque en suivant les étapes 2 à 4 du travail à faire 1.

#### Capture de la configuration de la sécurité à 5 :
```
[Insérez ici une capture d'écran de la configuration de la sécurité à 5]
```

### Q2. Les informations affichées par le comparateur sont-elles exploitables pour tenter une énumération ?

**Réponse :**
1. **Vérification des informations :**
   - J'ai comparé les réponses obtenues avec le comparateur de BurpSuite.
   - En mode sécurisé, les informations affichées ne permettent pas d’identifier les logins valides, rendant l’énumération impossible.

### Q3. Chercher dans le code source de la page `ws-user-account.php` (située dans `/var/www/html/mutillidae/webservices/soap/`) le codage mis en place permettant d’obtenir un encodage sécurisé. Expliquer le rôle de l’instruction EncodeforHTML.

**Réponse :**
1. **Analyser le code source :**
   - J'ai cherché le fichier `ws-user-account.php` situé dans `/var/www/html/mutillidae/webservices/soap/`.
   - L'instruction `EncodeforHTML` encode les caractères spéciaux en entités HTML, empêchant l’injection de code et sécurisant les réponses affichées.

#### Capture du code source analysé :
```
[Insérez ici une capture d'écran du code source analysé]
```

### Conclusion

#### Q1. Quelles sont les observations et les recommandations finales ?

**Réponse :**
1. **Synthèse des observations :**
   - J'ai comparé les versions non sécurisée et sécurisée.
   - J'ai identifié les vulnérabilités corrigées et les bonnes pratiques implémentées.

2. **Recommandations :**
   - J'ai recommandé d'implémenter des contrôles de validation côté serveur.
   - J'ai suggéré l'utilisation de requêtes préparées pour éviter les injections SQL.
   - J'ai conseillé d'encoder les messages de sortie pour éviter qu’un attaquant puisse les exploiter.

#### Capture des recommandations :
```
[Insérez ici une capture d'écran des recommandations]
```
