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

L'[API Localisation](https://localisation.gouv.nc/api/openapi) est un service public numérique permettant de rechercher, vérifier et géolocaliser des lieux sur l'ensemble du territoire calédonien, même en l'absence d'adresses.

Elle s'adresse aux développeurs d'applications métiers, de portails citoyens, ou de SI internes souhaitant :
- Uniformiser la saisie des localisations
- Améliorer la précision et la qualité des données collectées
- Permettre une interopérabilité entre les services

API REST conforme OpenAPI 3.0 (swagger disponible).

➡️ [Accéder à l'API REST conforme OpenAPI 3.0 (swagger disponible)](https://localisation.gouv.nc/api/openapi)  
➡️ [Comprendre ce qu'est le référentiel de localisation de Nouvelle-Calédonie](https://guide.data.gouv.nc/open-data-public/donnees-a-forte-valeur/referentiel-de-localisation/)  


## 📚 Sources de données utilisées par l’API

L’API Localisation de Nouvelle-Calédonie interroge trois sources principales :

- **Les adresses** : extraites de la [Base Adresse Nationale (BAN)](https://adresse.data.gouv.fr/), pour les communes adressées. Elles permettent d’obtenir des résultats de type `housenumber` (numéro d'adresse précise) ou `street` (centroïde de voie adressée).
- **Les points d’intérêt (POI)** : lieux significatifs (tribus, équipements publics, lieux-dits, voies nommées dans les communes non adressées, immeubles, etc.).
- **Les parcelles cadastrales** : via le cadastre géré à l’échelle du territoire (hors province des Îles).

Ces trois sources sont interrogées selon le ou les `index` spécifiés dans les appels API (`address`, `poi`, `cadastre`).



## 🔢 Fonctionnalités principales

### Recherche directe (`/search`)

- Recherche par chaîne de caractères : `?q=mediatheque dumbea`
- Recherche multi-index : `index=address,poi,cadastre`

### Exemples :
`GET /search?q=127 rue daly&index=address`  
`GET /search?q=lot 18 koniambo&index=parcel`   
`GET /search?q=mediatheque dumbea&index=poi,address`  

### Autocomplétion

- Saisie assistée avec pertinence des résultats
- Suggestion contextuelle (via lat/lon)

### Géocodage inversé (`/reverse`)

- À partir d'une paire de coordonnées (lat/lon), retrouver la localisation la plus proche

### Exemple :
`GET /reverse?lat=-22.255&lon=166.451`  

### Filtres disponibles

- Par commune (code INSEE ou nom)
- Par catégorie de POI (pour l'index `poi`)
- Par type de résultat (street, housenumber, etc.) (pour l'index `adress`)


## 🥇 Bonnes pratiques d’intégration

- Utilisez l'index `poi` pour les **tribus**, **équipements publics**, **voies non adressées**, etc.
- Affichez le **type de résultat** dans l'UI (ex : "Parcelle cadastrale", "Tribu", "Adresse")
- Limitez les résultats à 10 ou 20 pour optimiser l'affichage
- Utilisez les filtres de contexte (commune, catégorie de POI, type de POI, etc.) pour améliorer la précision
  
## ⚠️ Point d'attention : comprendre les types de résultats et éviter les doublons

ℹ️ À noter : selon l’index utilisé dans votre requête, le comportement de l’API diffère.  
Voici les trois cas principaux à connaître :

1. **Index `address` – recherche par numéro de rue**  
Une recherche comme `GET /search?q=127 daly&index=address&type=housenumber` retourne les données précises de l’adresse, avec coordonnées géographiques exactes. Ce type de résultat est possible uniquement si cette adresse est bien enregistrée dans la [Base Adresse Nationale (BAN)](https://adresse.data.gouv.fr/).  

2. **Index `address` – recherche par nom de rue sans numéro**
Une recherche comme `GET /search?q=arnold daly&index=address&type=street` retourne un centroïde de voie (point central calculé) associé à une emprise géographique (ou "box"). Ce résultat représente la rue dans son ensemble, utile pour un affichage cartographique qui englobe l'ensemble de la voie, mais ne contient pas les adresses précises (numéros de rue).  
ℹ️ À noter : Le centroïde peut être situé en dehors de la rue, notamment lorsqu’elle est courbe, comme c’est le cas pour rue Arnold Daly. Ce comportement est hérité de la [Base Adresse Nationale (BAN)](https://adresse.data.gouv.fr/), et n'est possible que dans les communes adressées.

3. **Index `poi` – voie nommée comme point d’intérêt**
Certaines voies ont été référencées comme points d’intérêt (POI), qu’elles soient dans des communes adressées ou non adressées. Une recherche comme `GET /search?q=arnold daly&index=poi` retournera un point situé directement sur la voie elle-même, au milieu de celle-ci.  
👉 Très utile dans les communes non adressées, cela permet de localiser une rue, même en l’absence de toute adresse postale.  
⚠️ Dans les communes déjà adressées, cela peut provoquer un doublon avec le centroïde généré par la BAN via l’index `address`, même si la logique technique est différente:  
- le point POI est sur la rue, au milieu de celle-ci
- tandis que le centroïde de l’index `address` peut être en dehors de la rue, car il est calculé pour encadrer l’ensemble de la voie.
  
⚠️ **Attention particulière à l’autocomplétion :** si vous activez l’autocomplétion avec plusieurs index (poi, address, etc.), l’utilisateur final pourrait se retrouver avec plusieurs suggestions identiques en apparence, sans savoir lequel choisir. Cela engendre des risques :
- Choix aléatoire d’un résultat sans compréhension du type
- Données hétérogènes dans vos bases
👉 Pour éviter de désorienter les utilisateurs finaux, il est recommandé aux développeurs :
- de définir des règles métier explicites en priorisant un index selon le contexte d’usage,
- de filtrer et structurer les résultats par type, notamment dans les suggestions de l’autocomplétion,
- ou d’afficher clairement le type de résultat retourné
- ou d’exclure certains doublons dans les traitements si nécessaire.

---

## 🚧 Evolutions prévues
- Les catégories de POI sont susceptibles d'être affinées au cours du temps

## 🔗 Ressources utiles
- [Page de vulgarisation sur le référentiel de localisation](https://guide.data.gouv.nc/open-data-public/donnees-a-forte-valeur/referentiel-de-localisation/) 
- [Documentation Swagger](https://localisation.gouv.nc/api/openapi)
- Contact technique : data@gouv.nc
