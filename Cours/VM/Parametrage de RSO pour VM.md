Commencer par récupérer la configuration RSO de la host machine via CMD->ipconfig /all  
---
## Création d'une VM
Outre les paramètres HardWare, plusieurs paramètres sont à modifier pour permettre à la bécane de monter sur le RSO  
(Quand bien même la bécane est bridgée)
## Partie menu VMware
Onglet Modifier > Editeur de RSO virtuel
-> Clear les VMnetX, ne garder que le NAT ou en faire un nouveau.
-> Modifier le RSO VMnet NAT en allant sur "modifier les settings"
-> Modifier l'@ IP de sous-RSO pour y mettre celle du RSO du routeur employé (Ex : 192.168.1.0/24)
-> Même fenêtre, bouton "NAT settings", mettre également l'@ passerelle
>> Penser à faire appliquer et fermer
-> Selectionner la machine et aller chercher l'onglet "VM">"settings"
-> Carte RSO > Connexion RSO = personnalisée (selectionner le bon VMnetX)
## Partie IN-VM (paramètres possiblement mis dès la config init') ** Uniquement le WinServ **
> Se rendre dans les paramètres de cartes RSO, et affecter en IPv4 une @IP disponible dans la même plage. la passerelle définie précédement, et le DNS (Généralement 1.1.1.1 et 8.8.8.8).