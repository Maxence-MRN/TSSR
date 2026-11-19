# Liaison LDAP avec AD

## Pour quoi faire ?

Permet de faire le pont entre AD et GLPI (récupérer les users depuis l'AD)

## Sur GLPI

- Configuration
  - Authentification
- Ajouter
  - Cliquer sur **Active Directory** sous "Préconfiguration"
    - Nom : Nom du Server où se trouve l'AD
    - Server par défaut : non
    - Activé : **OUI**
    - Server : *@IP du server*
    - Port : *Par défaut*
    - Commentaire : *libre*
    - Filtre de connexion : *Pré-rempli*
    - BaseDN : DC=*nomdomaine*,DC=*suffixedomaine*
    - DN du compte : administrateur@*nomdomaine.suffixedomaine*
    - Pwd du compte : *Pwd du compte mentionné*
    - Champ identifiant : *laisser pré-remplis*
    - Champ de synchro : *laisser pré-remplis*
      - Valider
- Message d'erreur, c'est *NORMAL*

## Sur WinServ
- Gestionnaire de server
  - Serveur local
    - Outils
      - Gestion de Strat de groupe
        - Dérouler jusqu'au domaine
          - Clic droit sur "Default Domain Policy"
            - Modifier
      - Config ordinateur
        - Paramètres Windows
            - Paramètres de Sécurité
              - Stratégies locales
                - Options de sécurité
                  - Contrôleur de domaine : Conditions requises pour la signature LDAP
                    - Définir sur "Aucun"
                      - Appliquer
                  - Contrôleur de domaine : application des conditions requises pour la signature...
                    - Définir sur "Activer"
                      - Appliquer > OK
                    - Définir ensuite sur "Désactiver"
                      - Appliquer > OK
- Ouvrir CMD
  - Commande : gpupdate /force

## Retour sur GLPI

Refresh
**TOUT AU VERT, QUE DU BONHEUR**
- Administration
  - Users
    - En haut, en-desous du "+", un rouage avec écrit "Liaison Annuaire LDAP" (**Si absent, déco/reco)
      - Importation
        - Sans filtre : Rechercher
          - Descendre et cocher les profils à importer
            - Action > Importer.
*Les users ont désormais un accès GLPI avec leurs accès*