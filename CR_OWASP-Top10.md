

## [SABOR ADAM](mailto:saboradam5@gmail.com), ESIEE-IT Bloc3 (BTS - SIO) 26/04/2024 


## 1. Contrôle d'Accès Défaillant
**C'est quoi ?** : Permettre aux utilisateurs de voir ou faire des choses qu'ils ne devraient pas pouvoir faire sur une application.  
**Que faire ?** : Mettre en place des vérifications pour qui a le droit de faire quoi dès le début du développement de l'application et bien suivre qui accède à quoi.

## 2. Défaillances Cryptographiques
**C'est quoi ?** : La protection insuffisante des données sensibles, comme les informations bancaires, qui ne sont pas bien chiffrées.  
**Que faire ?** : Chiffrer toutes les données importantes, surtout lorsqu'elles sont stockées ou envoyées sur internet.

## 3. Injection
**C'est quoi ?** : Envoyer de mauvaises données à l'application pour lui faire faire des choses non prévues, comme accéder à des données non autorisées.  
**Que faire ?** : Vérifier et nettoyer les données reçues avant de les utiliser.

## 4. Conception Non Sécurisée
**C'est quoi ?** : Ne pas considérer la sécurité dès les premières étapes de la création de l'application.  
**Que faire ?** : Intégrer la sécurité dès le début et tout au long du développement de l'application.

## 5. Mauvaise Configuration de Sécurité
**C'est quoi ?** : Des réglages de sécurité mal configurés qui créent des failles.  
**Que faire ?** : Configurer correctement et mettre à jour régulièrement les systèmes pour qu'ils restent sécurisés.

## 6. Composants Vulnérables et Obsolètes
**C'est quoi ?** : Utiliser des logiciels ou composants anciens ou non sécurisés.  
**Que faire ?** : Garder tous les logiciels à jour et éviter d'utiliser ceux qui sont reconnus comme non sécurisés.

## 7. Défaillances d'Identification et d'Authentification
**C'est quoi ?** : Les systèmes qui vérifient qui vous êtes ne sont pas assez forts, permettant aux intrus de se faire passer pour quelqu'un d'autre.  
**Que faire ?** : Utiliser des méthodes robustes pour vérifier l'identité des utilisateurs, comme l'authentification à deux facteurs.

## 8. Violations de l'Intégrité des Données et du Logiciel
**C'est quoi ?** : Modification inappropriée de données ou de logiciels sans détection.  
**Que faire ?** : Vérifier l'origine et l'intégrité de tout ce qui est téléchargé ou mis à jour.

## 9. Défaillances de Journalisation et de Surveillance
**C'est quoi ?** : Insuffisance de traces ou de surveillance pour détecter ou répondre aux problèmes de sécurité.  
**Que faire ?** : Assurer une bonne surveillance et utiliser des outils d'alerte en cas d'activité suspecte.

## 10. Forgery de Requêtes Côté Serveur (SSRF)
**C'est quoi ?** : Manipulation d'un serveur pour faire des requêtes externes qui peuvent être dangereuses.  
**Que faire ?** : Limiter les requêtes que le serveur peut faire et vérifier leur légitimité.
