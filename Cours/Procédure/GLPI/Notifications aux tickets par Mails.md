# Notification aux tickets par mail

Ici : ticket créé -> mail envoyé.

## Sur GLPI

- Configuration
  - Notifications
    - Activer les notifs
      - Activer notifs par mail
    - Configuration des notifs par mail
      - Rentrer le mail de l'admin (en entreprise, celui qui peut gérer les paramètres GLPI, souvent admin)
      - Rentrer le mail de l'expéditeur (En entreprise, la boîte partagée qui recevra les notifs)
      - Rentrer l'adresse de Réponse (même qu'expéditeur)
      - Rentrer l'adresse de Non-Réponse (même qu'expéditeur)
      - Mode d'envoi : PHP
      - Hôte SMTP : @IP ExchangeServer (pas DC)
      - Vérifier Certificat : non
      - Expéditeur du message : @mail expéditeur
    - Envoyer un mail test pour confirmer
  - Actions automatiques
    - Queuednotification
      - Mode d'execution :  GLPI
        - Executer (Si echec, retenter avec mode CLI)
- Administration
  - Users
    - Compte receptacle des tickets (Support par exemple)
      - Habilitations
        - Dans profil
          - Attribuer un rôle (Technicien pour tester)
            - Ajouter
- Sur un compte user
  - Créer un ticket
    - L'attribuer au compte cible (Support pour l'exemple, ou au groupe Technicien)
- Remontée de Mail ?