# Types de mise en Réseau

* Paramètres modifiables sur onglet Modifier > Editeur de réseaux Virtuels

## Vue d'ensemble ##  

                    RÉSEAU PHYSIQUE
                          │
                    [ Routeur ]
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
     PC Hôte         VM (Bridged)      Autres PCs
                          │
 ───────────────────────────────────────────────

                 VM (NAT)
                    │
                [ NAT VMware ]
                    │
                 PC Hôte
                    │
             Réseau physique

 ───────────────────────────────────────────────

                 VM (Host-Only)
                    │
          Réseau privé VMware
                    │
                 PC Hôte  


## Bridged Mode ## 

La machine virtuelle est directement connectée au réseau physique comme un ordinateur indépendant.  


        Réseau local (LAN)
                │
      ┌─────────┼─────────┐
      │         │         │
    PC1      PC Hôte   VM1
              │
         VMware Bridge  

### Caractéristiques ###

✅ Adresse IP obtenue du routeur/DHCP du réseau  
✅ Visible par tous les équipements du réseau  
✅ Peut fournir et recevoir des services réseau

❌ Consomme une adresse IP du réseau  

### Cas d'usage ###
- Serveur Web  
- Serveur DNS  
- Tests en environnement réel  
- Administration réseau  

## NAT Mode (Network Adress Translation)  
La VM utilise l'adresse IP du PC hôte pour accéder au réseau externe.

             INTERNET
                 │
             Routeur
                 │
              PC Hôte
                 │
             NAT VMware
                 │
                VM1
``  

### Caractéristiques ###

✅ Accès Internet immédiat  
✅ IP privée attribuée par VMware  
✅ Protège la VM du réseau externe

❌ La VM n'est généralement pas accessible directement depuis le réseau  

### Cas d'usage ###
- Navigation Internet
- Téléchargement de logiciels
- Laboratoires de test
- Machines virtuelles temporaires  

## Host-Only Mode ##
La VM peut communiquer uniquement avec le PC hôte et les autres VMs du même réseau Host-Only.  

          Réseau Host-Only

        ┌───────────────┐
        │   PC Hôte     │
        └───────┬───────┘
                │
      ┌─────────┼─────────┐
      │                   │
    VM1                 VM2

      (Pas d'accès Internet)

### Caractéristiques ###  

✅ Réseau totalement isolé  
✅ Communication entre VMs possible  
✅ Sécurisé pour les tests

❌ Pas d'accès Internet par défaut  

### Cas d'usages ###

- TP réseau
- Malware Analysis
- Exercices d'administration
- Laboratoires isolés  

## Comparatif Rapide ##

```text
┌────────────┬─────────────┬─────────────────┬────────────────────┬─────────────────────┐
│ Mode       │ Internet    │ Visible sur LAN │ Communication Hôte │ Usage principal     │
├────────────┼─────────────┼─────────────────┼────────────────────┼─────────────────────┤
│ Bridged    │ Oui         │ Oui             │ Oui                │ Serveurs, prod      │
│ NAT        │ Oui         │ Non             │ Oui                │ Tests, navigation   │
│ Host-Only  │ Non         │ Non             │ Oui                │ TP, labo isolé      │
└────────────┴─────────────┴─────────────────┴────────────────────┴─────────────────────┘
```

### Lecture simplifiée

```text
BRIDGED
VM <──────────────> Réseau local
         Visible de tous

NAT
VM ──> Hôte ──> Réseau local / Internet
       (traduction d'adresse)

HOST-ONLY
VM <──────────────> Hôte
     Réseau privé isolé
```
## Pour retenir ##
BRIDGED  → "Je suis un vrai PC du réseau"

NAT      → "Je sors sur Internet via mon hôte"

HOST-ONLY→ "Je reste dans mon laboratoire privé" 

## Choisir le mode ##

    Besoin d'être visible sur le réseau ?  

            │
           OUI
            │
        BRIDGED

            │
           NON
            │
    Besoin d'Internet ?
      │          │
     OUI        NON
      │          │
     NAT    HOST-ONLY