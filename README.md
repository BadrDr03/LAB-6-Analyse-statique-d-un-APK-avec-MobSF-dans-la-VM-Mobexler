# LAB-6-Analyse-statique-d-un-APK-avec-MobSF-dans-la-VM-Mobexler

# 📱 Rapport d'Audit : UnCrackable-Level1 (OWASP)

## 📝 Présentation du Projet
Ce laboratoire consiste en une **analyse statique** de l'application Android `UnCrackable-Level1.apk`. L'objectif est d'utiliser **MobSF** pour identifier les mécanismes de protection et les vulnérabilités potentielles.

* **Environnement :** VM Mobexler
* **Outil Principal :** MobSF (Mobile Security Framework)
* **Référentiel :** OWASP MASVS

---

## 📁 Task 1 : Préparation de l'Environnement
Une organisation méthodique garantit la traçabilité de l'analyse et facilite la rédaction du rapport final.

### 1. Configuration du Workspace
Le répertoire de travail a été créé et organisé pour isoler l'analyse.
> **Chemin :** `~/apk_analysis/2026-03-30/`

### 2. Intégrité du fichier (Hashing)
Le calcul du hash SHA-256 permet de garantir que l'APK n'a pas été modifié.

![Import OVA](https://github.com/user-attachments/assets/63488476-9394-41a6-a636-c16e252d3332)

---

## ⚙️ Task 2 : Analyse Statique avec MobSF
**Objectif :** Automatiser la détection des vulnérabilités et l'ingénierie inverse.

### 1. Authentification
L'accès à l'interface de gestion se fait via les identifiants par défaut du framework.
* **Username :** `mobsf`
* **Password :** `mobsf`

### 2. Soumission de l'échantillon
Le fichier `uncrackable1.apk` (identifié par le hash SHA-256 en Task 1) a été importé dans le moteur d'analyse.
* **Outil :** MobSF v4.0.6
* **Méthode :** Upload direct via l'interface web locale.

### 3. Synthèse des Vulnérabilités
L'analyse automatisée a révélé plusieurs failles nécessitant une investigation manuelle :
* **Niveau High :** 1 faille détectée.
* **Niveau Medium :** 4 failles détectées.
* **Trackers :** Aucun tracker publicitaire détecté.

![Import OVA](https://github.com/user-attachments/assets/34c576bc-9f23-4aad-885d-129a480a2bc2)

![Import OVA](https://github.com/user-attachments/assets/6e7c49e4-5817-4b5f-b90c-290fb4ada164)

![Import OVA](https://github.com/user-attachments/assets/b2837b0d-c592-4d3a-b36a-02dea67360e3)

![Import OVA](https://github.com/user-attachments/assets/d3cbcf2d-75d9-4a61-8ae6-2bcfba7757c6)

---

## 📊 Task 3 — Exploration de l'Interface MobSF
**Objectif :** Naviguer dans les résultats de l'analyse statique et identifier les métadonnées de l'application.

### 1. Vue d'ensemble du Dashboard
L'interface de MobSF permet une navigation rapide entre les différentes sections de l'audit (Permissions, Network Analysis, Security Score). Le tableau de bord centralise les statistiques critiques de l'APK.

### 2. Données de Traçabilité (Vérification)
Conformément aux exigences du laboratoire, les informations suivantes ont été relevées :
* **Version de l'outil :** v4.0.6
* **Security Score :** 15/100
* **Package Name :** `owasp.mstg.uncrackable1`
* **Main Activity :** `owasp.mstg.uncrackable1.MainActivity`

---

## 🛡️ Task 4 — Analyse du Manifeste (Manifest Analysis)
**Objectif :** Évaluer la posture de sécurité de l'application à travers ses fichiers de configuration.

### 1. Analyse des vulnérabilités critiques (High)
L'examen du fichier `AndroidManifest.xml` via MobSF a révélé des failles majeures de configuration :

* **Mode Debug Activé :** `android:debuggable="true"`. 
    * *Risque :* Permet l'injection de code et l'analyse dynamique non autorisée.
* **Sauvegarde Autorisée :** `android:allowBackup="true"`.
    * *Risque :* Fuite de données utilisateur via les outils de sauvegarde système.

### 2. Gestion des Permissions
L'application définit les droits d'accès au système. Dans ce laboratoire, nous vérifions :
* La pertinence des permissions demandées par rapport aux fonctionnalités.
* La présence de permissions "Dangereuses" selon le classement Android.

### 3. Analyse des Activités
L'inventaire des composants montre l'utilisation de la `MainActivity`. Nous surveillons les filtres d'intention (Intent Filters) pour prévenir les détournements d'activités.

![Import OVA](https://github.com/user-attachments/assets/7ca56609-c997-4228-b2b7-6fcb9072c826)

![Import OVA](https://github.com/user-attachments/assets/2dfbb6b8-2735-4d54-b37d-e49f42042c4b)

---

## 🔍 Task 5 — Analyse de Sécurité (Security Analysis)
**Objectif :** Identifier les vulnérabilités logicielles et les faiblesses d'implémentation technique.

### 1. Analyse du Code Source
L'examen automatisé du code a permis d'identifier plusieurs points de vigilance :
* **Cryptographie :** Recherche d'algorithmes obsolètes ou de vecteurs d'initialisation (IV) statiques.
* **Secrets :** Détection de chaînes de caractères sensibles (clés d'API, mots de passe) incluses directement dans le code.

### 2. Analyse des Librairies Natives (Shared Libraries)
L'application utilise des composants en C/C++. L'analyse MobSF vérifie la présence de protections essentielles au niveau binaire pour prévenir l'exploitation de dépassements de tampon (Buffer Overflow).

### 3. Sécurité Réseau
Vérification des politiques de sécurité réseau pour s'assurer que l'application impose des connexions chiffrées (TLS) et empêche les attaques de type Man-in-the-Middle (MitM).

![Import OVA](https://github.com/user-attachments/assets/83514675-3e5b-4d16-80a2-674070036287)
