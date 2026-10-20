
---

# ☁️ **Installation de Proxmox VE (Virtual Environment)**

> [!info] ⚙️ Contexte
> 
> Proxmox VE est un hyperviseur de Type 1 (Bare Metal) basé sur Debian.
> 
> Il s'installe directement sur le matériel (sans Windows ni Linux en dessous) et permet de gérer des VMs (KVM) et des Conteneurs (LXC) via une interface Web.

---

## 📋 **1️⃣ Prérequis Matériel**

Avant de commencer, assure-toi d'avoir :

- 🧠 **CPU** : 64 bits (Intel VT-x ou AMD-V activé dans le BIOS).
    
- 💾 **RAM** : Minimum 2 Go (8 Go+ recommandés pour faire tourner des VMs).
    
- 🔌 **Réseau** : Une connexion filaire (Ethernet) est fortement recommandée.
    
- 🗝️ **Clé USB** : Au moins 4 Go pour l'installateur.
    

---

## 💿 **2️⃣ Création du support d'installation**

1. **Télécharger l'ISO** sur le site officiel : [Proxmox Downloads](https://www.proxmox.com/en/downloads).
    
2. **Flasher l'ISO** sur une clé USB avec **Rufus** (Windows) ou **BalenaEtcher**.
    
3. **Booter** le serveur sur la clé USB (via F11, F12 ou Suppr selon le BIOS).
    

---

## 🖥️ **3️⃣ Étapes de l'installation (Pas à pas)**

Une fois l'installateur lancé, voici les écrans à configurer :

### 🔹 1. Welcome Screen

Sélectionnez **"Install Proxmox VE (Graphical)"** et validez.

### 🔹 2. End User License Agreement (EULA)

Cliquez sur **"I agree"**.

### 🔹 3. Target Harddisk (Disque cible)

Choisissez le disque où Proxmox sera installé.

> [!warning] ⚠️ Attention
> 
> Le disque choisi sera entièrement effacé.
> 
> Si vous avez plusieurs disques, installez l'OS sur un petit SSD (ex: 120Go) et gardez les gros disques pour le stockage des VMs.

### 🔹 4. Country, Timezone and Key Layout

- **Country** : France
    
- **Timezone** : Europe/Paris
    
- **Keyboard Layout** : French (Azerty)
    

### 🔹 5. Password and Email

- **Root Password** : Définissez le mot de passe administrateur (ne le perdez pas !).
    
- **Email** : Utilisé pour les alertes système.
    

### 🔹 6. Network Configuration (Le plus important !)

C'est ici que vous définissez l'IP fixe du serveur.

|**Champ**|**Exemple**|**Description**|
|---|---|---|
|**Hostname (FQDN)**|`pve.maison.local`|Nom complet (Machine + Domaine)|
|**IP Address**|`192.168.1.100`|L'IP pour accéder à l'interface|
|**Netmask**|`255.255.255.0`|/24 Classique|
|**Gateway**|`192.168.1.1`|IP de votre Box/Routeur|
|**DNS Server**|`1.1.1.1` ou `192.168.1.1`|Pour qu'il ait accès au net|

> [!tip] 💡 Conseil
> 
> Choisissez une IP en dehors de la plage DHCP de votre box pour éviter les conflits.

### 🔹 7. Summary & Install

Vérifiez tout, retirez la clé USB quand demandé, et cliquez sur **Install**. Le serveur va redémarrer.

---

## 🌐 **4️⃣ Premier Démarrage & Accès Web**

Une fois redémarré, un écran noir affiche une URL.

1. Sur un autre PC, ouvrez un navigateur.
    
2. Tapez l'adresse : **`https://<IP_DU_SERVEUR>:8006`**
    
3. Ignorez l'avertissement de sécurité SSL (Avancé -> Continuer).
    

**Login :**

- User : `root`
    
- Password : `Celui défini à l'étape 5`
    

---

## 🛠️ **5️⃣ Post-Installation (Indispensable)**

Par défaut, Proxmox utilise les dépôts "Entreprise" (payants). Il faut les désactiver pour un usage gratuit.

### 🔹 1. Désactiver le dépôt Entreprise

Dans l'interface web :

Node (pve) > Updates > Repositories

1. Sélectionnez `enterprise.proxmox.com`.
    
2. Cliquez sur **Disable**.
    

### 🔹 2. Activer le dépôt "No-Subscription"

1. Cliquez sur **Add**.
    
2. Repository : **No-Subscription**.
    
3. Cliquez sur **Add**.
    

### 🔹 3. Mettre à jour le système

Ouvrez le **Shell** (console) dans l'interface web et lancez :

Bash

```
apt update && apt dist-upgrade -y
```

---

## 💡 **Résumé Visuel**

|**Étape**|**Action**|
|---|---|
|**Boot**|Démarrer sur la clé USB|
|**Disque**|Attention, formatage complet !|
|**Réseau**|Définir une **IP Fixe** obligatoire|
|**Web UI**|Port **8006** en **HTTPS**|
|**Repo**|Passer en **No-Subscription**|

---

> [!success] ✅ Terminé !
> 
> Ton hyperviseur est prêt.
> 
> Tu peux maintenant :
> 
> - Uploader des ISOs (dans `local > ISO Images`).
>     
> - Créer ta première VM (Bouton "Create VM" en haut à droite).
>