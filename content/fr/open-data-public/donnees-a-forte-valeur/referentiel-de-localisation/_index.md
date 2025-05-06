---
title: "Référentiel de localisation"
date: 2024-11-15T11:18:12+11:00
draft: false
description: "Découvrez le concept de référentiel de localisation de Nouvelle-Calédonie"
weight: 1
objectifs:
- Comprendre ce qu'est le référentiel de localisation de Nouvelle-Calédonie
- Eclaircir les subtilités autour des notions d'adresse, de parcelle cadastrale, de POI
- Découvrir le service d'API de géocodage
---


# Référentiel de localisation : une brique essentielle pour un service public plus efficace

## 1. Ce qu’on croit savoir : une adresse, c’est toujours postal ?

En métropole, on dispose d’adresses postales normalisées (numéro, rue, code postal, commune).  
Mais en Nouvelle-Calédonie, la situation est différente :

- Seules **6 communes sur 33** sont pleinement adressées.
- Ailleurs, on localise via :
  - **Parcelles cadastrales**
  - des **points d’intérêt (POI)**:
        - **Tribus**
        - **Lieux-dits**
        - **Équipements publics**
        - **Voies nommées** (non normalisées)
        - Etc.
- Dans les **îles Loyauté**, il n’y a **ni cadastre ni adresses postales** : on utilise les **points d’intérêt (POI)**.

> 💡 Une "localisation", ce n’est pas forcément une adresse postale.

---

## 2. Pourquoi un référentiel commun est essentiel

Un référentiel commun de localisation permet de :

- 🚑 **Mieux localiser les personnes** en cas d’urgence ou de crise
- 🧩 **Uniformiser la saisie** dans les systèmes d’information (SI)
- 🔄 **Interconnecter les bases de données** du territoire
- 🧹 **Améliorer la qualité des données**

Il s’inscrit dans la dynamique du futur **Service Public de la Donnée (SPD) de la Nouvelle-Calédonie**.


## 3. L'API Localisation, une avancée majeure

Disponible sur [localisation.gouv.nc](https://localisation.gouv.nc), l’API localisation permet :

- 🔍 **Rechercher** une localisation (par adresse, parcelle cadastrale, POI)
- ✍️ **Auto-compléter** les saisies dans un formulaire
- 📍 **Géolocaliser** un point
- 🔁 **Faire une recherche inversée** (à partir de coordonnées)
- 🗺️ **Afficher les résultats sur une carte**

➡️ [Accéder à l'API REST conforme OpenAPI 3.0 (swagger disponible)](https://localisation.gouv.nc/api/openapi)  
➡️ [Comprendre comment utiliser l'API Localisation (Guide du développeur)](https://guide.data.gouv.nc/guide-du-developpeur/API-localisation/)  


## 4. Cas d’usage concrets

- 🌪️ **Cyclone** : repérer les habitations à secourir
- 🦠 **COVID** : localiser les foyers isolés ou les clusters
- 🏢 **Formulaires en ligne** : aider à saisir un lieu même sans adresse postale


## 5. Et demain ?

- Intégration de l’API dans les applications métiers et les démarches en ligne
- Alimentation continue des données au fur et à mesure de l'implémentation de l'adressage des communes
- Vers une brique essentielle d’un **commun numérique territorial**


## 7. En savoir plus

- 🔗 [API Localisation](https://localisation.gouv.nc)
- 📜 [Guide du développeur sur l'API localisation](https://guide.data.gouv.nc/guide-du-developpeur/API-localisation/)
- 📘 [Feuille de route Data 2024–2025](https://drive.google.com/file/d/1XC_C2qcxsaH5Gj5XCH29STr6oIyKFBvo/view?usp=sharing)
- 📍 [Site web du GIE SERAIL](https://www.serail.nc/) : Le Groupement d’Intérêt Économique SERAIL accompagne activement les communes calédoniennes dans leurs démarches d’adressage et de numérotation des voies.
- 🤝 [Site web de la DITTT](https://dittt.gouv.nc/information-geographique/en-savoir-plus/cadastre-et-inventaire-parcellaire) : La Direction des Infrastructures, de la Topographie et des Transports Terrestres joue un rôle clé dans la structuration et la mise à disposition des données géographiques du territoire.
- 🎥 [Vidéo Afterwork Data](https://www.youtube.com/watch?v=HQaQj8_NQt4) avec l'intervention de Fabien CAPRI, directeur du GIE SERAIL (⌛ à 40'57)
- 📧 Contact : [data@gouv.nc](mailto:data@gouv.nc)
