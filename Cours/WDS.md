# Windows Deployment Services

## Rôle de WDS

#### Qu'est-ce que WDS ?

Un rôle de serveur Windows pour installer les OS Windows par RSO.

##### Déploiement Microsoft passé par 3 époques

- L'ancien Monde : RIS (Remote Installation Services)
- - Sous Windows 2000/2003
- - Ancêtre du WDS, très rigide, copiait les secteurs de disque de manière brute
- Âge d'or : duo WDS + MDT (2005-2023)
- - WDS servait de tuyau (transport RSO)
- - MDT servait de cerveau (automatisation, pilote ou logiciels)
- Transition actuelle : vers le Cloud
- - 

##### Pourquoi le WDS en 2026 ?

Même si MDT s'efface, le WDS reste vital :
- Infra locale : en environnement isolé d'Internet (Usine, banque, défense)
- ????

##### PXE (Preboot eXection Environment)

C'est un standard permettant à une station de démarrer depuis le RSO avant même d'avoir un OS sur le disque

Fonctionnement :
- Le client envoie une requête DHCP "Discovery"
- Le server DHCP répond avec une IP et les "Options PXE"
- Le client contacte le server WDS pour download le programme d'amorce

#### Besoin du WDS

- ADDS : Pour approbation des machines, gestion de comptes,
- DNS ???
- DHCP ???
- Stockage : partition NTFS dédiée au stockage d'images

## Installation

