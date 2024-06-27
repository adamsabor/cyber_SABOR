
## OWASP_Mission2A
[SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT  
Bloc3 (BTS - SIO) 13/06/2024

### Premier Défi : Énumération des logins

#### Q1. Configurer Burp Suite et le navigateur

**Question :** Comment ai-je configuré Burp Suite et le navigateur pour capturer les requêtes ?

**Réponse :**
1. **Configurer le proxy Burp Suite :**
   - J'ai ouvert Burp Suite et créé un projet temporaire en utilisant les paramètres par défaut.
   - Ensuite, je suis allé dans l'onglet "Proxy" puis "Options".
   - J'ai noté l'adresse IP et le port par défaut (127.0.0.1 et port 8080).

2. **Configurer le navigateur pour utiliser Burp Suite comme proxy :**
   - J'ai accédé aux paramètres réseau de Firefox et configuré le proxy manuel avec l'adresse IP et le port de Burp Suite.
   - J'ai téléchargé et installé le certificat de Burp Suite dans Firefox pour éviter les conflits.

#### Capture de la configuration du proxy dans Firefox :
```
[Insérez ici une capture d'écran de la configuration du proxy dans Firefox]
```

### Q2. Positionner le niveau de sécurité à 0 (Hosed)

**Question :** Comment ai-je positionné le niveau de sécurité à 0 dans Mutillidae ?

**Réponse :**
1. **Sur la page d'accueil de Mutillidae :**
   - J'ai cherché le lien "Toggle Security" et cliqué dessus pour définir le niveau de sécurité à "0 (Hosed)".

#### Capture de l'interface Mutillidae avec la sécurité à 0 :
```
[Insérez ici une capture d'écran de l'interface Mutillidae avec la sécurité à 0]
```

### Q3. Test d’une requête et d’une réponse sur un login inexistant

**Question :** Comment ai-je testé une requête et une réponse sur un login inexistant ?

**Réponse :**
1. **Accéder à la page "Username Enumeration" :**
   - J'ai navigué vers OWASP 2017 => A2 : Broken Authentication and Session Management => Username Enumeration => Lookup User (SOAP Web Service).
   
2. **Tester un login inexistant :**
   - J'ai positionné le proxy à "intercept on" dans Burp Suite.
   - J'ai cliqué sur "View the WSDL".
   - J'ai fait un clic droit dans la fenêtre de capture et sélectionné "Extensions > Wsdler > Parse WSDL".
   - J'ai cliqué sur "getUser" et observé le code de la requête.
   - J'ai envoyé cette requête au "Repeater" de Burp Suite.
   - J'ai cliqué sur "Send" pour observer la réponse et l'envoyer au "Comparer".

#### Capture de la requête et réponse pour un login inexistant :
```
[Insérez ici une capture d'écran de la requête et réponse pour un login inexistant]
```

### Q4. Test d’une requête et d’une réponse sur un login existant

**Question :** Comment ai-je testé une requête et une réponse sur un login existant ?

**Réponse :**
1. **Créer des utilisateurs :**
   - J'ai créé deux utilisateurs sous Mutillidae nommés "utilisateur1" et "utilisateur2".

2. **Tester un login existant :**
   - J'ai répété les manipulations précédentes avec un login valide.
   - J'ai comparé les réponses obtenues entre un login valide et un login inexistant.

#### Capture de la réponse pour un login valide :
```
[Insérez ici une capture d'écran de la réponse pour un login valide]
```

### Q5. Créer un dictionnaire de login et lancer l’énumération

**Question :** Comment ai-je créé un dictionnaire de login et lancé l’énumération ?

**Réponse :**
1. **Créer un dictionnaire de login :**
   - J'ai ouvert un éditeur de texte et saisi des logins les uns en dessous des autres. Puis, j'ai enregistré le fichier.

2. **Lancer l’énumération :**
   - Dans l'onglet Repeater de Burp Suite, j'ai envoyé la requête avec un login correct à l'Intruder.
   - J'ai sélectionné la valeur du login comme variable dans l'onglet "Positions".
   - J'ai chargé le dictionnaire de login dans l'onglet "Payload".
   - J'ai ajouté un filtre pour détecter les logins corrects (chaîne de caractère "Results for").
   - J'ai lancé l'attaque en cliquant sur "Start Attack".

#### Capture des résultats de l'énumération des logins :
```
[Insérez ici une capture d'écran des résultats de l'énumération des logins]
```

### Q6. Analyser les résultats

**Question :** Quelles sont les lignes de la réponse sur lesquelles l’attaquant a pu s’appuyer pour lancer l’attaque ?

**Réponse :**
1. **Analyse des réponses :**
   - J'ai utilisé le comparateur de Burp Suite pour comparer les réponses entre un login valide et un login inexistant.
   - Les différences dans les messages affichés ont permis d'identifier les logins valides. Les réponses contenant la chaîne de caractère "Results for" indiquent un login valide.

#### Capture des résultats de l’analyse :
```
[Insérez ici une capture d'écran des résultats de l’analyse]
```

### Travail à faire 2 : Énumération des logins en mode sécurisé et analyse du code source

#### Q1. Relancer BurpSuite en mode sécurisé

**Question :** Comment ai-je relancé BurpSuite en mode sécurisé ?

**Réponse :**
1. **Positionner le niveau de sécurité à 5 :**
   - J'ai fermé puis relancé BurpSuite.
   - J'ai positionné le niveau de sécurité à 5 dans Mutillidae.
   - J'ai relancé l'attaque en suivant les étapes 2 à 4 du travail à faire 1.

#### Capture de la configuration de la sécurité à 5 :
```
[Insérez ici une capture d'écran de la configuration de la sécurité à 5]
```

### Q2. Analyser les résultats en mode sécurisé

**Question :** Les informations affichées par le comparateur sont-elles exploitables pour tenter une énumération ?

**Réponse :**
1. **Vérification des informations :**
   - J'ai comparé les réponses obtenues avec le comparateur de Burp Suite.
   - En mode sécurisé, les informations affichées ne permettent pas d’identifier les logins valides, rendant l’énumération impossible.

### Q3. Analyser le code source pour comprendre l’encodage sécurisé

**Question :** Comment ai-je analysé le code source pour comprendre l’encodage sécurisé ?

**Réponse :**
1. **Rechercher le codage dans la page `ws-user-account.php` :**
   - J'ai cherché le fichier `ws-user-account.php` situé dans `/var/www/html/mutillidae/webservices/soap/`.
   - L'instruction `EncodeforHTML` encode les caractères spéciaux en entités HTML, empêchant l’injection de code et sécurisant les réponses affichées.

#### Capture du code source analysé :
```
[Insérez ici une capture d'écran du code source analysé]
```

### Conclusion

**Question :** Quelles sont les observations et les recommandations finales ?

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

