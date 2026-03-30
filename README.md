Projet 2 - The Scripting Project

> TSSR - Automatisation de tâches par script
> Groupe : **G-1** 

---

## Présentation du projet

Ce projet consiste à créer un **outil d'administration centralisée multi-plateforme**.
Il permet d'administrer à distance des machines clientes Windows et Linux depuis deux serveurs :
- Un serveur **Debian** (script Bash)
- Un serveur **Windows Server** (script PowerShell)
- Un client **Ubuntu**
- Un client **Windows**

---

## Équipe

| Membre |
|--------|
| Zinedine Balamane | 
| Brice Hemart | 
| Patrick Tambwe | 
| Mohamed Badane | 

---

## 🏗️ Infrastructure

### Machines virtuelles (Proxmox)

| Machine | OS | IP (G[X]) | Rôle |
|---|---|---|---|
| SRVLX01 | Debian 13 CLI | 172.16.[X]0.10 | Serveur Bash |
| SRVWIN01 | Windows Server 2022 GUI | 172.16.[X]0.5 | Serveur PowerShell |
| CLILIN01 | Ubuntu 24 LTS | 172.16.[X]0.30 | Client Linux |
| CLIWIN01 | Windows 10/11 | 172.16.[X]0.20 | Client Windows |

- **Masque :** 255.255.255.0
- **Passerelle :** 172.16.[X]0.254
- **DNS :** 8.8.8.8

---

## ⚙️ Prérequis & Installation

### Côté serveur Linux (SRVLX01)

```bash
# Cloner le dépôt
git clone https://github.com/[organisation]/TSSR-Projet2-G[X].git

# Rendre le script exécutable
chmod +x scripts/bash/main.sh

# Lancer le script
./scripts/bash/main.sh
```

### Côté serveur Windows (SRVWIN01)

```powershell
# Autoriser l'exécution de scripts
Set-ExecutionPolicy RemoteSigned

# Lancer le script
.\scripts\powershell\main.ps1
```

---

## 🚀 Fonctionnalités

### Actions disponibles

| Fonctionnalité | Bash | PowerShell |
|---|---|---|
| Verrouillage de la machine | ✅ | ✅ |
| Création de compte utilisateur local | ✅ | ✅ |
| Changement de mot de passe | ✅ | ✅ |
| Suppression de compte utilisateur | ✅ | ✅ |
| Ajout à un groupe d'administration | ✅ | ✅ |
| Redémarrage de la machine | ✅ | ✅ |
| Création / suppression de répertoire | ✅ | ✅ |
| Prise en main à distance (CLI) | ✅ | ✅ |
| Activation du pare-feu | ✅ | ✅ |
| Exécution de script distant | ✅ | ✅ |

### Informations collectées

| Information | Bash | PowerShell |
|---|---|---|
| Liste des utilisateurs locaux | ✅ | ✅ |
| 5 derniers logins | ✅ | ✅ |
| Adresse IP / masque / passerelle | ✅ | ✅ |
| Disques (nombre, partitions, FS, taille) | ✅ | ✅ |
| Espace disque restant | ✅ | ✅ |
| Version de l'OS | ✅ | ✅ |
| Carte graphique | ✅ | ✅ |
| CPU % | ✅ | ✅ |
| Uptime | ✅ | ✅ |
| 10 derniers événements critiques | ✅ | ✅ |
| Température CPU | ✅ | ✅ |
| Droits/permissions sur un dossier | ✅ | ✅ |
| Recherche dans les logs (utilisateur/machine) | ✅ | ✅ |

---

## 📁 Structure du dépôt
