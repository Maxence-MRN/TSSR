# Création Serveur Exchange

## Sur un Premier WinServ
!!RENOMMER ET ATTRIBUER @IP FIXE!!

### Rôle du Serv
- ADDS
  - Promouvoir DC
    - Attribuer un nom de domaine : XXX.YY
      - Reboot
- DNS
  - Paramétrer Zone inversée
    -     - Reboot
**Créer un user** (GRP : Admin)

## Sur un Deuxième WinServ

!! RENNOMER ET ATTRIBUER UNE @IP FIXE **DANS le MÊME RSO QUE LA PREMIERE MACHINE**!!
Le DNS préféré sera **L'@IP du DC-Server**

**Le mettre dans le domaine, définit par le premier serv**

### Rôle du Serv
- Pas de rôle

## Situation et Installation

### SUR L'AD (Windows Server 2025) :

Nom serveur + IP fixée
Prérequis : ADDS + DNS -> Promu contrôleur de domaine et zone inversée faite

Carte réseau : NAT

1) Win+R > SCONFIG : Bloquer toutes les mises à jour depuis Windows Update
   
2) Avec la console PowerShell taper la commande suivante : Install-WindowsFeature RSAT-ADDS

3) Installer vcredist_x64

4) Télécharger l'ISO Exchange Server SE (ExchangeServerSE-x64.iso, RTM 15.2.2562.17) et le coller sur le bureau du Server

5) - Double clic sur l'Iso > Le lecteur de DVD virtuel s'ouvre en lecteur E:/
     - Aller dans la barre URL de l'explorateur, entrer "CMD"
       - Le cmd s'ouvre en E:\>

6) Taper les trois commandes suivantes (*PAS SIMULTANEMENT*) :

Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms_DiagnosticDataON
Setup.exe /PrepareAD /OrganizationName:"**NomDeDomaine**" /IAcceptExchangeServerLicenseTerms_DiagnosticDataON
Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms_DiagnosticDataON

-----------------------------------------------------------------------------

### SUR LE SERVEUR EXCHANGE (Windows Server 2025) :

Nom serveur + IP fixée, serveur joint au domaine, carte en NAT

1) Win+R > SCONFIG : Bloquer toutes les mises à jour depuis Windows Update

2) Installer vcredist_x64

3) Executer le UcmaRuntimeSetup

4) Télécharger l'ISO Exchange Server SE et le coller sur le bureau du Server

5) - Double clic sur l'Iso > Le lecteur de DVD virtuel s'ouvre en lecteur E:/
     - Aller dans la barre URL de l'explorateur, entrer "CMD"
       - Le cmd s'ouvre en E:\> et lancer l'installation (les rôles Windows nécessaires sont ajoutés par le setup) :
         - Setup.exe /Mode:Install /Roles:Mailbox /InstallWindowsComponents /IAcceptExchangeServerLicenseTerms_DiagnosticDataON
       - **SI LE SCRIPT AFFICHE TOUTE UNE LISTE DE MESSAGES D'ERREURS, SE DECONNECTER ET SE RECONNECTER EN ADMIN DOMAINE, PUIS RELANCER LE SCRIPT**
   - Echec à l'analyse des éléments préalable. (*C'est normal*)
     - Lancer le rewrite_amd64
       - Installer

6) Dans le fichier ISO, lancer manuellement le Setup
  - à l'issue des analyses préalables, lancer l'installation

7)  Redémarrer le serveur