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
      - Pwd profil root
    - Emploi du gestionnaire de paquet :
      - Commande sur Debian : apt update (Cette commande NE FAIT QUE VERIFIER LES MAJ)
      - Appliquer les updates si requis : apt upgrade
      - Possibilité de mettre à jour d'éventuelles dépendances : apt full-upgrade
      - *Une commande pour désinstaller un paquet si nécessaire* : apt purge *nomdupaquet*
    - installer socle Apache 2, MariaDB, PHP
      - commande : apt install apache2 php mariadb-server -y
    - Installation des paquets dévolus au fonctionnement de php
      - commande : apt install php-xml php-common php-json php-mysql php-mbstring php-curl php-gd php-intl php-zip php-bz2 php-apcu -y
      - puis : apt install php-ldap php-fpm php-bcmath -y
    - Paramétrage de MariaDB
      - commande : mariadb-secure-installation
        - Password Super-admin
        - **ATTENTION, Plusieurs question seront posées. Répondre oui à tout, SAUF AU CHANGEMENT DE PWD SUPER-ADMIN!!!**
      - commande : mysql -u root -p
        - Pwd profil root
          - commande : create database glpi;
          - puis : GRANT ALL PRIVILEGES ON glpi.* TO *nomdeuser*@localhost IDENTIFIED BY "*Pwdcréé*";
          - puis : flush privileges;
            - exit
              - retour en root@GLPI
    - Installation GLPI
      - Commande : wget https://github.com/glpi-project/glpi/releases/download/12.0.2/glpi-12.0.2.tgz
      - extraire le fichier téléchargé (c'est une archive)
        - Commande : tar -xzvf glpi-12.0.2.tgz -C /var/www/html
    - Octroi de droits complets sur le dossier
      - commande : chmod 755 -R /var/www/html
    - Changement de propriétaire à son propre profit
      - Commande : chown www-data:www-data -R /var/www/html/
    - Recharger le service
      - systemctl restart apache2 mariadb.service
    - Création et édition d'un fichier GLPI
      - Commande : nano /etc/apache2/sites-available/glpi.conf
          - COMMANDE SUIVANTE, **!PENSER AU CHANGEMENT d'@IP POUR METTRE CELLE DU SERVER GLPI!**
          - <VirtualHost *:80> 
	            ServerName glpi 
	            ServerAlias (172.X.X.X) 
	            DocumentRoot /var/www/html 
	            Alias /glpi /var/www/html/glpi/public 
	            <Directory /var/www/html/glpi/public> 
	                Options -Indexes +FollowSymLinks 
	                Require all granted 
	                RewriteEngine On 
	                RewriteBase /glpi/ 
	                RewriteCond %{REQUEST_FILENAME} !-f 
	                RewriteCond %{REQUEST_FILENAME} !-d 
	                RewriteRule ^ index.php [QSA,L] 
                </Directory> 
                <FilesMatch \.php$> 
	                SetHandler "proxy:unix:/run/php/php8.4-fpm.sock|fcgi://localhost" 
                </FilesMatch> 
            	ErrorLog ${APACHE_LOG_DIR}/glpi_error.log 
            	CustomLog ${APACHE_LOG_DIR}/glpi_access.log combined 
            </VirtualHost>
      - Save dans nano
        - CTRL + O 
          - Entrer
      - Quitter nano
        - CTRL + X
      - Finaliser les config:
        - Commande UNE PAR UNE :
          - a2enmod proxy_fcgi setenvif
          - a2enmod rewrite
          - a2enconf php*-fpm
          - a2dissite 000-default.conf
          - a2ensite glpi.conf
          - systemctl restart apache2 mariadb.service