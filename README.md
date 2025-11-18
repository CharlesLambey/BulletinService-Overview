# 📨 BulletinService  
### *Service Windows automatisé pour la signature électronique et l’envoi sécurisé des bulletins de paie*

---

## 🎯 Présentation du projet

**BulletinService** est un service Windows professionnel développé pour automatiser le processus de traitement, de signature électronique et d’envoi sécurisé des bulletins de paie aux salariés.

Il permet de réduire les tâches manuelles, de sécuriser les échanges et d’améliorer la traçabilité dans le processus de distribution des bulletins.

---

## 🧩 Fonctionnalités principales

### 🔒 1. Signature électronique (optionnelle)
Le service peut apposer une signature électronique sur chaque bulletin PDF :

- **Signature désactivée**
- **Signature locale** (image .png sur le disque)
- **Signature en ligne via Google Drive** (compte de service Google)

### 📤 2. Distribution automatique par email
- Récupération des informations salariés depuis **Sage Paie & RH**
- Association automatique entre bulletin et salarié
- Envoi via SMTP

### 🧠 3. Intégration Sage Paie & RH
Extraction automatique de données :
- Nom  
- Matricule  
- Genre  
- Email  
- Informations utiles pour l’envoi ciblé du bulletin

### 📝 4. Gestion et suivi
- Journaux d’exécution (logs)
- Gestion des erreurs
- Historique des opérations

---

## 🧱 Architecture technique

| Composant | Technologie / Outil |
|----------|----------------------|
| Application | C# – Windows Service (.NET Framework) |
| Signature PDF | iTextSharp |
| API Cloud | Google Drive API (v3 – Service Account) |
| Emailing | SMTP |
| Logs | Stockage local (LogFolder) |

---

## 📂 Structure du projet (présentation)

    BulletinService/
    │
    │── Service1.cs              # Service Windows principal
    │── GoogleDriveHelper.cs     # Gestion de la signature Google Drive
    │── PdfSigner.cs             # Apposition de la signature PDF
    │── Log.cs                   # Système de logs
    │── App.config               # Paramètres du service
    │── packages.config
    │── Program.cs


> ⚠️ *Le code source complet n’est pas publié pour raisons de confidentialité.*

---

## 🖥️ Prérequis système

| Élément | Exigence |
|--------|----------|
| Système | Windows 10 / Windows Server 2016+ |
| Framework | .NET Framework 4.7.2+ |
| Droits | Administrateur (installation du service) |
| Connexion | Internet requise pour Drive & SMTP |
| Espace requis | 500 Mo minimum |

---

## ⚙️ Modes de signature

| Mode | Description |
|------|-------------|
| **Désactivée** | Aucun traitement appliqué |
| **Locale** | Image .png stockée localement |
| **En ligne** | Récupération Google Drive via compte de service |

---

## ⚙️ Exemple de configuration (anonymisé)

```xml
<configuration>
  <appSettings>
    <!-- Activation de la signature -->
    <add key="onsign" value="true"/>

    <!-- Mode signature : en ligne / locale -->
    <add key="onligne" value="false"/>

    <!-- Chemin signature locale -->
    <add key="cheminSigneOffLine" value="C:\Signatures\signature.png"/>

    <!-- Paramètres SMTP (anonymisés) -->
  </appSettings>
</configuration>

```

## 🧑‍💻 Rôle dans le projet

Développement complet du service Windows, incluant :

- Architecture logicielle
- Développement en C#
- Intégration Sage Paie
- Gestion signature PDF (iTextSharp)
- Intégration Google Drive API
- Système d’envoi email (SMTP)
- Gestion des logs
- Déploiement et configuration


## 🔒 Code source non publié

Ce repository présente uniquement :

- l’architecture
- les concepts
- les fonctionnalités
- la documentation d’ensemble
> ⚠️ Le code source complet reste confidentiel conformément aux exigences de l’entreprise.

## 🎉 Résultats

- ✔️ Réduction importante des tâches manuelles
- ✔️ Distribution rapide et sécurisée des bulletins
- ✔️ Automatisation fiable et continue
- ✔️ Amélioration de la confidentialité et traçabilité

---

## 🔐 Sécurité
- Aucune donnée sensible n’est publiée dans ce dépôt.
- Le code source réel est confidentiel.
- Le README sert uniquement à illustrer l’expérience sur le projet.

---

## 👤 Auteur
**Charles LAMBEY**  
Consultant & Développeur Full Stack  
_Odoo | Sage 100 & X3 | Intégration & Automatisation_

---
