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





---

