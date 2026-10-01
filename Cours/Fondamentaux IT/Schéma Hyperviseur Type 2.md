# Hyperviseur de Type 2

```text
+----------------------------------+
| Applications Utilisateur         |
| (Navigateur, Office, Jeux, etc.) |
+----------------------------------+
| Système d'exploitation Hôte      |
| (Windows, Linux, macOS)          |
+----------------------------------+
| Hyperviseur Type 2               |
| (VMware Workstation, VirtualBox) |
+----------------------------------+
| Machine Virtuelle 1              |
| +------------------------------+ |
| | OS Invité (Windows)          | |
| +------------------------------+ |
+----------------------------------+
| Machine Virtuelle 2              |
| +------------------------------+ |
| | OS Invité (Linux)            | |
| +------------------------------+ |
+----------------------------------+
| Matériel Physique                |
| CPU - RAM - Disque - Réseau      |
+----------------------------------+
```

## Principe

L'hyperviseur de type 2 s'exécute comme une application au-dessus d'un système d'exploitation hôte.

### Exemples
- VMware Workstation Pro
- Oracle VirtualBox
- VMware Fusion
- Parallels Desktop

### Avantages
- Installation simple
- Idéal pour les tests et la formation
- Utilisable sur un poste de travail classique

### Inconvénients
- Performances inférieures à un hyperviseur de type 1
- Dépend du système d'exploitation hôte
- Consomme davantage de ressources