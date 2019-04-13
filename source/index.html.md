---
title: Institut.io API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
#  - ruby
#  - python
#  - javascript

toc_footers:
  - <a href='https://www.institut.io' target='_blank'>Sign up for an account</a>
  - <a href='https://api.institut.io/admin/login' target='_blank'>Login to your account</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Institut.io API! You can use our API to access an organization's training courses and related information.

An organization that has an account on Institut.io can administer its own data (training courses, schedules, training centers, etc.) in Institut.io's backoffice.

Any media, whether it be owned by the organization or by a third party such as a training course marketplace, can retrieve the organization's data thanks to the API using the right key.

# Search Engine

Institut.io implements Elasticsearch, which provides great performance and flexibility to the training courses search engine.

Elasticsearch is the most popular enterprise search engine in the world, as it combines great performance with simplicity, adaptability and scalability. For detailed information, please visit <a href="https://www.elastic.co/products/elasticsearch" target="&#95;blank">Elasticsearch's website</a>

# Administration

All data indexed in Institut.io's search engine is administered in a backoffice provided by Institut.io to the administrators of every account.

To access your account's backoffice, visit the <a href="https://api.institut.io/admin/login" target="&#95;blank">Institut.io's login page</a> and use the credentials provided when subscribing to an account. A password retrieval procedure can be accessed from the login page.

# Authentication

> To authorize, use this code:

```shell
# With cUrl, you can just pass the correct header with each request
curl https://api.institut.io/last_part_of_url  \
  -H "Authorization: api_key"
```

> Make sure to replace `api_key` with your API key and `last_part_of_url` with an API endpoint's URL.

Institut.io uses API keys to allow access to the API.

When subscribing to an Institut.io account, an organization is granted an API key, referred to in this documentation as <code>api_key</code>.

You can register an Institut.io account on <a href="https://www.institut.io" target="&#95;blank">Institut.io's website</a>.

Institut.io expects for the API key to be included in all API requests to the server in the request header. The password field should be left blank.

Header | Value | Description
--------- | ------- | -----------
Authorization | api_key | API key granted by Institut.io to a registered account

<aside class="notice">
Institut.io operates exclusively over HTTPS. Requests that are received over HTTP without encryption will fail.
</aside>

# Accounts

## Account Creation

An Account can be created free of payment, capture or any kind of commitment, using the <a href="https://www.institut.io" target="&#95;blank">Institut.io's website</a>.

## Account Object

The Account object contains information about an Institut.io account.

Property | Type | Description
--------- | ------- | -----------
<code>id</code> | <code>int</code> | The ID of the Account
<code>title</code> | <code>string</code> | The title of the Account
<code>coverImage</code> | <code>array</code> | Information about the Image that is linked to the Account as its cover image


# Courses

## Get All Courses

```shell
curl https://api.institut.io/courses  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "Animer des réunions en anglais",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 5,
            "value": "cours par téléphone"
        },
        "summary": "Pour s'adapter au mieux aux contraintes horaires des professionnels en activité, cette formation à l'animation de réunions professionnelles en anglais est dispensée sous la forme de conversations téléphoniques hebdomadaires avec un formateur natif.",
        "goal": "Préparer et animer des séances de travail ou des réunions.\r\nFaire un exposé, une présentation face à un auditoire.\r\nParticiper à une téléconférence.",
        "description": null,
        "targetedSkills": "Etre à l'aise pour animer des réunions professionnelles.",
        "programme": null,
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/4a0d4bae4767206fdf5c492f3926f960.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_4a0d4bae4767206fdf5c492f3926f960.jpeg",
            "alt": "Anglais"
        },
        "domains": [
            {
                "id": 5,
                "title": "Anglais"
            }
        ],
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1572825600
    },
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "La formation Excel Initiation vous apprendra à maîtriser les fonctionnalités fondamentales du tableur de Microsoft Office.",
        "goal": "Maîtriser les fonctionnalités fondamentales d'Excel\r\nConcevoir et exploiter des tableaux en utilisant des formules de calculs simples\r\nIllustrer des valeurs avec un graphique\r\nUtiliser des listes de données \r\nMettre en forme les données\r\nMettre en page et imprimer un tableau dans Excel",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>D&eacute;couvrir Excel</h2>\r\n<ul>\r\n<li>D&eacute;couverte du&nbsp;tableur</li>\r\n<li>G&eacute;n&eacute;ralit&eacute;s sur l'environnement&nbsp;Excel</li>\r\n<li>Le&nbsp;ruban&nbsp;fichier</li>\r\n<li>Ouverture d'un classeur</li>\r\n<li>Gestion&nbsp;des&nbsp;fen&ecirc;tres</li>\r\n<li>D&eacute;placement dans un&nbsp;classeur</li>\r\n<li>Saisie de&nbsp;donn&eacute;es&nbsp;dans&nbsp;Excel</li>\r\n<li>Modification du&nbsp;contenu d'une cellule</li>\r\n<li>S&eacute;lection et&nbsp;effacement de&nbsp;cellules</li>\r\n<li>Annulation et&nbsp;r&eacute;tablissement d'une action</li>\r\n<li>Enregistrement d'un classeur</li>\r\n<li>La&nbsp;zone \"Dites-nous ce&nbsp;que vous voulez faire\"&nbsp;: outil d'aide &agrave;&nbsp;la&nbsp;r&eacute;alisation d'actions*</li>\r\n</ul>\r\n<h2>R&eacute;aliser les&nbsp;premiers calculs&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Saisie d'une formule de&nbsp;calcul</li>\r\n<li>Calcul d'une somme ou&nbsp;autre statistique simple</li>\r\n<li>Calcul d'un pourcentage</li>\r\n<li>R&eacute;f&eacute;rence absolue dans une&nbsp;formule</li>\r\n<li>Copie vers des&nbsp;cellules adjacentes</li>\r\n<li>Copie vers des&nbsp;cellules non adjacentes</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;donn&eacute;es&nbsp;sous&nbsp;Excel</h2>\r\n<ul>\r\n<li>Formats num&eacute;riques simples</li>\r\n<li>Police et&nbsp;taille des&nbsp;caract&egrave;res</li>\r\n<li>Alignement des&nbsp;cellules</li>\r\n<li>Couleur des&nbsp;cellules</li>\r\n<li>Bordure des&nbsp;cellules</li>\r\n<li>Utiliser les&nbsp;th&egrave;mes et&nbsp;les styles pour la&nbsp;mise en forme&nbsp;dans&nbsp;Excel</li>\r\n<li>Capture d'&eacute;cran</li>\r\n</ul>\r\n<h2>G&eacute;rer les&nbsp;cellules&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Zoom d'affichage</li>\r\n<li>Le&nbsp;mode plein &eacute;cran</li>\r\n<li>Largeur de&nbsp;colonne / hauteur de&nbsp;ligne</li>\r\n<li>Insertion / suppression de&nbsp;lignes, de&nbsp;colonnes...</li>\r\n<li>D&eacute;placement de&nbsp;cellules</li>\r\n<li>Copie rapide de&nbsp;la mise en forme d'une cellule</li>\r\n<li>Fusion de&nbsp;cellules</li>\r\n<li>Orientation</li>\r\n<li>Affichage de&nbsp;plusieurs lignes dans une&nbsp;cellule</li>\r\n<li>Conserver la&nbsp;copie</li>\r\n<li>Copie de&nbsp;r&eacute;sultats de&nbsp;calcul&nbsp;</li>\r\n</ul>\r\n<h2>Imprimer et&nbsp;diffuser un&nbsp;classeur&nbsp;Excel</h2>\r\n<ul>\r\n<li>Mise en page</li>\r\n<li>Aper&ccedil;u et&nbsp;impression</li>\r\n<li>Titres de&nbsp;colonnes / lignes r&eacute;p&eacute;t&eacute;s &agrave;&nbsp;l'impression</li>\r\n<li>Masquage des&nbsp;&eacute;l&eacute;ments d'une feuille</li>\r\n<li>Zone d'impression</li>\r\n<li>Saut de&nbsp;page</li>\r\n<li>En-t&ecirc;te et&nbsp;pied de&nbsp;page</li>\r\n<li>Pr&eacute;sentation d&rsquo;un tableau en ligne</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;chiffres avec des&nbsp;graphiques&nbsp;simples</h2>\r\n<ul>\r\n<li>Outil d'aide au&nbsp;choix du&nbsp;type de&nbsp;graphique</li>\r\n<li>Cr&eacute;ation et&nbsp;d&eacute;placement d'un graphique</li>\r\n<li>Styles&nbsp;et&nbsp;dispositions&nbsp;</li>\r\n<li>S&eacute;lection et&nbsp;mise&nbsp;en&nbsp;forme&nbsp;des &eacute;l&eacute;ments d'un graphique</li>\r\n<li>Modification des&nbsp;&eacute;l&eacute;ments texte du&nbsp;graphique</li>\r\n<li>L&eacute;gende et&nbsp;zone de&nbsp;tra&ccedil;age</li>\r\n</ul>\r\n<h2>Utiliser des&nbsp;listes&nbsp;de&nbsp;donn&eacute;es&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un tableau de&nbsp;type liste de&nbsp;donn&eacute;es</li>\r\n<li>Utilisation du&nbsp;remplissage instantan&eacute;</li>\r\n<li>Tris</li>\r\n<li>Filtres automatiques</li>\r\n<li>Calculs automatiques dans un&nbsp;tableau&nbsp;Excel</li>\r\n<li>Filtrer dynamiquement avec les&nbsp;Segments</li>\r\n</ul>\r\n<h2>Personnaliser les&nbsp;feuilles des&nbsp;classeurs&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un nouveau classeur</li>\r\n<li>Nom d'une feuille, couleur de&nbsp;l'onglet</li>\r\n<li>Insertion, suppression de&nbsp;feuilles</li>\r\n<li>D&eacute;placement, copie et&nbsp;masquage d'une feuille</li>\r\n</ul>\r\n<p>&nbsp;</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/2c8ef4e045eca260e4661698e029b125.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_2c8ef4e045eca260e4661698e029b125.jpeg",
            "alt": "Excel"
        },
        "domains": [
            {
                "id": 8,
                "title": "Excel"
            }
        ],
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "typicalLearningTime": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ]
    },
    {
        "id": 3,
        "title": "Management d'équipe",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "Une formation pour apprendre au manager à faire progresser collectivement son équipe, au service d'objectifs communs",
        "goal": "Identifier les conditions d’efficacité du management de proximité\r\nMettre en œuvre les outils et méthodes pour animer une équipe au quotidien et se positionner en tant que responsable d’équipe",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>Se positionner en tant que manager</h2>\r\n<p>Introduction au&nbsp;management d'&eacute;quipe</p>\r\n<p>La posture du manager&nbsp;</p>\r\n<h2>Conna&icirc;tre&nbsp;les diff&eacute;rents styles de management</h2>\r\n<p>Identifier les styles de management</p>\r\n<p>Analyser les forces et les faiblesses de chacun de ces styles</p>\r\n<h2>Adopter en toute situation un comportement&nbsp;de manager</h2>\r\n<p>Revue des&nbsp;comportements&nbsp;&agrave; adopter&nbsp;en situation de crise</p>\r\n<p>S'affirmer simplement plut&ocirc;t que d'adopter un&nbsp;comportement de fuite, attaque ou manipulation</p>\r\n<h2>Exercer une autorit&eacute; positive en affirmant sa confiance en soi</h2>\r\n<p>Mettre en &eacute;vidence ses attitudes&nbsp;spontan&eacute;es</p>\r\n<p>Cr&eacute;er les conditions&nbsp;d'une relation de confiance&nbsp;avec ses collaborateurs</p>\r\n<h2>Organiser, animer et&nbsp;entra&icirc;ner son &eacute;quipe</h2>\r\n<p>Clarifier les r&ocirc;les dans l'&eacute;quipe et d&eacute;finir les objectifs</p>\r\n<p>Motiver les membres de son &eacute;quipe</p>\r\n<p>Manager d'anciens coll&egrave;gues et des coll&egrave;gues plus &acirc;g&eacute;s</p>\r\n<p>Am&eacute;liorer la performance de l'&eacute;quipe gr&acirc;ce &agrave; un management adapt&eacute;</p>\r\n<p>Orienter l'action collective</p>\r\n<h2>Communiquer efficacement</h2>\r\n<p>Adopter les attitudes ad&eacute;quates dans la relation de face-&agrave;-face</p>\r\n<p>Faire face aux conflits et situations difficiles</p>\r\n<p>Savoir formuler et recevoir une critique</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "alt": "Management"
        },
        "domains": [
            {
                "id": 3,
                "title": "Management et leadership"
            }
        ],
        "priceInter": {
            "amount": "1800.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "2160.00",
            "discountType": "percent",
            "discountAmount": "15.00",
            "discountedPrice": "1530.00"
        },
        "priceIntra": {
            "amount": "6600.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "7920.00"
        },
        "duration": {
            "canonical": 259200,
            "days": 3
        },
        "typicalLearningTime": {
            "canonical": 259200,
            "days": 3
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1557705600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 1,
                "title": "Omega Formation Lyon",
                "city": "Lyon",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            },
            {
                "id": 6,
                "title": "Regus Bordeaux",
                "city": "Bordeaux",
                "country": "France"
            }
        ]
    }
]
```

This endpoint retrieves all Courses.

### HTTP Request

`GET https://api.institut.io/courses`

### Response Fields

Field | Description
--------- | -----------
id | Identifier of the course

## Get A Specific Course

```shell
curl https://api.institut.io/courses/1  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "La formation Excel Initiation vous apprendra à maîtriser les fonctionnalités fondamentales du tableur de Microsoft Office.",
        "goal": "Maîtriser les fonctionnalités fondamentales d'Excel\r\nConcevoir et exploiter des tableaux en utilisant des formules de calculs simples\r\nIllustrer des valeurs avec un graphique\r\nUtiliser des listes de données \r\nMettre en forme les données\r\nMettre en page et imprimer un tableau dans Excel",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>D&eacute;couvrir Excel</h2>\r\n<ul>\r\n<li>D&eacute;couverte du&nbsp;tableur</li>\r\n<li>G&eacute;n&eacute;ralit&eacute;s sur l'environnement&nbsp;Excel</li>\r\n<li>Le&nbsp;ruban&nbsp;fichier</li>\r\n<li>Ouverture d'un classeur</li>\r\n<li>Gestion&nbsp;des&nbsp;fen&ecirc;tres</li>\r\n<li>D&eacute;placement dans un&nbsp;classeur</li>\r\n<li>Saisie de&nbsp;donn&eacute;es&nbsp;dans&nbsp;Excel</li>\r\n<li>Modification du&nbsp;contenu d'une cellule</li>\r\n<li>S&eacute;lection et&nbsp;effacement de&nbsp;cellules</li>\r\n<li>Annulation et&nbsp;r&eacute;tablissement d'une action</li>\r\n<li>Enregistrement d'un classeur</li>\r\n<li>La&nbsp;zone \"Dites-nous ce&nbsp;que vous voulez faire\"&nbsp;: outil d'aide &agrave;&nbsp;la&nbsp;r&eacute;alisation d'actions*</li>\r\n</ul>\r\n<h2>R&eacute;aliser les&nbsp;premiers calculs&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Saisie d'une formule de&nbsp;calcul</li>\r\n<li>Calcul d'une somme ou&nbsp;autre statistique simple</li>\r\n<li>Calcul d'un pourcentage</li>\r\n<li>R&eacute;f&eacute;rence absolue dans une&nbsp;formule</li>\r\n<li>Copie vers des&nbsp;cellules adjacentes</li>\r\n<li>Copie vers des&nbsp;cellules non adjacentes</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;donn&eacute;es&nbsp;sous&nbsp;Excel</h2>\r\n<ul>\r\n<li>Formats num&eacute;riques simples</li>\r\n<li>Police et&nbsp;taille des&nbsp;caract&egrave;res</li>\r\n<li>Alignement des&nbsp;cellules</li>\r\n<li>Couleur des&nbsp;cellules</li>\r\n<li>Bordure des&nbsp;cellules</li>\r\n<li>Utiliser les&nbsp;th&egrave;mes et&nbsp;les styles pour la&nbsp;mise en forme&nbsp;dans&nbsp;Excel</li>\r\n<li>Capture d'&eacute;cran</li>\r\n</ul>\r\n<h2>G&eacute;rer les&nbsp;cellules&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Zoom d'affichage</li>\r\n<li>Le&nbsp;mode plein &eacute;cran</li>\r\n<li>Largeur de&nbsp;colonne / hauteur de&nbsp;ligne</li>\r\n<li>Insertion / suppression de&nbsp;lignes, de&nbsp;colonnes...</li>\r\n<li>D&eacute;placement de&nbsp;cellules</li>\r\n<li>Copie rapide de&nbsp;la mise en forme d'une cellule</li>\r\n<li>Fusion de&nbsp;cellules</li>\r\n<li>Orientation</li>\r\n<li>Affichage de&nbsp;plusieurs lignes dans une&nbsp;cellule</li>\r\n<li>Conserver la&nbsp;copie</li>\r\n<li>Copie de&nbsp;r&eacute;sultats de&nbsp;calcul&nbsp;</li>\r\n</ul>\r\n<h2>Imprimer et&nbsp;diffuser un&nbsp;classeur&nbsp;Excel</h2>\r\n<ul>\r\n<li>Mise en page</li>\r\n<li>Aper&ccedil;u et&nbsp;impression</li>\r\n<li>Titres de&nbsp;colonnes / lignes r&eacute;p&eacute;t&eacute;s &agrave;&nbsp;l'impression</li>\r\n<li>Masquage des&nbsp;&eacute;l&eacute;ments d'une feuille</li>\r\n<li>Zone d'impression</li>\r\n<li>Saut de&nbsp;page</li>\r\n<li>En-t&ecirc;te et&nbsp;pied de&nbsp;page</li>\r\n<li>Pr&eacute;sentation d&rsquo;un tableau en ligne</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;chiffres avec des&nbsp;graphiques&nbsp;simples</h2>\r\n<ul>\r\n<li>Outil d'aide au&nbsp;choix du&nbsp;type de&nbsp;graphique</li>\r\n<li>Cr&eacute;ation et&nbsp;d&eacute;placement d'un graphique</li>\r\n<li>Styles&nbsp;et&nbsp;dispositions&nbsp;</li>\r\n<li>S&eacute;lection et&nbsp;mise&nbsp;en&nbsp;forme&nbsp;des &eacute;l&eacute;ments d'un graphique</li>\r\n<li>Modification des&nbsp;&eacute;l&eacute;ments texte du&nbsp;graphique</li>\r\n<li>L&eacute;gende et&nbsp;zone de&nbsp;tra&ccedil;age</li>\r\n</ul>\r\n<h2>Utiliser des&nbsp;listes&nbsp;de&nbsp;donn&eacute;es&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un tableau de&nbsp;type liste de&nbsp;donn&eacute;es</li>\r\n<li>Utilisation du&nbsp;remplissage instantan&eacute;</li>\r\n<li>Tris</li>\r\n<li>Filtres automatiques</li>\r\n<li>Calculs automatiques dans un&nbsp;tableau&nbsp;Excel</li>\r\n<li>Filtrer dynamiquement avec les&nbsp;Segments</li>\r\n</ul>\r\n<h2>Personnaliser les&nbsp;feuilles des&nbsp;classeurs&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un nouveau classeur</li>\r\n<li>Nom d'une feuille, couleur de&nbsp;l'onglet</li>\r\n<li>Insertion, suppression de&nbsp;feuilles</li>\r\n<li>D&eacute;placement, copie et&nbsp;masquage d'une feuille</li>\r\n</ul>\r\n<p>&nbsp;</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/2c8ef4e045eca260e4661698e029b125.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_2c8ef4e045eca260e4661698e029b125.jpeg",
            "alt": "Excel"
        },
        "domains": [
            {
                "id": 8,
                "title": "Excel"
            }
        ],
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "typicalLearningTime": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ]
    }
]
```

This endpoint retrieves a specific course.

### HTTP Request

`GET https://api.institut.io/courses/<id>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the course to retrieve

### Response Fields

Name | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the Course
<code>title</code> | <code>string</code> | The title of the Course
<code>indexed</code> | <code>boolean</code> | Instruction whether the Course should be allowed to be indexed by search engine bots on the media making the API call
<code>account</code> | <code>array</code> | The Account which the Course is linked to on the media making the API calls
<code>owner</code> | <code>array</code> | The Account which owns the Course (ie which was used when creating the Course object)
<code>mode</code> | <code>array</code> | The learning Mode of the Course
<code>summary</code> | <code>string</code> | The summary of the Course
<code>goal</code> | <code>string</code> | The goal of the Course
<code>description</code> | <code>string</code> | The description of the Course
<code>targetedSkills</code> | <code>string</code> | The targeted skills of the Course
<code>programme</code> | <code>string</code> | The programme of the Course
<code>coverImage</code> | <code>array</code> | The cover Image of the Course
<code>priceInter</code> | <code>array</code> | The inter-organization Price of the Course
<code>priceIntra</code> | <code>array</code> | The intra-organization Price of the Course
<code>duration</code> | <code>array</code> | The duration of the Course
<code>typicalLearningTime</code> | <code>array</code> | The typical learning time of the Course
<code>count</code> | <code>array</code> | The number of sessions of the Course
<code>nextStartDate</code> | <code>int</code> | The timestamp of the Course's next start date
<code>nextOpenDate</code> | <code>int</code> | The timestamp of the Course's next opening date
<code>premises</code> | <code>array</code> | The Premises where the Course is scheduled

## Paginate

The "Get All Courses" endpoint can be queried with pagination parameters.

```shell
curl -g "https://api.institut.io/courses?paginate[from]=20&paginate[size]=10"  \
  -H "Authorization: ZKXvA9fE"
```

>The above command returns 10 Courses ranking from 21 to 30 (if the query without pagination parameters should return more than 30 results).

### HTTP Request

`GET https://api.institut.io/courses?paginate[from]=<first_result_ranking>&paginate[size]=<max_number_returned_results`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>first_result_ranking</code> | <code>int</code> | Ranking of the first result to be returned
<code>max_number_returned_results</code> | <code>int</code> | Maximum number of results to be returned



## Search An Expression

```shell
curl "https://api.institut.io/courses?expression=apprendre"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "http://localhost:8000/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "http://localhost:8000/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "La formation Excel Initiation vous apprendra à maîtriser les fonctionnalités fondamentales du tableur de Microsoft Office.",
        "goal": "Maîtriser les fonctionnalités fondamentales d'Excel\r\nConcevoir et exploiter des tableaux en utilisant des formules de calculs simples\r\nIllustrer des valeurs avec un graphique\r\nUtiliser des listes de données \r\nMettre en forme les données\r\nMettre en page et imprimer un tableau dans Excel",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>D&eacute;couvrir Excel</h2>\r\n<ul>\r\n<li>D&eacute;couverte du&nbsp;tableur</li>\r\n<li>G&eacute;n&eacute;ralit&eacute;s sur l'environnement&nbsp;Excel</li>\r\n<li>Le&nbsp;ruban&nbsp;fichier</li>\r\n<li>Ouverture d'un classeur</li>\r\n<li>Gestion&nbsp;des&nbsp;fen&ecirc;tres</li>\r\n<li>D&eacute;placement dans un&nbsp;classeur</li>\r\n<li>Saisie de&nbsp;donn&eacute;es&nbsp;dans&nbsp;Excel</li>\r\n<li>Modification du&nbsp;contenu d'une cellule</li>\r\n<li>S&eacute;lection et&nbsp;effacement de&nbsp;cellules</li>\r\n<li>Annulation et&nbsp;r&eacute;tablissement d'une action</li>\r\n<li>Enregistrement d'un classeur</li>\r\n<li>La&nbsp;zone \"Dites-nous ce&nbsp;que vous voulez faire\"&nbsp;: outil d'aide &agrave;&nbsp;la&nbsp;r&eacute;alisation d'actions*</li>\r\n</ul>\r\n<h2>R&eacute;aliser les&nbsp;premiers calculs&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Saisie d'une formule de&nbsp;calcul</li>\r\n<li>Calcul d'une somme ou&nbsp;autre statistique simple</li>\r\n<li>Calcul d'un pourcentage</li>\r\n<li>R&eacute;f&eacute;rence absolue dans une&nbsp;formule</li>\r\n<li>Copie vers des&nbsp;cellules adjacentes</li>\r\n<li>Copie vers des&nbsp;cellules non adjacentes</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;donn&eacute;es&nbsp;sous&nbsp;Excel</h2>\r\n<ul>\r\n<li>Formats num&eacute;riques simples</li>\r\n<li>Police et&nbsp;taille des&nbsp;caract&egrave;res</li>\r\n<li>Alignement des&nbsp;cellules</li>\r\n<li>Couleur des&nbsp;cellules</li>\r\n<li>Bordure des&nbsp;cellules</li>\r\n<li>Utiliser les&nbsp;th&egrave;mes et&nbsp;les styles pour la&nbsp;mise en forme&nbsp;dans&nbsp;Excel</li>\r\n<li>Capture d'&eacute;cran</li>\r\n</ul>\r\n<h2>G&eacute;rer les&nbsp;cellules&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Zoom d'affichage</li>\r\n<li>Le&nbsp;mode plein &eacute;cran</li>\r\n<li>Largeur de&nbsp;colonne / hauteur de&nbsp;ligne</li>\r\n<li>Insertion / suppression de&nbsp;lignes, de&nbsp;colonnes...</li>\r\n<li>D&eacute;placement de&nbsp;cellules</li>\r\n<li>Copie rapide de&nbsp;la mise en forme d'une cellule</li>\r\n<li>Fusion de&nbsp;cellules</li>\r\n<li>Orientation</li>\r\n<li>Affichage de&nbsp;plusieurs lignes dans une&nbsp;cellule</li>\r\n<li>Conserver la&nbsp;copie</li>\r\n<li>Copie de&nbsp;r&eacute;sultats de&nbsp;calcul&nbsp;</li>\r\n</ul>\r\n<h2>Imprimer et&nbsp;diffuser un&nbsp;classeur&nbsp;Excel</h2>\r\n<ul>\r\n<li>Mise en page</li>\r\n<li>Aper&ccedil;u et&nbsp;impression</li>\r\n<li>Titres de&nbsp;colonnes / lignes r&eacute;p&eacute;t&eacute;s &agrave;&nbsp;l'impression</li>\r\n<li>Masquage des&nbsp;&eacute;l&eacute;ments d'une feuille</li>\r\n<li>Zone d'impression</li>\r\n<li>Saut de&nbsp;page</li>\r\n<li>En-t&ecirc;te et&nbsp;pied de&nbsp;page</li>\r\n<li>Pr&eacute;sentation d&rsquo;un tableau en ligne</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;chiffres avec des&nbsp;graphiques&nbsp;simples</h2>\r\n<ul>\r\n<li>Outil d'aide au&nbsp;choix du&nbsp;type de&nbsp;graphique</li>\r\n<li>Cr&eacute;ation et&nbsp;d&eacute;placement d'un graphique</li>\r\n<li>Styles&nbsp;et&nbsp;dispositions&nbsp;</li>\r\n<li>S&eacute;lection et&nbsp;mise&nbsp;en&nbsp;forme&nbsp;des &eacute;l&eacute;ments d'un graphique</li>\r\n<li>Modification des&nbsp;&eacute;l&eacute;ments texte du&nbsp;graphique</li>\r\n<li>L&eacute;gende et&nbsp;zone de&nbsp;tra&ccedil;age</li>\r\n</ul>\r\n<h2>Utiliser des&nbsp;listes&nbsp;de&nbsp;donn&eacute;es&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un tableau de&nbsp;type liste de&nbsp;donn&eacute;es</li>\r\n<li>Utilisation du&nbsp;remplissage instantan&eacute;</li>\r\n<li>Tris</li>\r\n<li>Filtres automatiques</li>\r\n<li>Calculs automatiques dans un&nbsp;tableau&nbsp;Excel</li>\r\n<li>Filtrer dynamiquement avec les&nbsp;Segments</li>\r\n</ul>\r\n<h2>Personnaliser les&nbsp;feuilles des&nbsp;classeurs&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un nouveau classeur</li>\r\n<li>Nom d'une feuille, couleur de&nbsp;l'onglet</li>\r\n<li>Insertion, suppression de&nbsp;feuilles</li>\r\n<li>D&eacute;placement, copie et&nbsp;masquage d'une feuille</li>\r\n</ul>\r\n<p>&nbsp;</p>",
        "coverImage": {
            "file": "http://localhost:8000/uploads/images/2c8ef4e045eca260e4661698e029b125.jpeg",
            "thumb": "http://localhost:8000/uploads/images/_2c8ef4e045eca260e4661698e029b125.jpeg",
            "alt": "Excel"
        },
        "domains": [
            {
                "id": 8,
                "title": "Excel"
            }
        ],
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "typicalLearningTime": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ],
        "score": 6.822408
    },
    {
        "id": 3,
        "title": "Management d'équipe",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "http://localhost:8000/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "http://localhost:8000/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "Une formation pour apprendre au manager à faire progresser collectivement son équipe, au service d'objectifs communs",
        "goal": "Identifier les conditions d’efficacité du management de proximité\r\nMettre en œuvre les outils et méthodes pour animer une équipe au quotidien et se positionner en tant que responsable d’équipe",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>Se positionner en tant que manager</h2>\r\n<p>Introduction au&nbsp;management d'&eacute;quipe</p>\r\n<p>La posture du manager&nbsp;</p>\r\n<h2>Conna&icirc;tre&nbsp;les diff&eacute;rents styles de management</h2>\r\n<p>Identifier les styles de management</p>\r\n<p>Analyser les forces et les faiblesses de chacun de ces styles</p>\r\n<h2>Adopter en toute situation un comportement&nbsp;de manager</h2>\r\n<p>Revue des&nbsp;comportements&nbsp;&agrave; adopter&nbsp;en situation de crise</p>\r\n<p>S'affirmer simplement plut&ocirc;t que d'adopter un&nbsp;comportement de fuite, attaque ou manipulation</p>\r\n<h2>Exercer une autorit&eacute; positive en affirmant sa confiance en soi</h2>\r\n<p>Mettre en &eacute;vidence ses attitudes&nbsp;spontan&eacute;es</p>\r\n<p>Cr&eacute;er les conditions&nbsp;d'une relation de confiance&nbsp;avec ses collaborateurs</p>\r\n<h2>Organiser, animer et&nbsp;entra&icirc;ner son &eacute;quipe</h2>\r\n<p>Clarifier les r&ocirc;les dans l'&eacute;quipe et d&eacute;finir les objectifs</p>\r\n<p>Motiver les membres de son &eacute;quipe</p>\r\n<p>Manager d'anciens coll&egrave;gues et des coll&egrave;gues plus &acirc;g&eacute;s</p>\r\n<p>Am&eacute;liorer la performance de l'&eacute;quipe gr&acirc;ce &agrave; un management adapt&eacute;</p>\r\n<p>Orienter l'action collective</p>\r\n<h2>Communiquer efficacement</h2>\r\n<p>Adopter les attitudes ad&eacute;quates dans la relation de face-&agrave;-face</p>\r\n<p>Faire face aux conflits et situations difficiles</p>\r\n<p>Savoir formuler et recevoir une critique</p>",
        "coverImage": {
            "file": "http://localhost:8000/uploads/images/d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "thumb": "http://localhost:8000/uploads/images/_d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "alt": "Management"
        },
        "domains": [
            {
                "id": 3,
                "title": "Management et leadership"
            }
        ],
        "priceInter": {
            "amount": "1800.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "2160.00",
            "discountType": "percent",
            "discountAmount": "15.00",
            "discountedPrice": "1530.00"
        },
        "priceIntra": {
            "amount": "6600.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "7920.00"
        },
        "duration": {
            "canonical": 259200,
            "days": 3
        },
        "typicalLearningTime": {
            "canonical": 259200,
            "days": 3
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1557705600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 1,
                "title": "Omega Formation Lyon",
                "city": "Lyon",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            },
            {
                "id": 6,
                "title": "Regus Bordeaux",
                "city": "Bordeaux",
                "country": "France"
            }
        ],
        "score": 2.5891387
    }
]
```

This endpoint retrieves all Courses matching an expression.

The results of this query include an additional <code>score</code> field of type <code>decimal</code>. This fields ranks the results according to their relevance with the <code>expression</code> parameter. The most relevant results are ranked with the highest <code>score</code> values.

### HTTP Request

`GET https://api.institut.io/courses?expression=<expression>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>expression</code> | <code>string</code> | The searched expression

### Response Fields

The response includes a <code>score</code> field in addition to all fields returned by the queries that fetch one or several Courses.

Name | Type | Description
--------- | --------- | -----------
<code>score</code> | <code>decimal</code> | The score of the Course

## Filter By Domain

### Using Domain titles

```shell
curl -g "https://api.institut.io/courses?domains[titles]=Bureautique,Langues"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?domains[ids]=7,4"  \
  -H "Authorization: ZKXvA9fE"
```

> The two above commands return the same JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "Animer des réunions en anglais",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 5,
            "value": "cours par téléphone"
        },
        "summary": "Pour s'adapter au mieux aux contraintes horaires des professionnels en activité, cette formation à l'animation de réunions professionnelles en anglais est dispensée sous la forme de conversations téléphoniques hebdomadaires avec un formateur natif.",
        "goal": "Préparer et animer des séances de travail ou des réunions.\r\nFaire un exposé, une présentation face à un auditoire.\r\nParticiper à une téléconférence.",
        "description": null,
        "targetedSkills": "Etre à l'aise pour animer des réunions professionnelles.",
        "programme": null,
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/4a0d4bae4767206fdf5c492f3926f960.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_4a0d4bae4767206fdf5c492f3926f960.jpeg",
            "alt": "Anglais"
        },
        "domains": [
            {
                "id": 5,
                "title": "Anglais"
            }
        ],
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1572825600
    },
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "La formation Excel Initiation vous apprendra à maîtriser les fonctionnalités fondamentales du tableur de Microsoft Office.",
        "goal": "Maîtriser les fonctionnalités fondamentales d'Excel\r\nConcevoir et exploiter des tableaux en utilisant des formules de calculs simples\r\nIllustrer des valeurs avec un graphique\r\nUtiliser des listes de données \r\nMettre en forme les données\r\nMettre en page et imprimer un tableau dans Excel",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>D&eacute;couvrir Excel</h2>\r\n<ul>\r\n<li>D&eacute;couverte du&nbsp;tableur</li>\r\n<li>G&eacute;n&eacute;ralit&eacute;s sur l'environnement&nbsp;Excel</li>\r\n<li>Le&nbsp;ruban&nbsp;fichier</li>\r\n<li>Ouverture d'un classeur</li>\r\n<li>Gestion&nbsp;des&nbsp;fen&ecirc;tres</li>\r\n<li>D&eacute;placement dans un&nbsp;classeur</li>\r\n<li>Saisie de&nbsp;donn&eacute;es&nbsp;dans&nbsp;Excel</li>\r\n<li>Modification du&nbsp;contenu d'une cellule</li>\r\n<li>S&eacute;lection et&nbsp;effacement de&nbsp;cellules</li>\r\n<li>Annulation et&nbsp;r&eacute;tablissement d'une action</li>\r\n<li>Enregistrement d'un classeur</li>\r\n<li>La&nbsp;zone \"Dites-nous ce&nbsp;que vous voulez faire\"&nbsp;: outil d'aide &agrave;&nbsp;la&nbsp;r&eacute;alisation d'actions*</li>\r\n</ul>\r\n<h2>R&eacute;aliser les&nbsp;premiers calculs&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Saisie d'une formule de&nbsp;calcul</li>\r\n<li>Calcul d'une somme ou&nbsp;autre statistique simple</li>\r\n<li>Calcul d'un pourcentage</li>\r\n<li>R&eacute;f&eacute;rence absolue dans une&nbsp;formule</li>\r\n<li>Copie vers des&nbsp;cellules adjacentes</li>\r\n<li>Copie vers des&nbsp;cellules non adjacentes</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;donn&eacute;es&nbsp;sous&nbsp;Excel</h2>\r\n<ul>\r\n<li>Formats num&eacute;riques simples</li>\r\n<li>Police et&nbsp;taille des&nbsp;caract&egrave;res</li>\r\n<li>Alignement des&nbsp;cellules</li>\r\n<li>Couleur des&nbsp;cellules</li>\r\n<li>Bordure des&nbsp;cellules</li>\r\n<li>Utiliser les&nbsp;th&egrave;mes et&nbsp;les styles pour la&nbsp;mise en forme&nbsp;dans&nbsp;Excel</li>\r\n<li>Capture d'&eacute;cran</li>\r\n</ul>\r\n<h2>G&eacute;rer les&nbsp;cellules&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Zoom d'affichage</li>\r\n<li>Le&nbsp;mode plein &eacute;cran</li>\r\n<li>Largeur de&nbsp;colonne / hauteur de&nbsp;ligne</li>\r\n<li>Insertion / suppression de&nbsp;lignes, de&nbsp;colonnes...</li>\r\n<li>D&eacute;placement de&nbsp;cellules</li>\r\n<li>Copie rapide de&nbsp;la mise en forme d'une cellule</li>\r\n<li>Fusion de&nbsp;cellules</li>\r\n<li>Orientation</li>\r\n<li>Affichage de&nbsp;plusieurs lignes dans une&nbsp;cellule</li>\r\n<li>Conserver la&nbsp;copie</li>\r\n<li>Copie de&nbsp;r&eacute;sultats de&nbsp;calcul&nbsp;</li>\r\n</ul>\r\n<h2>Imprimer et&nbsp;diffuser un&nbsp;classeur&nbsp;Excel</h2>\r\n<ul>\r\n<li>Mise en page</li>\r\n<li>Aper&ccedil;u et&nbsp;impression</li>\r\n<li>Titres de&nbsp;colonnes / lignes r&eacute;p&eacute;t&eacute;s &agrave;&nbsp;l'impression</li>\r\n<li>Masquage des&nbsp;&eacute;l&eacute;ments d'une feuille</li>\r\n<li>Zone d'impression</li>\r\n<li>Saut de&nbsp;page</li>\r\n<li>En-t&ecirc;te et&nbsp;pied de&nbsp;page</li>\r\n<li>Pr&eacute;sentation d&rsquo;un tableau en ligne</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;chiffres avec des&nbsp;graphiques&nbsp;simples</h2>\r\n<ul>\r\n<li>Outil d'aide au&nbsp;choix du&nbsp;type de&nbsp;graphique</li>\r\n<li>Cr&eacute;ation et&nbsp;d&eacute;placement d'un graphique</li>\r\n<li>Styles&nbsp;et&nbsp;dispositions&nbsp;</li>\r\n<li>S&eacute;lection et&nbsp;mise&nbsp;en&nbsp;forme&nbsp;des &eacute;l&eacute;ments d'un graphique</li>\r\n<li>Modification des&nbsp;&eacute;l&eacute;ments texte du&nbsp;graphique</li>\r\n<li>L&eacute;gende et&nbsp;zone de&nbsp;tra&ccedil;age</li>\r\n</ul>\r\n<h2>Utiliser des&nbsp;listes&nbsp;de&nbsp;donn&eacute;es&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un tableau de&nbsp;type liste de&nbsp;donn&eacute;es</li>\r\n<li>Utilisation du&nbsp;remplissage instantan&eacute;</li>\r\n<li>Tris</li>\r\n<li>Filtres automatiques</li>\r\n<li>Calculs automatiques dans un&nbsp;tableau&nbsp;Excel</li>\r\n<li>Filtrer dynamiquement avec les&nbsp;Segments</li>\r\n</ul>\r\n<h2>Personnaliser les&nbsp;feuilles des&nbsp;classeurs&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un nouveau classeur</li>\r\n<li>Nom d'une feuille, couleur de&nbsp;l'onglet</li>\r\n<li>Insertion, suppression de&nbsp;feuilles</li>\r\n<li>D&eacute;placement, copie et&nbsp;masquage d'une feuille</li>\r\n</ul>\r\n<p>&nbsp;</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/2c8ef4e045eca260e4661698e029b125.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_2c8ef4e045eca260e4661698e029b125.jpeg",
            "alt": "Excel"
        },
        "domains": [
            {
                "id": 8,
                "title": "Excel"
            }
        ],
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "typicalLearningTime": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ]
    }
]
```

This endpoint retrieves all Courses linked to a Domain or one of its children.

### HTTP Request

`GET https://api.institut.io/courses?domains[titles]=<domain_titles>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>domain_titles</code> | <code>string</code> | The Domain titles, separated with comas

### Using Domain IDs

This endpoint retrieves all Courses linked to a Domain or one of its children.

### HTTP Request

`GET https://api.institut.io/courses?domains[ids]=<domain_ids>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>domain_ids</code> | <code>string</code> | The Domain IDs, separated with comas

## Filter By Mode

```shell
curl https://api.institut.io/courses?modes=onsite,mooc  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "La formation Excel Initiation vous apprendra à maîtriser les fonctionnalités fondamentales du tableur de Microsoft Office.",
        "goal": "Maîtriser les fonctionnalités fondamentales d'Excel\r\nConcevoir et exploiter des tableaux en utilisant des formules de calculs simples\r\nIllustrer des valeurs avec un graphique\r\nUtiliser des listes de données \r\nMettre en forme les données\r\nMettre en page et imprimer un tableau dans Excel",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>D&eacute;couvrir Excel</h2>\r\n<ul>\r\n<li>D&eacute;couverte du&nbsp;tableur</li>\r\n<li>G&eacute;n&eacute;ralit&eacute;s sur l'environnement&nbsp;Excel</li>\r\n<li>Le&nbsp;ruban&nbsp;fichier</li>\r\n<li>Ouverture d'un classeur</li>\r\n<li>Gestion&nbsp;des&nbsp;fen&ecirc;tres</li>\r\n<li>D&eacute;placement dans un&nbsp;classeur</li>\r\n<li>Saisie de&nbsp;donn&eacute;es&nbsp;dans&nbsp;Excel</li>\r\n<li>Modification du&nbsp;contenu d'une cellule</li>\r\n<li>S&eacute;lection et&nbsp;effacement de&nbsp;cellules</li>\r\n<li>Annulation et&nbsp;r&eacute;tablissement d'une action</li>\r\n<li>Enregistrement d'un classeur</li>\r\n<li>La&nbsp;zone \"Dites-nous ce&nbsp;que vous voulez faire\"&nbsp;: outil d'aide &agrave;&nbsp;la&nbsp;r&eacute;alisation d'actions*</li>\r\n</ul>\r\n<h2>R&eacute;aliser les&nbsp;premiers calculs&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Saisie d'une formule de&nbsp;calcul</li>\r\n<li>Calcul d'une somme ou&nbsp;autre statistique simple</li>\r\n<li>Calcul d'un pourcentage</li>\r\n<li>R&eacute;f&eacute;rence absolue dans une&nbsp;formule</li>\r\n<li>Copie vers des&nbsp;cellules adjacentes</li>\r\n<li>Copie vers des&nbsp;cellules non adjacentes</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;donn&eacute;es&nbsp;sous&nbsp;Excel</h2>\r\n<ul>\r\n<li>Formats num&eacute;riques simples</li>\r\n<li>Police et&nbsp;taille des&nbsp;caract&egrave;res</li>\r\n<li>Alignement des&nbsp;cellules</li>\r\n<li>Couleur des&nbsp;cellules</li>\r\n<li>Bordure des&nbsp;cellules</li>\r\n<li>Utiliser les&nbsp;th&egrave;mes et&nbsp;les styles pour la&nbsp;mise en forme&nbsp;dans&nbsp;Excel</li>\r\n<li>Capture d'&eacute;cran</li>\r\n</ul>\r\n<h2>G&eacute;rer les&nbsp;cellules&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Zoom d'affichage</li>\r\n<li>Le&nbsp;mode plein &eacute;cran</li>\r\n<li>Largeur de&nbsp;colonne / hauteur de&nbsp;ligne</li>\r\n<li>Insertion / suppression de&nbsp;lignes, de&nbsp;colonnes...</li>\r\n<li>D&eacute;placement de&nbsp;cellules</li>\r\n<li>Copie rapide de&nbsp;la mise en forme d'une cellule</li>\r\n<li>Fusion de&nbsp;cellules</li>\r\n<li>Orientation</li>\r\n<li>Affichage de&nbsp;plusieurs lignes dans une&nbsp;cellule</li>\r\n<li>Conserver la&nbsp;copie</li>\r\n<li>Copie de&nbsp;r&eacute;sultats de&nbsp;calcul&nbsp;</li>\r\n</ul>\r\n<h2>Imprimer et&nbsp;diffuser un&nbsp;classeur&nbsp;Excel</h2>\r\n<ul>\r\n<li>Mise en page</li>\r\n<li>Aper&ccedil;u et&nbsp;impression</li>\r\n<li>Titres de&nbsp;colonnes / lignes r&eacute;p&eacute;t&eacute;s &agrave;&nbsp;l'impression</li>\r\n<li>Masquage des&nbsp;&eacute;l&eacute;ments d'une feuille</li>\r\n<li>Zone d'impression</li>\r\n<li>Saut de&nbsp;page</li>\r\n<li>En-t&ecirc;te et&nbsp;pied de&nbsp;page</li>\r\n<li>Pr&eacute;sentation d&rsquo;un tableau en ligne</li>\r\n</ul>\r\n<h2>Pr&eacute;senter les&nbsp;chiffres avec des&nbsp;graphiques&nbsp;simples</h2>\r\n<ul>\r\n<li>Outil d'aide au&nbsp;choix du&nbsp;type de&nbsp;graphique</li>\r\n<li>Cr&eacute;ation et&nbsp;d&eacute;placement d'un graphique</li>\r\n<li>Styles&nbsp;et&nbsp;dispositions&nbsp;</li>\r\n<li>S&eacute;lection et&nbsp;mise&nbsp;en&nbsp;forme&nbsp;des &eacute;l&eacute;ments d'un graphique</li>\r\n<li>Modification des&nbsp;&eacute;l&eacute;ments texte du&nbsp;graphique</li>\r\n<li>L&eacute;gende et&nbsp;zone de&nbsp;tra&ccedil;age</li>\r\n</ul>\r\n<h2>Utiliser des&nbsp;listes&nbsp;de&nbsp;donn&eacute;es&nbsp;avec&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un tableau de&nbsp;type liste de&nbsp;donn&eacute;es</li>\r\n<li>Utilisation du&nbsp;remplissage instantan&eacute;</li>\r\n<li>Tris</li>\r\n<li>Filtres automatiques</li>\r\n<li>Calculs automatiques dans un&nbsp;tableau&nbsp;Excel</li>\r\n<li>Filtrer dynamiquement avec les&nbsp;Segments</li>\r\n</ul>\r\n<h2>Personnaliser les&nbsp;feuilles des&nbsp;classeurs&nbsp;dans&nbsp;Excel</h2>\r\n<ul>\r\n<li>Cr&eacute;ation d'un nouveau classeur</li>\r\n<li>Nom d'une feuille, couleur de&nbsp;l'onglet</li>\r\n<li>Insertion, suppression de&nbsp;feuilles</li>\r\n<li>D&eacute;placement, copie et&nbsp;masquage d'une feuille</li>\r\n</ul>\r\n<p>&nbsp;</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/2c8ef4e045eca260e4661698e029b125.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_2c8ef4e045eca260e4661698e029b125.jpeg",
            "alt": "Excel"
        },
        "domains": [
            {
                "id": 8,
                "title": "Excel"
            }
        ],
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "typicalLearningTime": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ]
    },
    {
        "id": 3,
        "title": "Management d'équipe",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "mode": {
            "id": 1,
            "value": "onsite"
        },
        "summary": "Une formation pour apprendre au manager à faire progresser collectivement son équipe, au service d'objectifs communs",
        "goal": "Identifier les conditions d’efficacité du management de proximité\r\nMettre en œuvre les outils et méthodes pour animer une équipe au quotidien et se positionner en tant que responsable d’équipe",
        "description": null,
        "targetedSkills": null,
        "programme": "<h2>Se positionner en tant que manager</h2>\r\n<p>Introduction au&nbsp;management d'&eacute;quipe</p>\r\n<p>La posture du manager&nbsp;</p>\r\n<h2>Conna&icirc;tre&nbsp;les diff&eacute;rents styles de management</h2>\r\n<p>Identifier les styles de management</p>\r\n<p>Analyser les forces et les faiblesses de chacun de ces styles</p>\r\n<h2>Adopter en toute situation un comportement&nbsp;de manager</h2>\r\n<p>Revue des&nbsp;comportements&nbsp;&agrave; adopter&nbsp;en situation de crise</p>\r\n<p>S'affirmer simplement plut&ocirc;t que d'adopter un&nbsp;comportement de fuite, attaque ou manipulation</p>\r\n<h2>Exercer une autorit&eacute; positive en affirmant sa confiance en soi</h2>\r\n<p>Mettre en &eacute;vidence ses attitudes&nbsp;spontan&eacute;es</p>\r\n<p>Cr&eacute;er les conditions&nbsp;d'une relation de confiance&nbsp;avec ses collaborateurs</p>\r\n<h2>Organiser, animer et&nbsp;entra&icirc;ner son &eacute;quipe</h2>\r\n<p>Clarifier les r&ocirc;les dans l'&eacute;quipe et d&eacute;finir les objectifs</p>\r\n<p>Motiver les membres de son &eacute;quipe</p>\r\n<p>Manager d'anciens coll&egrave;gues et des coll&egrave;gues plus &acirc;g&eacute;s</p>\r\n<p>Am&eacute;liorer la performance de l'&eacute;quipe gr&acirc;ce &agrave; un management adapt&eacute;</p>\r\n<p>Orienter l'action collective</p>\r\n<h2>Communiquer efficacement</h2>\r\n<p>Adopter les attitudes ad&eacute;quates dans la relation de face-&agrave;-face</p>\r\n<p>Faire face aux conflits et situations difficiles</p>\r\n<p>Savoir formuler et recevoir une critique</p>",
        "coverImage": {
            "file": "https://api.institut.io/uploads/images/d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_d18790cc59ed231f3ad70d1e27b96411.jpeg",
            "alt": "Management"
        },
        "domains": [
            {
                "id": 3,
                "title": "Management et leadership"
            }
        ],
        "priceInter": {
            "amount": "1800.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "2160.00",
            "discountType": "percent",
            "discountAmount": "15.00",
            "discountedPrice": "1530.00"
        },
        "priceIntra": {
            "amount": "6600.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "7920.00"
        },
        "duration": {
            "canonical": 259200,
            "days": 3
        },
        "typicalLearningTime": {
            "canonical": 259200,
            "days": 3
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1557705600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 1,
                "title": "Omega Formation Lyon",
                "city": "Lyon",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            },
            {
                "id": 6,
                "title": "Regus Bordeaux",
                "city": "Bordeaux",
                "country": "France"
            }
        ]
    }
]
```

This endpoint retrieves all Courses which Mode matches the request.

### HTTP Request

`GET https://api.institut.io/courses?modes=<modes>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>modes</code> | <code>string</code> | The Mode names, separated with comas: <br> <code>onsite</code> - on site course <br> <code>onsiteIntra</code> - on site intra-organization <br> <code>onsiteInter</code> - on site inter-organization <br> <code>elearning</code> - e-learning course <br> <code>phone</code> - cours par téléphone <br> <code>tutored</code> - remote course with a tutor <br> <code>blended</code> - a course combining on site and remote training <br> <code>mooc</code> - MOOC (Massive Open Online Course) <br> <code>workshop</code> - Workshop <br> <code>seminar</code> - Seminar <br> <code>conference</code> - Conference <br> <code>serious</code> - Serious game <br> <code>mobile</code> - Mobile learning <br> <code>rapide</code> - Rapid learning

## Filter By Date

```shell
curl -g "https://api.institut.io/courses?dates[start]=1541238178"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?dates[end]=1541238178"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?dates[start]=1541238178&dates[end]=1541238178"  \
  -H "Authorization: ZKXvA9fE"
```

This endpoint retrieves all Courses which scheduled dates match the request.

### HTTP Request

`GET https://api.institut.io/courses?dates[start]=<start_date>`

`GET https://api.institut.io/courses?dates[end]=<end_date>`

`GET https://api.institut.io/courses?dates[start]=<start_date>&dates[end]=<end_date>`

To convert a date to its timestamp before calling the API endpoint, there are several tools available such as <a href="https://helloacm.com/tools/unix-timestamp-converter/" target="&#95;blank">HelloACM's Unix timestamp converter</a>, which provides an API endpoint for Date String to TimeStamp conversion.

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>start_date</code> | <code>int</code> | The start date's timestamp
<code>end_date</code> | <code>int</code> | The end date's timestamp

## Filter By Price

```shell
curl -g "https://api.institut.io/courses?price[min]=1000"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?price[max]=2000"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?price[min]=1000&price[max]=2000"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?price[type]=inter&price[max]=2000"  \
  -H "Authorization: ZKXvA9fE"
```

This endpoint retrieves all Courses which Price(s) match the request.

### HTTP Request

`GET https://api.institut.io/courses?price[min]=<minimum_price>`

`GET https://api.institut.io/courses?price[max]=<maximum_price>`

`GET https://api.institut.io/courses?price[min]=<minimum_price>&price[max]=<maximum_price>`

`GET https://api.institut.io/courses?price[type]=<price_type>&price[max]=<maximum_price>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>minimum_price</code> | <code>int</code> | The minimum Price
<code>maximum_price</code> | <code>int</code> | The maximum Price
<code>price_type</code> | <code>int</code> | The Price type: <br> <code>inter</code> - Price for inter-organization training course <br> <code>intra</code> - Price for intra-organization training course

## Filter By Duration

```shell
curl -g "https://api.institut.io/courses?duration[min]=100000"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?duration[max]=500000"  \
  -H "Authorization: ZKXvA9fE"

curl -g "https://api.institut.io/courses?duration[min]=100000&duration[max]=500000"  \
  -H "Authorization: ZKXvA9fE"
```

This endpoint retrieves all Courses which Duration matches the request.

### HTTP Request

`GET https://api.institut.io/courses?duration[min]=<minimum_duration>`

`GET https://api.institut.io/courses?duration[max]=<maximum_duration>`

`GET https://api.institut.io/courses?duration[min]=<minimum_duration>&duration[max]=<maximum_duration>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>minimum_duration</code> | <code>int</code> | The minimum Duration in seconds (refers to the canonical value of the Duration)
<code>maximum_duration</code> | <code>int</code> | The maximum Duration in seconds (refers to the canonical value of the Duration)

## Restrict Course Info

```shell
curl "https://api.institut.io/courses?display=mode"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "Animer des réunions en anglais",
        "indexed": true,
        "mode": {
            "id": 5,
            "value": "cours par téléphone"
        }
    },
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "mode": {
            "id": 1,
            "value": "onsite"
        }
    },
    {
        "id": 3,
        "title": "Management d'équipe",
        "indexed": true,
        "mode": {
            "id": 1,
            "value": "onsite"
        }
    }
]
```

```shell
curl "https://api.institut.io/courses?display=owner,priceinter,count,dates,premises"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 2,
        "title": "Animer des réunions en anglais",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1572825600
    },
    {
        "id": 1,
        "title": "Excel Initiation - Tableaux de calculs simples",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "priceInter": {
            "amount": "1200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1440.00"
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextStartdate": 1560211200,
        "nextOpendate": 1560729600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 3,
                "title": "Omega Formation Lille",
                "city": "Lille",
                "country": "France"
            },
            {
                "id": 4,
                "title": "Omega Formation Nantes",
                "city": "Nantes",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            }
        ]
    },
    {
        "id": 3,
        "title": "Management d'équipe",
        "indexed": true,
        "owner": {
            "id": 1,
            "title": "Omega Formation",
            "coverImage": {
                "file": "https://api.institut.io/uploads/images/c0d5c55bf328956abb9fad8133db4ee1.png",
                "thumb": "https://api.institut.io/uploads/images/_c0d5c55bf328956abb9fad8133db4ee1.png",
                "alt": "Omega Formation"
            }
        },
        "priceInter": {
            "amount": "1800.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "2160.00",
            "discountType": "percent",
            "discountAmount": "15.00",
            "discountedPrice": "1530.00"
        },
        "count": {
            "present": 0,
            "future": 1,
            "unscheduled": 0
        },
        "nextOpendate": 1557705600,
        "premises": [
            {
                "id": 2,
                "title": "Omega Group",
                "city": "Paris",
                "country": "France"
            },
            {
                "id": 1,
                "title": "Omega Formation Lyon",
                "city": "Lyon",
                "country": "France"
            },
            {
                "id": 5,
                "title": "Regus Marseille Les Docks",
                "city": "Marseille",
                "country": "France"
            },
            {
                "id": 6,
                "title": "Regus Bordeaux",
                "city": "Bordeaux",
                "country": "France"
            }
        ]
    }
]
```


By default, Course queries return a significant number of fields for each Course.

The <code>display</code> parameter can be used to optimize performance by returning only a selection of field values.

The <code>id</code> and <code>title</code> fields are always returned.

### HTTP Request

`GET https://api.institut.io/courses?display=<fields_to_be_returned>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>display</code> | <code>string</code> | The fields which values have to be returned. The <code>display</code> parameter can include several field names, which must be separated with commas: <br> <code>owner</code> <br> <code>mode</code> <br> <code>summary</code> <br> <code>goal</code> <br> <code>description</code> <br> <code>targetedSkills</code> <br> <code>programme</code> <br> <code>coverImage</code> <br> <code>domains</code> <br> <code>priceinter</code> <br> <code>priceintra</code> <br> <code>duration</code> <br> <code>typicalLearningTime</code> <br> <code>count</code> <br> <code>dates</code> <br> <code>premises</code>

# Sessions

This section is currently being updated.

A Session is a scheduled occurrence of a Course.

## Get All Sessions Of A Course

## Get A Specific Session

# Domains

A Domain is a training topic which Courses can be linked to.
A Domain can have a parent and several children.

## Get All Domains

```shell
curl "https://api.institut.io/domains"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "7",
        "title": "Bureautique",
        "children": [
            {
                "id": 8,
                "title": "Excel"
            },
            {
                "id": 9,
                "title": "PowerPoint"
            }
        ]
    },
    {
        "id": "4",
        "title": "Langues",
        "children": [
            {
                "id": 5,
                "title": "Anglais"
            },
            {
                "id": 6,
                "title": "Espagnol"
            }
        ]
    },
    {
        "id": "1",
        "title": "Management",
        "children": [
            {
                "id": 3,
                "title": "Management et leadership"
            },
            {
                "id": 2,
                "title": "Management transverse"
            }
        ]
    },
    {
        "id": "10",
        "title": "Ressources humaines",
        "children": [
            {
                "id": 11,
                "title": "Entretien annuel"
            },
            {
                "id": 12,
                "title": "Paie"
            }
        ]
    }
]
```

This endpoint retrieves all domains.

### HTTP Request

`GET https://api.institut.io/domains`

### Response Fields

Field | Type | Description
--------- | ------- | -----------
<code>id</code> | <code>int</code> | The ID of the Domain
<code>title</code> | <code>string</code> | The name of the Domain
<code>children</code> | <code>array</code> | The Domain's children

# Premises

A Premise is a location linked to an Account: training center, office, etc.

## Get All Premises

```shell
curl "https://api.institut.io/premises"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "2",
        "title": "Omega Group",
        "type": "headquarter",
        "rank": 1,
        "description": "Siège social du groupe Omega",
        "address": {
            "line1": "14 boulevard Montmartre",
            "line2": null,
            "line3": null
        },
        "zipcode": "75009",
        "city": "Paris",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "49",
            "longitude": "2"
        },
        "email": "accueil@omega-formation.com",
        "phone": "01 53 24 60 25",
        "fax": null
    },
    {
        "id": "3",
        "title": "Omega Formation Lille",
        "type": "training center",
        "rank": 2,
        "description": null,
        "address": {
            "line1": "108 rue Nationale",
            "line2": null,
            "line3": null
        },
        "zipcode": "59000",
        "city": "Lille",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "51",
            "longitude": "3"
        },
        "email": "lille@omega-formation.com",
        "phone": "03 20 10 01 18",
        "fax": null
    },
    {
        "id": "1",
        "title": "Omega Formation Lyon",
        "type": "training center",
        "rank": 3,
        "description": "Centre de formation de Omega Formation à Lyon",
        "address": {
            "line1": "283 Rue Garibaldi",
            "line2": null,
            "line3": null
        },
        "zipcode": "69003",
        "city": "Lyon",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "46",
            "longitude": "5"
        },
        "email": "lyon@omega-formation.com",
        "phone": "0482538627",
        "fax": null
    },
    {
        "id": "4",
        "title": "Omega Formation Nantes",
        "type": "training center",
        "rank": 4,
        "description": null,
        "address": {
            "line1": "13 Rue Jean Jacques Rousseau",
            "line2": null,
            "line3": null
        },
        "zipcode": "44000",
        "city": "Nantes",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "47",
            "longitude": "-2"
        },
        "email": "nantes@omega-formation.com",
        "phone": "02 40 69 25 27",
        "fax": null
    },
    {
        "id": "5",
        "title": "Regus Marseille Les Docks",
        "type": "training center",
        "rank": 5,
        "description": "Centre d'affaires",
        "address": {
            "line1": "10 Place de la Joliette",
            "line2": "Cedex 2, Les Docks - Atrium 10.6",
            "line3": null
        },
        "zipcode": "13567",
        "city": "Marseille",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "43",
            "longitude": "5"
        },
        "email": "marseille-lesdocks@regus.fr",
        "phone": "04 91 13 45 12",
        "fax": null
    },
    {
        "id": "6",
        "title": "Regus Bordeaux",
        "type": "training center",
        "rank": 6,
        "description": null,
        "address": {
            "line1": "Rue Charles Domercq",
            "line2": null,
            "line3": null
        },
        "zipcode": "33082",
        "city": "Bordeaux",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "45",
            "longitude": "-1"
        },
        "email": "bordeaux@regus.fr",
        "phone": "05 56 64 42 52",
        "fax": null
    }
]
```

This endpoint retrieves all premises.

### HTTP Request

`GET https://api.institut.io/premises`

### Response Fields

The response fields for this endpoint are the same as the response fields for the endpoint which retrieves a specific premise.

## Get A Specific Premise

```shell
curl "https://api.institut.io/premises/1"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "1",
        "title": "Omega Formation Lyon",
        "type": "training center",
        "rank": 3,
        "description": "Centre de formation de Omega Formation à Lyon",
        "address": {
            "line1": "283 Rue Garibaldi",
            "line2": null,
            "line3": null
        },
        "zipcode": "69003",
        "city": "Lyon",
        "state": null,
        "country": "France",
        "coordinates": {
            "latitude": "46",
            "longitude": "5"
        },
        "email": "lyon@omega-formation.com",
        "phone": "0482538627",
        "fax": null
    }
]
```

This endpoint retrieves a specific premise.

### HTTP Request

`GET https://api.institut.io/premises/<id>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the premise to retrieve

### Response Fields

Name | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the Premise
<code>title</code> | <code>string</code> | The name of the Premise
<code>type</code> | <code>string</code> | The type of the Premise: <br> <code>training center</code> - regular training center <br> <code>headquarter</code> - headquarter of the organization <br> <code>offices</code> - offices of the organization, that are neither the headquarter nor a training center <br> <code>conference</code> - a conference hall that hosts the organization's events <br> <code>others</code> - any other type of premises
<code>rank</code> | <code>int</code> | The rank of the Premise among the list of all Premises linked to the Account
<code>description</code> | <code>string</code> | A text describing the Premise
<code>address1</code> | <code>string</code> | First line of the Premise's address
<code>address2</code> | <code>string</code> | Second line of the Premise's address
<code>address3</code> | <code>string</code> | Third line of the Premise's address
<code>zipcode</code> | <code>string</code> | The zipcode of the Premise's location
<code>city</code> | <code>string</code> | The city where the Premise is located
<code>state</code> | <code>string</code> | The state where the Premise is located
<code>country</code> | <code>string</code> | The country where the Premise is located
<code>latitude</code> | <code>string</code> | The latitude where the Premise is located
<code>longitude</code> | <code>string</code> | The longitude where the Premise is located
<code>email</code> | <code>string</code> | The email contact of the Premise
<code>phone</code> | <code>string</code> | The phone contact of the Premise
<code>fax</code> | <code>string</code> | The fax contact of the Premise

## Restrict Premise Info

```shell
curl "https://api.institut.io/premises?display=city"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "2",
        "city": "Paris"
    },
    {
        "id": "3",
        "city": "Lille"
    },
    {
        "id": "1",
        "city": "Lyon"
    },
    {
        "id": "4",
        "city": "Nantes"
    },
    {
        "id": "5",
        "city": "Marseille"
    },
    {
        "id": "6",
        "city": "Bordeaux"
    }
]
```

```shell
curl "https://api.institut.io/premises?display=title,address"  \
  -H "Authorization: ZKXvA9fE"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "2",
        "title": "Omega Group",
        "address": {
            "line1": "14 boulevard Montmartre",
            "line2": null,
            "line3": null
        }
    },
    {
        "id": "3",
        "title": "Omega Formation Lille",
        "address": {
            "line1": "108 rue Nationale",
            "line2": null,
            "line3": null
        }
    },
    {
        "id": "1",
        "title": "Omega Formation Lyon",
        "address": {
            "line1": "283 Rue Garibaldi",
            "line2": null,
            "line3": null
        }
    },
    {
        "id": "4",
        "title": "Omega Formation Nantes",
        "address": {
            "line1": "13 Rue Jean Jacques Rousseau",
            "line2": null,
            "line3": null
        }
    },
    {
        "id": "5",
        "title": "Regus Marseille Les Docks",
        "address": {
            "line1": "10 Place de la Joliette",
            "line2": "Cedex 2, Les Docks - Atrium 10.6",
            "line3": null
        }
    },
    {
        "id": "6",
        "title": "Regus Bordeaux",
        "address": {
            "line1": "Rue Charles Domercq",
            "line2": null,
            "line3": null
        }
    }
]
```


By default, Premise queries return a significant number of fields for each Premise.

The <code>display</code> parameter can be used to optimize performance by returning only a selection of field values.

The <code>id</code> field is always returned.

### HTTP Request

`GET https://api.institut.io/premises?display=<fields_to_be_returned>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>display</code> | <code>string</code> | The fields which values have to be returned. The <code>display</code> parameter can include several field names, which must be separated with commas: <br> <code>title</code> <br> <code>type</code> <br> <code>rank</code> <br> <code>description</code> <br> <code>address</code> <br> <code>zipcode</code> <br> <code>city</code> <br> <code>state</code> <br> <code>country</code> <br> <code>coordinates</code> <br> <code>email</code> <br> <code>phone</code> <br> <code>fax</code>

# Other Objects

Institut.io's model includes a number of objects.

Some of them are generic:

- Image

Others are specific to Course Objects:

- Mode

- Price

- Duration

- Count

## Image Object

Property | Type | Description
--------- | ------- | -----------
<code>file</code> | <code>string</code> | The URL of the Image file
<code>thumb</code> | <code>string</code> | The URL of the Image's thumbnail
<code>alt</code> | <code>string</code> | The alt attribute of the Image

## Price Object

The Price of the Course, either inter or intra organization:

- inter organization: the Course gathers trainees from different organizations and the Price is set for each single individual

- intra organization: the Course gathers trainees from a single organization and the Price is set for the whole group of trainees

Property | Type | Description
--------- | ------- | -----------
<code>amount</code> | <code>decimal</code> | The Price amount excluding VAT
<code>currency</code> | <code>string</code> | The abbreviation of the currency in which the Price is offered
<code>vat</code> | <code>decimal</code> | The percentage of VAT
<code>amountIncVat</code> | <code>decimal</code> | The Price amount including VAT
<code>discountType</code> | <code>decimal</code> | The type of discount applied to the Price: <br> <code>percent</code> - a percentage of the Price amount <br> <code>value</code> - a fix value to be substracted from the Price amount
<code>discountAmount</code> | <code>decimal</code> | The amount of the discount applied to the Price (either in percentage or in value)
<code>discountedPrice</code> | <code>decimal</code> | The Price amount after discount

## Duration Object

A Duration can be defined with a set of values such as a number of <code>years</code>, <code>months</code>, <code>weeks</code>, <code>days</code>, <code>hours</code>, <code>minutes</code> and <code>seconds</code>. The value of the Duration is the cumulation of all those values, which is provided with the <code>canonical</code> field, which sums up the equivalent of all fields in seconds.

Property | Type | Description
--------- | ------- | -----------
<code>canonical</code> | <code>int</code> | The total number of seconds in the Duration
<code>years</code> | <code>int</code> | The number of years of the Duration
<code>months</code> | <code>int</code> | The number of months of the Duration
<code>weeks</code> | <code>int</code> | The number of weeks of the Duration
<code>days</code> | <code>int</code> | The number of days of the Duration
<code>hours</code> | <code>int</code> | The number of hours of the Duration
<code>minutes</code> | <code>int</code> | The number of minutes of the Duration
<code>seconds</code> | <code>int</code> | The number of seconds of the Duration

## Count Object

The Count details the number of sessions of a Course.

Property | Type | Description
--------- | ------- | -----------
<code>present</code> | <code>int</code> | The number of sessions that have already started and are not yet finished
<code>future</code> | <code>int</code> | The number of sessions that have not started yet
<code>unscheduled</code> | <code>int</code> | The number of sessions which dates have not been set
