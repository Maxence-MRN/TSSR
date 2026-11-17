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

SUR L'AD (Windows Server 2025) :

Nom serveur + IP fixée
Prérequis : ADDS + DNS -> Promu contrôleur de domaine et zone inversée faite

Carte réseau : NAT

1) Avec la console PowerShell taper la commande suivante : Install-WindowsFeature RSAT-ADDS

1') SCONFIG : Bloquer toutes les mises à jour depuis Windows Update

2) Installer VC++ 2012 x64 (vcredist_x64) et VC++ 2013 x64, puis redémarrer
   (.NET 4.8.1 est déjà intégré à WS2025 : rien à installer)

3) Télécharger l'ISO Exchange Server SE (ExchangeServerSE-x64.iso, RTM 15.2.2562.17)
   et l'extraire dans E:\exchange

4) Ouvrir la console CMD (en administrateur, avec un compte membre de Schema Admins
   et Enterprise Admins) et se placer dans le dossier E:\exchange

5) Taper les trois commandes suivantes :

Serv2025

Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms_DiagnosticDataON
Setup.exe /PrepareAD /OrganizationName:"vincent" /IAcceptExchangeServerLicenseTerms_DiagnosticDataON
Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms_DiagnosticDataON

-----------------------------------------------------------------------------

SUR LE SERVEUR EXCHANGE (Windows Server 2025) :

1) Nom serveur + IP fixée, serveur joint au domaine, carte en NAT

1') SCONFIG : Bloquer toutes les mises à jour depuis Windows Update

2) Installer le vcredist 2012 x64 puis le vcredist 2013 x64
   (.NET 4.8.1 est déjà intégré à WS2025 : rien à installer)

3) Installer le module IIS URL Rewrite (rewrite_amd64), puis redémarrer

4) Extraire l'ISO Exchange SE dans C:\exchange (ou la monter)

5) Ouvrir la console CMD en administrateur, se placer dans E:\exchange
   et lancer l'installation (les rôles Windows nécessaires sont ajoutés par le setup) :

Setup.exe /Mode:Install /Roles:Mailbox /InstallWindowsComponents /IAcceptExchangeServerLicenseTerms_DiagnosticDataON

6) Redémarrer le serveur

7) Installer la dernière mise à jour de sécurité Exchange SE (SU), lancée en administrateur