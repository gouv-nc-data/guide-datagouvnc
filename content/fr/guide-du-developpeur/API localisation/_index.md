---
title: "API localisation"
date: 2024-11-15T11:18:12+11:00
draft: false
description: "Tout ce qu'il faut savoir pour intégrer l'API Localisation dans vos systèmes"
weight: 1
objectifs:
- Comprendre comment utiliser l'API Localisation
---


## 💡 Présentation générale

L'[API Localisation](https://localisation.gouv.nc/api/openapi) est un service public numérique permettant de rechercher, vérifier et géolocaliser des lieux sur l'ensemble du territoire calédonien, même en l'absence d'adresses postales.

Elle s'adresse aux développeurs d'applications métiers, de portails citoyens, ou de SI internes souhaitant :
- Uniformiser la saisie des localisations
- Améliorer la précision et la qualité des données collectées
- Permettre une interopérabilité entre les services

API REST conforme OpenAPI 3.0 (swagger disponible).

➡️ [Accéder à l'API REST conforme OpenAPI 3.0 (swagger disponible)](https://localisation.gouv.nc/api/openapi)
➡️ [Comprendre ce qu'est le référentiel de localisation de Nouvelle-Calédonie](https://guide.data.gouv.nc/open-data-public/donnees-a-forte-valeur/referentiel-de-localisation/)


## 🔢 Fonctionnalités principales

### Recherche directe (`/search`)

- Recherche par chaîne de caractères : `?q=mediatheque dumbea`
- Recherche multi-index : `index=address,poi,parcel`

### Autocomplétion

- Saisie assistée avec pertinence des résultats
- Suggestion contextuelle (via lat/lon)

### Géocodage inversé (`/reverse`)

- À partir d'une paire de coordonnées (lat/lon), retrouver la localisation la plus proche

### Filtres disponibles

- Par commune (code INSEE ou nom)
- Par catégorie de POI (pour l'index "poi")
- Par type de résultat (street, housenumber, etc.) (pour l'index "adress")


## 🥇 Bonnes pratiques d’intégration

- Utilisez l'index `poi` pour les **tribus**, **équipements publics**, **voies non adressées**, etc.
- Affichez le **type de résultat** dans l'UI (ex : "Parcelle cadastrale", "Tribu", "Adresse")
- Limitez les résultats à 10 ou 20 pour optimiser l'affichage
- Utilisez les filtres de contexte (commune, catégorie de POI, type de POI, etc.) pour améliorer la précision
- ℹ️ À noter : dans l'index "address", les voies nommées issues de la [Base Adresse Nationale (BAN)](https://adresse.data.gouv.fr/) sont représentées par un point central (appelé "centroïde de voie") utilisé pour centrer la carte lors d’une recherche. Ce comportement permet d’afficher une emprise cartographique complète ("box") autour de la voie, mais ne garantit pas que l'on récupère l'ensemble des adresses présentes sur cette voie. Il peut aussi y avoir doublon avec l’index "poi" si cette voie est également recensée comme point d’intérêt. Pensez à détermliner des règles de gestion appropriées à vos besoin ou à documenter ce point dans votre interface utilisateur si besoin.

---

## 📊 Exemples d'appels d'API

GET /search?q=127 rue daly&index=address  
GET /search?q=lot 18 koniambo&index=parcel   
GET /search?q=mediatheque dumbea&index=poi,address  
GET /reverse?lat=-22.255&lon=166.451  

## 🚧 Evolutions prévues / Modifications en cours (mars 2025)
- Les catégories de POI sont susceptibles d'être affinées au cours du temps

## 🔗 Ressources utiles
- Page de vulgarisation du sujet "Localisation" : guide.data.gouv.nc/open-data-public/donnees-a-forte-valeur/referentiel-de-localisation
- Documentation Swagger : https://localisation.gouv.nc/api/openapi
- Contact technique : data@gouv.nc
