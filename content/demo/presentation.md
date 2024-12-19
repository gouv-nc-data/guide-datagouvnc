+++
title = 'Echantillon de code'
date = 2024-10-10T15:58:39+11:00
weight = 1
+++

# Test des differentes parties du site
## Titre numeroté 
Pour numéroté les differents titre , il faudra entrer manuellement les differents chiffre
{{<code>}}## 1. titre 1 
paragraphe de la section 1
## 2. titre 2
paragraphe de la section 2
{{</code>}}
## Image 
Pour ajouter une image dans les pages, il faut utiliser le markdown : 
{{<code>}}[text-alternatif](lien ou chemin de l'image){{</code>}}
![Test Image](https://icons.iconarchive.com/icons/martz90/circle/256/video-camera-icon.png)

## Video
Pour ajouter une video youtube dans les pages , il faut utiliser le shortcode {{youtube}}:
{{<code>}}< video id="identifiant de la video youtube">{{</code>}}
{{< video id="ns3w4xDFAq8?si=HLA0nm51J4edQTKL" >}}

## Echantillon de code
Pour intégrer des échantillon de code dans les pages, tu peux utiliser
- le markdown " `` "
- le shortcode {{code}}:

###  le markdown " `` "
Utilisez des accents graves (`) pour créer des styles de code intraligne au sein d’un paragraphe. 


Voci un exemple : ``function test() {
 console.log("notice the blank line before this function?"); }``

### Le shortcode {{code}}
{{< code >}}{< code >}
contenu du code 
{< /code >}{{< /code >}}


## Notice 

Pour intégrer des encart informative dans les pages, il faut utiliser le shortcode {{notice}}: 

{{<code>}}type = "info" ,"warning","error" 
{< notice type="" title="Titre de l'encart">}
Contenu de l'encart
{< /notice >}{{</code>}}

### Exemples
#### Notice Informative
{{< notice type="info" title="Information">}}
Please find a list of our real-time APIs [here](#).
{{< /notice >}}
#### Notice Attention
{{< notice type="warning" >}}
Please find a list of our real-time APIs [here](#).
{{< /notice >}}
#### Notice Erreur
{{< notice type="error" >}}
Please find a list of our real-time APIs [here](#).
{{< /notice >}}


## Tableau 

Pour ajouter un Tableau dans les pages , il faut utiliser le markdown : 
{{<code>}}| Dataset Name       | Format   | Size   | Last Updated | Accessibility   |
|--------------------|----------|--------|--------------|-----------------|
| Population Data    | CSV      | 2 MB   | 2024-10-01   | Public          |
| Weather Statistics | JSON     | 5 MB   | 2024-09-20   | Public          |
| Traffic Reports    | XML      | 3 MB   | 2024-10-05   | Restricted      |
| COVID-19 Cases     | XLSX     | 4 MB   | 2024-10-08   | Public          |
| Economic Indicators| PDF      | 1 MB   | 2024-09-25   | Public          |{{</code>}}
### Exemple


| Dataset Name       | Format   | Size   | Last Updated | Accessibility   |
|--------------------|----------|--------|--------------|-----------------|
| Population Data    | CSV      | 2 MB   | 2024-10-01   | Public          |
| Weather Statistics | JSON     | 5 MB   | 2024-09-20   | Public          |
| Traffic Reports    | XML      | 3 MB   | 2024-10-05   | Restricted      |
| COVID-19 Cases     | XLSX     | 4 MB   | 2024-10-08   | Public          |
| Economic Indicators| PDF      | 1 MB   | 2024-09-25   | Public          |


## Bouton 
Ce bouton respecte le disign systeme du futur Data gouv NC V2
Pour ajouter un bouton dans les pages , il faut utliser le shortcode {{button}}: 

{{<code>}}{< button href="le lien de la page" >}
Intitulé du bouton
{< /button >}{{</code>}}
### Exemple
{{< button href="https://data.gouv.nc" >}}
Accéder à data.gouv.nc
{{< /button >}}

## Lien "a"

Pour ajouter un lien dans les pages , il faut utiliser le markdown : 
{{<code>}}[Texte cliquable](Lien de la page){{</code>}}
[Accéder à data.gouv.nc](https://data.gouv.nc)
## Foire Aux Questions (FAQ)
Pour ajouter une foire aux questions, il faut utiliser le shortcode {{faq}} :
{{<code>}}{< faq question="Question posée" >}
Réponses
{< /faq >}{{</code>}}
### Exemple
{{< faq question="Comment installer Hugo ?" >}}
Téléchargez Hugo à partir du site officiel et suivez les instructions d'installation pour votre système d'exploitation.
{{< /faq >}}
{{< faq question="Comment utiliser un theme Hugo ?" >}}
Téléchargez Hugo à partir du site officiel et suivez les instructions d'installation pour votre système d'exploitation.
{{< /faq >}}


## Tabs
Pour ajouter un Tabs dans les pages , il faut utliser les shortcodes {{tabs}} et {{tab}}: 
{{<code>}}{< tabs >}
    {< tab id="1" name="Onglet 1" checked="checked" >}
    Contenu du premier onglet.
    {< /tab >}

    {< tab id="2" name="Onglet 2" >}
    Contenu du deuxième onglet.
    {< /tab >}
{< /tabs >}{{</code>}}

### Exemple
{{< tabs >}}

    {{< tab id="1" name="Onglet 1" checked="checked" >}}
    Contenu du premier onglet.
    {{< /tab >}}

    {{< tab id="2" name="Onglet 2" >}}
    Contenu du deuxième onglet.
    {{< /tab >}}

{{< /tabs >}}

## Chronologie des versions
Pour ajouter une timeline dans les pages , il faut utliser les shortcodes {{timeline}} et {{timeline-item}}: 
{{<code>}}{< timeline >}
    {< timeline-item date="01/01/2024" >}
    Version 1.0 - Lancement initial.
    {< /timeline-item >}{{</code>}}
### Exemple
{{< timeline >}}
    {{< timeline-item date="01/01/2024" >}}
    Version 1.0 - Lancement initial.
    {{< /timeline-item >}}

    {{< timeline-item date="01/11/2024" >}}
    Version 1.1 - Ajout de nouvelles fonctionnalités.
    {{< /timeline-item >}}
{{< /timeline >}}


## Glossaire
Pour ajouter une timeline dans les pages , il faut utliser les shortcodes {{glossary}} et {{glossary-item}}: 
{{<code>}}{< glossary title="Titre du Glossaire" >}
{< glossary-term term="Mot à définir" >}
Définition
{< /glossary-term >}
{< /glossary >}{{</code>}}

### Exemple
{{< glossary title="Glossaire technique" >}}
{{< glossary-term term="API" >}}
Interface de programmation d'application, permet à deux applications de communiquer entre elles.
{{< /glossary-term >}}
{{< /glossary >}}

## Colonne
{{< columns ratio="4:2" class="my-custom-class" >}}
<div>Contenu de la première colonne</div>
<---> 
<div>Contenu de la deuxième colonne</div>
<---> 
<div>Contenu de la deuxième colonne</div>
<---> 
<div>Contenu de la deuxième colonne</div>
<div>Contenu de la deuxième colonne</div>
{{< /columns >}}

## Hint
{{< hint type="danger" title="Information" >}}
  Ceci est un exemple d'astuce ou d'information supplémentaire.
{{< /hint >}}


## Formule de math
{{< katex >}}
  a^2 + b^2 = c^2
{{< /katex >}}


