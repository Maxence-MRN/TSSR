# Installation GLPI

## Server Debian
- Créer un server Debian
  - Graphical Install (n'implique pas nécessairement une Interface Graph User)
  - Langue
  - Nom machine
    - Domaine si déjà connu
    - Nom Super-user
    - Nom User
  - Installation sur Disque entier
    - Tout mettre sur une seule partition
    - Terminer le partitionnement
    - "Faut-il appliquer les changement?" **OUI**
  - "Faut-il analyser d'autres supports?" **NON**
  - France
  - Version "deb.debian.org"
  - *Mandataire vide*
    - Suivant
      - En théorie, 11 fichiers s'installent
  - Selection des logiciels
    - Décocher environnement Debian et GNOME
    - Cocher Serveur SSH
  - Installation de GRUB sur main disk ?
    - **OUI**
    - Périphérique d'installation ?
      - /dev/sda **!!! NE SURTOUT PAS SE RATER SUR CETTE SELECTION!!!**
  - Reboot
**Installation OS Linux OK**
- Se logger en root
  - commande : ip a
  - Relever l'@IP
  
## Basculer en machine host
-   cmd
    - commande : ssh nomduprofiluser@adresseIP
        - Se logger avec le profil user créé sur Debian
    - commande : su -
      - Password Super-admin
    - Emploi du gestionnaire de paquet :
      - Commande sur Debian : apt update (Cette commande NE FAIT QUE VERIFIER LES MAJ)
      - Appliquer les updates si requis : apt upgrade
    - 