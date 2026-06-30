# 📨 BulletinService — Service Windows d’envoi automatisé des bulletins de paie

**BulletinService** est un service Windows développé en **C# (.NET Framework)** permettant :

- d’apposer automatiquement une signature électronique (image **locale**) sur les bulletins de paie au format PDF ;
- d’extraire les informations des salariés depuis **Sage Paie & RH** ;
- d’envoyer individuellement chaque bulletin au salarié correspondant ;
- de journaliser toutes les opérations (logs) pour analyse et traçabilité.

Ce service s’adresse aux entreprises qui souhaitent automatiser et sécuriser la distribution électronique des bulletins de paie. **BulletinService** se connecte directement au logiciel **Sage Paie & RH** afin de récupérer les informations relatives aux salariés.
L’utilisation de **Sage Paie & RH** constitue donc un prérequis pour garantir le bon fonctionnement du service.

Cependant, si vous utilisez un autre logiciel de paie, nous pouvons personnaliser BulletinService afin de l’adapter à votre solution actuelle.

---

## 🚀 Fonctionnalités principales

### ✔️ Signature électronique des PDFs  
- Signature **locale** (image stockée sur le disque, chemin configurable)  
- Position et dimensions paramétrables (`posX`, `posY`, `largeur`, `hauteur`)  
- Option de désactivation totale de la signature (`onsign`)  
- Si la signature est activée mais le fichier introuvable : **log explicite** et bulletins non envoyés (pas de bulletin non signé)

### ✔️ Envoi automatique des bulletins par email  
- Envoi **SMTP via OAuth2** (Microsoft 365 / Azure Entra ID, XOAUTH2)  
- Connexion chiffrée (SSL/TLS)  
- Contenu d’email personnalisable  
- Association automatique PDF ↔ salarié via :  
  **Matricule – Date de Paie**  
- **Validation du format** de l’adresse avant envoi ; gestion des cas
  *email absent* (`_NoEmail`) et *email invalide* (`_InvalidEmail`)

### ✔️ Sécurité des secrets  
- Aucun secret en clair dans `App.config`  
- Secret Azure et identifiants SQL lus depuis des **variables d’environnement**
  (`BULLETIN_OAUTH_CLIENT_SECRET`, `BULLETIN_SQL_USER`, `BULLETIN_SQL_PASSWORD`)

### ✔️ Intégration Sage Paie & RH  
- Lecture des informations salariés  
- Correspondance PDF / fiche du salarié

### ✔️ Exécution en tant que Service Windows  
- Démarrage automatique  
- Exécution en arrière-plan  
- Logs détaillés

---

## 🧱 Architecture technique

- **Langage** : C#  
- **Framework** : .NET Framework 4.8  
- **Service Windows**  
- **Signature PDF** : iTextSharp (signature locale)  
- **Email** : SMTP **OAuth2** (Microsoft 365) via MSAL (`Microsoft.Identity.Client`)  
- **Base de données** : SQL Server (Sage Paie & RH)  
- **Logging** interne dans `LogFolder/`, avec repli **Event Viewer** (source `BulletinService`)  

Schéma détaillé disponible dans `docs/ARCHITECTURE.md`.

---

## 📂 Structure du projet

    BulletinService/
    │ README.md
    │ App.config
    │ BulletinService.csproj
    │ Program.cs
    │ Service1.cs            (orchestrateur du service)
    │ PdfSigner.cs           (signature PDF locale)
    │ OAuth2MailSender.cs    (envoi email SMTP OAuth2)
    │ OAuth2TokenService.cs  (jeton OAuth2 via Azure / MSAL)
    │ EnvConfig.cs           (lecture des secrets via variables d'environnement)
    │ EmployeeInfo.cs
    │ Log.cs                 (logs fichier + repli Event Viewer)
    │
    │ ProjectInstaller.cs              (installe le service + source EventLog)
    │ ProjectInstaller.Designer.cs
    │
    ├── Properties/
    │ └── AssemblyInfo.cs
    └── docs/
      ├── INSTALL.md
      ├── CONFIG.md
      ├── DEPLOY.md
      └── ARCHITECTURE.md


---

## ⚙️ Documentation

La documentation détaillée se trouve dans le dossier `docs/` :

- `docs/INSTALL.md` → installation/démarrage/arrêt du service  
- `docs/CONFIG.md` → paramètres complets du fichier App.config  
- `docs/ARCHITECTURE.md` → diagrammes + logique interne du service  
- `docs/DEPLOY.md` → checklist de déploiement (secrets, SQL, variables d’environnement, service)  

---

## 👤 Auteur

**Charles LAMBEY**  
Consultant & Développeur Full Stack  
_Odoo | Sage 100 & X3 | Intégration & Automatisation_

---

## 📜 Licence

Projet interne — **Code source privé**.  
Toute diffusion est strictement interdite sans autorisation du propriétaire.
