# Projet 2 - The Scripting Project

## Description

Ce projet consiste à créer un outil d'administration centralisée multi-plateforme capable d'administrer
à distance des machines clientes Windows et Linux depuis deux serveurs distincts.

L'outil permet de :

- Gérer des utilisateurs à distance
- Administrer des postes clients
- Interroger le statut d'une machine
- Créer et rechercher des informations dans des journaux d'événements
- Automatiser des opérations ciblées

Il se compose de deux scripts :

- Un script **Bash** exécutable depuis un serveur Debian
- Un script **PowerShell** exécutable depuis un serveur Windows Server

---

## Equipe - Groupe 1

| Membre |
|--------|
| Zinedine Balamane |
| Brice Hemart |
| Patrick Tambwe |
| Mohamed Badane |

---

## Contexte du projet

- **Formation :** TSSR - Technicien Systeme et Reseaux
- **Hyperviseur :** Proxmox VE (serveur distant)
- **Plage VM Groupe 1 :** ID 101 a 198

---

## Infrastructure

### Machines virtuelles

| Machine | OS | Adresse IP (G1) | Role |
|---|---|---|---|
| SRVLX01 | Debian 13 CLI | 172.16.10.10 | Serveur - script Bash |
| SRVWIN01 | Windows Server 2022 GUI | 172.16.10.5 | Serveur - script PowerShell |
| CLILIN01 | Ubuntu 24 LTS | 172.16.10.30 | Client Linux |
| CLIWIN01 | Windows 10/11 | 172.16.10.20 | Client Windows |

### Parametres reseau

| Parametre | Valeur |
|---|---|
| Masque | 255.255.255.0 |
| Passerelle | 172.16.10.254 |
| DNS | 8.8.8.8 |

### Comptes par defaut

| Machine | Compte | Mot de passe | Groupe |
|---|---|---|---|
| SRVLX01 | wilder | Azerty1* | sudo |
| SRVLX01 | root | Azerty1* | - |
| SRVWIN01 | Wilder | Azerty1* | Administrateurs |
| SRVWIN01 | Administrator | Azerty1* | - |
| CLILIN01 | wilder | Azerty1* | sudo |
| CLIWIN01 | Wilder | Azerty1* | Administrateurs locaux |

---

## Prerequis et Installation

### Cote serveur Linux (SRVLX01)

```bash
# Cloner le depot
git clone https://github.com/WildCodeSchool/TSSR-Projet2-G1.git

# Rendre le script executable
chmod +x scripts/bash/main.sh

# Lancer le script
./scripts/bash/main.sh
````

### Cote serveur Windows (SRVWIN01)

```powershell
# Autoriser l'execution de scripts
Set-ExecutionPolicy RemoteSigned

# Lancer le script
.\scripts\powershell\main.ps1
```

---

## Fonctionnalites

### Actions disponibles

| Type | Cible | Action | Bash | PowerShell |
|---|---|---|---|---|
| Action | Ordinateur client | Verrouillage | Oui | Oui |
| Action | Ordinateur client | Redemarrage | Oui | Oui |
| Action | Ordinateur client | Creation de repertoire | Oui | Oui |
| Action | Ordinateur client | Suppression de repertoire | Oui | Oui |
| Action | Ordinateur client | Prise en main a distance (CLI) | Oui | Oui |
| Action | Ordinateur client | Activation du pare-feu | Oui | Oui |
| Action | Ordinateur client | Execution de script sur machine distante | Oui | Oui |
| Action | Utilisateur | Creation de compte utilisateur local | Oui | Oui |
| Action | Utilisateur | Changement de mot de passe | Oui | Oui |
| Action | Utilisateur | Suppression de compte utilisateur local | Oui | Oui |
| Action | Utilisateur | Ajout a un groupe d'administration | Oui | Oui |
| Action | Utilisateur | Ajout a un groupe | Oui | Oui |

### Informations collectees

| Type | Cible | Information | Bash | PowerShell |
|---|---|---|---|---|
| Information | Ordinateur client | Liste des utilisateurs locaux | Oui | Oui |
| Information | Ordinateur client | 5 derniers logins | Oui | Oui |
| Information | Ordinateur client | Adresse IP, masque, passerelle | Oui | Oui |
| Information | Ordinateur client | Nombre de disques | Oui | Oui |
| Information | Ordinateur client | Partitions (nombre, nom, FS, taille) | Oui | Oui |
| Information | Ordinateur client | Espace disque restant par partition/volume | Oui | Oui |
| Information | Ordinateur client | Version de l'OS | Oui | Oui |
| Information | Ordinateur client | Carte graphique | Oui | Oui |
| Information | Ordinateur client | CPU % | Oui | Oui |
| Information | Ordinateur client | Uptime | Oui | Oui |
| Information | Ordinateur client | 10 derniers evenements critiques | Oui | Oui |
| Information | Ordinateur client | Temperature CPU | Oui | Oui |
| Information | Utilisateur | Droits/permissions sur un dossier | Oui | Oui |
| Information | Script | Recherche dans log_evt.log par utilisateur | Oui | Oui |
| Information | Script | Recherche dans log_evt.log par ordinateur | Oui | Oui |

---

## Structure du depot
