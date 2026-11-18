# GLPI
Gestionnaire Libre de Parc Informatique  

## Définition
Outil OpenSource de gestion des Services Informatiques (Information Technology Service Management), du helpdesk et du suivi des actifs.  
Regroupe sur une seule plateforme les demandes, flux de travail, les actifs et le support.  
Disponible en version auto-hébergée, ou en Cloud (GLPI Network)

## Objectifs

### Multi facteurs
- Organiser le support et traiter les incidents et demandes selon processus ITIL
- Inventaire : vision complète et à jour du parc
- Relier inventaire des actifs au helpdesk pour savoir quel équipement est concerné par quel ticket
- Piloter budget, contrat, fournisseur, licence
- Administrer user, groupes et droits d'accès

### Piliers
- HELPDESK : traitement incident/demande
- INVENTAIRE : Automatisé via Agent GLPI
- GESTION : Financère et contractuelle

### Axes de travail

#### Gestion des actifs
- Permet de gérer inventaire des actifs matériels et logiciels tels que les PC, périphériques, logiciels installés, licences, etc...
- Permet de suivre les détails des actifs, leur localisation, leur état, historique, et infos pertinentes.

#### Gestion des tickets
- Système de gestion des tickets pour suivi de demandes d'assistance technique, incidents, problèmes etc...
- Permet de gérer les flux de travail, prioriser les tickets, assigner les tâches, suivre l'état de résolution, communiquer avec les users.

#### Gestion de contrats
- Permet de gérer les contrats liés aux actifs informatiques, tels que les contrats de maintenance, garantie, location, etc...
- Permet de suivre les détails des contrats, dates d'expiration, conditions, et générer des rappels automatiques.

#### Gestion des stats et reporting
- Propose des fonctionnalités de reporting et de génération de stats pour analyser les data relatives aux actifs
- Permet de suivre les perfs, identifier les tendances, évaluer l'utilisation des ressources.

#### Gestion des users
- Permet de créer une hiérarchie locale entre N1, N2, Nx et les admins/superviseurs
- Prend en charge le LDAP (*Lightweight Directory Access Protocol*) avec l'AD
- GLPI devient un tableau de bord de travau quotidien

## Installation

### Pile LAMP
- Installation des paquets nécessaires au LAMP : Linux, Apache2, MariaDB, PHP

### Installation et paramétrage de la base de données
- Initialisation sécurisée de MariaDB
- Création database GLPI
- Création d'un user full privileges sur cette database

### Download de ?????????