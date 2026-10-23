# Information Technology Infrastructure Library
## Simple, cékoi?
Registre des bonnes pratiques au sein d'un système informatique.  
Repose sur **4 piliers** :
- Stratégie
- Gestion de services
- Valeur pour les parties prenantes
- Haute vélocité dans l'IT
## 5 étapes du cycle de vie d'un Service
1. Stratégie des services
    - Définit la perspective, la position les plans et les modèles qu'un fournisseur de service doit exécuter pour atteindre les résulats attendus par l'organisation
2. Conception des services
    - Comprend la conception des services, les pratiques de gouvernances et les process/politiques nécessaires pour réaliser la strat du fournisseur de service et pour faciliter l'introduction des services dans les environnements pris en charge.
3. Transition des services
    - Garantit que les services nouveaux, modifiés ou désactivés répondent aux attentes de l'organistion telles que documentées.
4. Exploitation des services
    - Coordonne et réalise les activités et les process requis pour fournir les services aux users et clients à des lvl de services convenus et pour les gérer. L'exploitati° des services gère aussi la technologie qui est utilisée pour fournir et soutenir les services.
5. Amélioration continue des services (CSI : Continual Service Improvement)
    - Garantit que les services sont alignés sur les besoins changeants de l'organisation en identifiant et en apportant des améliorations aux services informatiques qui soutiennent les process commerciaux.
## Concept clefs de la gestion des services IT
*Ensemble de rôles, fonctions et process mises en oeuvre pour fournir de la valeur au clients*  
- Valeur et Co-création
- Gestion des relations de services
- Valeur : résultats, coûts et risques
### 7 principes directeurs
1. Privilégier la valeur
2. Commencer là où on est
3. Avancer par itération avec des retours
4. Collaborer et promouvoir la visibilité
5. Penser et travailler de façon holistique
6. Opter pour la simplicité et la praticité
7. Optimiser et Automatiser
## GLPI  (Gestionnaire Libre de Parc Informatique)
### Gestion des actifs
- Permet de gérer l'inventaire des actifs matériels et logiciels tels que les ordinateurs, periphériques, licences, etc...
- Permet de suivre les détails des actifs, leur localisation, état, historique et informations pertinentes
### Gestion des tickets
- Système de gestion de tickets pour suivre les demandes d'assistances technique, les incidents, les problèmes et les demandes de service.
- Permet de gérer les flux de travail, prioriser les tickets, assigner les tâches, suivre l'état de résolution, et communiquer avec les users
**Nota : La différence entre incident et demande. Un incident est a un impact sur la productivité (panne de RSO, équipement HS, etc...), la demande est un souhait formulé par le user (Besoin d'une souris neuve, casque, etc...)**
### Gestion des contrats
- Permet de gérer les contrats liés aux actifs, tels que les contrats de maintenance, garantie, etc...
- Permet de suivre les détails des contrates, date d'expiration, conditions, rappels automatiques.
### Gestion des connaissances
- Permet de créer une base de connaissances pour stocker et partager des articles, des guides, des process.
- Facilite le partage des bonnes pratiques.
- Permet aux users de trouver des réponses à leurs questions avant de soumettre un ticket.
### Reporting et Stats
- Propose des fonctionnalités de reporting et de génération de statistiques pour analyser les données relatives aux actifs, aux tickets, contrats, etc...
- Permet de suivre les perfs, identifier les tendances, évaluer l'utilisation des ressources, prendre des décisions basées sur les données.
### Add-ONS GLPI
- Agent GLPI : offre les fonctionnalités avancées pour la découverte auto des actifs, gestion des MAJ, surveillance matérielle.
### Cycle de vie d'un ticket GLPI
- Enregistrement
- Classification (urgence du ticket)
- Traitement (recherche de résolution)
- Solution (application de résolution)
- Validation (Confirmation de résolution)
- Clôture