# Base RSO

IEEE-> norme 802.3 (Ethernet) et 802.11 (Wifi)
Les normes 802.XX sont les normes RSO issues des trois grandes familles de RSO (LAN, MAN, WAN)

**Modèle OSI (Open System Interconnection) et TCP/IP (Transmission Control Protocol/Internet Protocol)**

- 7 : Application = Data   
- 6 : Présentation = Data
- 5 : Session = Data
- 4 : Transport = Segment (TCP ou DPC)
- 3 : Réseau = Paquet (Routeur)
- 2 : Liaison = Trame (switch)
- 1 : Physique = Bits (câbles)
*Protocol Data Unit est l'unité de chaque couche du modèle (donc Data, Segment, Paquet, Trame et Bits)*

- 4 : Application
- 3 : Transport
- 2 : Internet
- 1 : Accès Réseau
Mémo : Avec Internet Tout Arrive
Alternative : **RITA**


Qu'est-ce que le modèle OSI ? Le processus d'encapsulation des données pour le transit sur le réseau.

## Petit glossaire
- OSI : **Open System Interconnection** - Modèle à 7 couches permettant l'encapsulation des données pour transit. Permet aussi de diagnostiquer un problème RSO.
- TCP/IP : **Transmission Control Protocol/Internet Protocol** - Modèle à 4 couches qui s'oppose au modèle OSI, gérant l'encapsulation des données pour transit. Se résume à une simplification du modèle OSI
- BIOS/UEFI : **Basic Input Output System / Unified Extensible Firmware Interface** - Deux micrologiciels permettant le boot d'un système informatique. La différence réside dans la vitesse de traitement; l'UEFI étant plus moderne, il est plus rapide en fusionnant deux étapes lors du démarrage. L'UEFI bénéficie d'une interface graphique également.
- ISO : **Image System**, il s'agit d'un fichier avec un OS inclut.
- WDS/Déploiement : **Windows Deployment Service** - Service permettant le déploiement d'images système sur les postes clients par RSO. Requiert deux fichiers : boot.wim et install.wim de l'OS désiré.
- Bridged/NAT/Host-Only : Les trois modes de paramètres d'une carte RSO d'une VM. Le mode H.O. ne permet à une VM de communiquer qu'avec les autres VM et la machine hôte. Le NAT (**Network Address Translation**) permet à la VM d'emprunter l'adresse de la machine hôte pour se connecter à Internet. Le mode Bridge donne une adresse propre à la VM, lui permettant d'être considérée comme une machine à part entière, au même titre que la machine hôte.
- Octets/Bits : Unité de poids d'un fichier informatique. C'est également le language de base permettant aux machines de communiquer et de lire les données.
- PXE : **PreBoot eXecution Environment** : permet l'amorçage d'une image de démarrage lors d'un déploiement par RSO.
- DHCP : **Dynamic Host Configuration Protocol** : Service permettant d'attribuer une configuration RSO à une machine cliente selon une étendue (Pool d'@) et un bail.
- MBR/GPT : **Master Boot Record/ Guid Partition Table** : Attribués respectivement au BIOS et à l'UEFI, ce sont les tables de partionnement qui leur sont attribué.
- RUFUS/VENTOY : Outils permettant de rendre une clef bootable pour restauration d'image. Rufus ne permet que d'inscrire un seul iso, Ventoy permet d'en embarquer plusieurs.
- Partition : Un espace de stockage logique alloué dans un disque dur.
- NTFS : **New Technology Files System** : Système de Fichiers de Microsoft, succédant au FAT.
- SHA256 (signature) : Permet de vérifier l'intégrité d'un fichier.
- VMWARE : Logiciel permettant une hypervision de type 1 et 2. Workstation pour type 2 et ESXI pour type 1.
- Windows Server : Un OS dédié à la création et au déploiement de services.
- DNS : **Domain Name System** : Service permettant de résoudre un nom de domaine en @IP et inversement.
- @IP/MAC : Identité d'un équipement RSO. L'@IP est un nom logique sur le RSO, par opposition à l'@MAC qui est un nom physique.
- IEEE 802.3/803.11 : Deux normes régissant le fonctionnement respectif des connections Ethernet et Wifi.
- Gestionnaire de parc informatique : Logiciel permettant de faire de l'inventoring, gestion de licences ou de logiciels. L'exemple le plus répandu est GLPI.