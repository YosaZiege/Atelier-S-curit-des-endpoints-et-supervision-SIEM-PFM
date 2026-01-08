# 🛡️ Atelier Sécurité des Endpoints & Supervision SIEM (Multi-OS)

Ce projet documente la mise en œuvre d'une plateforme complète de supervision et de protection basée sur **Wazuh** (SIEM/EDR) au sein d'un environnement Cloud AWS. Il permet de monitorer des parcs informatiques mixtes (Linux & Windows) et de détecter des menaces en temps réel.

---

## 🏗️ Architecture du Projet

L'architecture est déployée sur **AWS Learner Lab** et se compose des éléments suivants :

◈ **VPC AWS** — Réseau isolé avec Security Groups configurés pour les flux SIEM.  
◈ **Wazuh Server (Ubuntu)** — Cerveau du système (collecte, corrélation et analyse).  
◈ **Wazuh Agent (Linux)** — Monitoring d'un endpoint Ubuntu (Audit SSH & FIM).  
◈ **Wazuh Agent (Windows)** — Monitoring Windows Server 2025 avec intégration Sysmon.

---

## 🚀 Fonctionnalités Clés

➤ **Endpoint Security** | Surveillance de l'intégrité des fichiers (FIM) et détection de vulnérabilités.  
➤ **IAM Auditing** | Audit des tentatives de connexion (Brute-force SSH, échecs RDP).  
➤ **EDR Avancé** | Utilisation de **Sysmon** pour capturer la création de processus et les connexions suspectes.  
➤ **Visualisation** | Tableau de bord centralisé pour l'analyse des menaces en temps réel.

---

## 🛠️ Configuration & Installation

### 1. Prérequis Serveur
* Instance Ubuntu 22.04 LTS (Type `t3.medium` recommandé).
* Ouverture des ports 1514 (UDP/TCP), 1515 (TCP), 443 (HTTPS) et 55000 (API) dans le Security Group AWS.

### 2. Déploiement des Agents
* **Linux** : Installation du paquet via le gestionnaire `apt` et renseignement de l'adresse IP du Manager dans le fichier `ossec.conf`.
* **Windows** : Installation de l'agent via l'installeur MSI, couplé à l'installation de **Sysmon** avec un fichier de configuration XML optimisé pour Wazuh.

---

## 🛡️ Scénarios de Test (Démonstrations)

### A. Côté Linux
❖ **Brute-force SSH** : Simulation de tentatives de connexion échouées pour valider les règles de corrélation.  
❖ **FIM (File Integrity)** : Monitoring en temps réel des modifications dans les répertoires critiques (`/etc`, `/bin`).

### B. Côté Windows
❖ **Gestion des Privilèges** : Détection immédiate de création d'utilisateurs (`net user /add`) via PowerShell.  
❖ **Échecs Login RDP** : Surveillance de l'Event ID 4625 (Logon Failure).  
❖ **Audit Processus** : Visibilité profonde via Sysmon sur l'exécution de commandes administratives.

---

## 🧰 Stack Technique
* **SIEM/EDR** : Wazuh
* **Cloud** : AWS (VPC, Security Groups, EC2)
* **Monitoring** : Sysmon (Windows Internals)
* **Systèmes** : Ubuntu 22.04 LTS & Windows Server 2025

--- 
*Projet réalisé dans le cadre d'un atelier pratique sur la cybersécurité et la supervision SIEM.*
