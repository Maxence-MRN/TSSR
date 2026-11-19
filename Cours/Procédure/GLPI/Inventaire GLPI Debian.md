# Upload Automatique d'inventaire GLPI pour Debian
## Sur GLPI

- Dans l'onglet "Administration"
  - Inventaire
    - Confirmer "Inventaire activé"
    - Selectionner le mode d'authentification (dans le cadre d'un TP, prendre aucun)
- Aller sur Github pour connaître la dernière version disponible de l'agent : [Github Agent GLPI release latest](https://github.com/glpi-project/glpi-agent/releases/latest)
  - Le server est sur Debian, il faut donc identifier la version correspondante (opter pour la version sans snap install support)

## Sur la Debian

- Il faudra utiliser un script perl. La version étant identifiée, se placer dans un dossier, par exemple :
  - commande : cd /tmp
  - puis : wget https://github.com/glpi-project/glpi-agent/releases/download/1.XX/glpi-agent-1.XX-linux-installer.pl (où on remplace les XX du numéro de version par celui désiré)
- Exécuter le script pour installation
  - commande : sudo perl glpi-agent-1.XX-linux-installer.pl (où on remplace les XX du numéro de version par celui désiré) **Si je suis log en profil root, enlever le "sudo"**
    - Lorsqu'il est demandé de renseigner l'URL du server GLPI, saisir **entièrement** l'@.
      - commande : http://@ipserver/glpi
    - Laisser vide les demandes liées à la config de l'inventaire local et l'ajout d'un tag
    - *Nota: dans le cas d'un emploi d'une authentification basique pour inventaire via agent (donc hors TP), il sera nécessaire de modifier un fichier de config pour déclarer l'ID et le Pwd à utiliser pour lier l'agent au server GLPI*
  - Forcer la remontée d'inventaire par execution de l'agent
    - Commande : glpi-agent --force
  - Retourner sur la page GLPI, constater la machine montée dans le menu "Parc " > sous-menu "ordinateurs"

Remontée Terminée. Noter que chaque machine devant être inventoriée doit avoir l'agent installé pour être référencée. Un script ou une GPO est donc souhaitable dans le cas de machines multiples.