---
title: Institut.io API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
#  - ruby
#  - python
#  - javascript

toc_footers:
  - <a href='https://www.institut.io' target='_blank'>Sign up for an account</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Institut.io API! You can use our API to access an organisation's training courses and related information.

All information retrieved by this API is managed by the organisation within its Institut.io backoffice.

# Search Engine

# Administration

# Authentication

> To authorize, use this code:

```shell
# The API key
curl "https://api.institut.io/api_key/last_part_of_url"
```

> Make sure to replace `api_key` with your API key and `last_part_of_url` with an API endpoint's URL.

Institut.io uses API keys to allow access to the API.

When subscribing to an Institut.io account, an organisation is granted an API key, referred to in this documentation as <code>api_key</code>.

You can register an Institut.io account on <a href="https://www.institut.io" target="&#95;blank">Institut.io's website</a>.

Institut.io expects for the API key to be included in all API requests to the server in the request URL as follows:

<code>https://api.institut.io/api_key/last_part_of_url</code>

<aside class="notice">
You must replace <code>api_key</code> with your organisation's API key and <code>last_part_of_url</code> with an API endpoint's URL.
</aside>

# Accounts

## Account Creation

## Account Object

The Account object contains information about an Institut.io account.

Property | Type | Description
--------- | ------- | -----------
<code>id</code> | <code>int</code> | The ID of the Account
<code>title</code> | <code>string</code> | The title of the Account
<code>imagecover</code> | <code>array</code> | Information about the Image that is linked to the Account as its cover image


# Courses

## Get All Courses

```shell
curl "https://api.institut.io/YBhxbaKU/courses"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "238",
        "score": 0,
        "title": "Test",
        "account": {
            "id": 10,
            "title": "Aldebaran OF"
        },
        "owner": {
            "id": 10,
            "title": "Aldebaran OF"
        },
        "mode": {
            "id": 0,
            "value": "on site"
        },
        "imagecover": {
            "file": "https://api.institut.io/uploads/images/5561fcb66eb7666a6247b94aa4dbae28.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_5561fcb66eb7666a6247b94aa4dbae28.jpeg",
            "alt": "conseil"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 1,
            "future": 0,
            "unscheduled": 0
        }
    },
    {
        "id": "242",
        "score": 0,
        "title": "Réseaux - serveurs",
        "account": {
            "id": 10,
            "title": "Aldebaran OF",
            "imagecover": {
                "file": "https://api.institut.io/uploads/images/061d4c71f5191590504dfd4100af972d.jpeg",
                "thumb": "https://api.institut.io/uploads/images/_061d4c71f5191590504dfd4100af972d.jpeg",
                "alt": "excel"
            }
        },
        "owner": {
            "id": 11,
            "title": "Sagittarius OF"
        },
        "mode": {
            "id": 0,
            "value": "on site"
        },
        "price_inter": {
            "amount": "3200.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "3840.00"
        },
        "count": {
            "present": 0,
            "future": 0,
            "unscheduled": 1
        }
    }
]
```

This endpoint retrieves all courses.

### HTTP Request

`GET https://api.institut.io/YBhxbaKU/courses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
expression | null | If defined, the result will include courses matching the expression with full text search
domains | null | If set to false, the result will include kittens that have already been adopted.

### Response Fields

Field | Description
--------- | -----------
id | Identifier of the course

## Get A Specific Course

```shell
curl "https://api.institut.io/YBhxbaKU/courses/243"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "243",
        "score": 0,
        "title": "Réseaux - serveurs",
        "account": {
            "id": 10,
            "title": "Aldebaran OF",
            "imagecover": {
                "file": "http://localhost:8000/uploads/images/4165c3046ee2b35cbf1b3c1a9e5b8cce.jpeg",
                "thumb": "http://localhost:8000/uploads/images/_4165c3046ee2b35cbf1b3c1a9e5b8cce.jpeg",
                "alt": "moon"
            }
        },
        "owner": {
            "id": 11,
            "title": "Sagittarius OF"
        },
        "mode": {
            "id": 0,
            "value": "on site"
        },
        "summary": "En quelques mots, voici un résumé",
        "goal": "Azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn \r\n\r\nAzerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn azerty qsdfgh wxcvbn",
        "description": "CEtte formation est très intéressante, elle porte sur les réseaux et serveurs",
        "targetedSkills": "Savoir gérer les serveurs",
        "programme": "<p>Azerty</p>\r\n<p><em>Lorem ipsum</em></p>\r\n<p>Qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm&nbsp;qsdfghjklm</p>\r\n<p>&nbsp;</p>\r\n<p><strong>Lorem</strong></p>\r\n<p>Ipsum</p>",
        "imagecover": {
            "file": "http://localhost:8000/uploads/images/e2e624085ca161c9fb7994d22eea520f.jpeg",
            "thumb": "http://localhost:8000/uploads/images/_e2e624085ca161c9fb7994d22eea520f.jpeg",
            "alt": "Hello, this is a greeting card for year 2013"
        },
        "price_inter": {
            "amount": "2000.00",
            "currency": "USD",
            "vat": "10.00",
            "amountIncVat": "2200.00",
            "discountType": "percent",
            "discountAmount": "15.00",
            "discountedPrice": "1700.00"
        },
        "price_intra": {
            "amount": "1000.00",
            "currency": "EUR",
            "vat": "20.00",
            "amountIncVat": "1200.00"
        },
        "duration": {
            "canonical": 121438042,
            "years": 3,
            "days": 25,
            "hours": 12,
            "minutes": 47,
            "seconds": 22
        },
        "count": {
            "present": 2,
            "future": 0,
            "unscheduled": 1
        }
    }
]
```

This endpoint retrieves a specific course.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses/<id>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the course to retrieve

### Response Fields

Name | Type | Description
--------- | --------- | -----------
<code>id</code> | <code>int</code> | The ID of the Course
<code>title</code> | <code>string</code> | The title of the Course
<code>account</code> | <code>array</code> | The Account which the Course is linked to on the media making the API calls
<code>owner</code> | <code>array</code> | The Account which owns the Course (ie which was used when creating the Course object)
<code>mode</code> | <code>array</code> | The learning Mode of the Course
<code>summary</code> | <code>string</code> | The summary of the Course
<code>goal</code> | <code>string</code> | The goal of the Course
<code>description</code> | <code>string</code> | The description of the Course
<code>targetedSkills</code> | <code>string</code> | The targeted skills of the Course
<code>programme</code> | <code>string</code> | The programme of the Course
<code>imagecover</code> | <code>array</code> | The cover Image of the Course
<code>price_inter</code> | <code>array</code> | The inter-organization Price of the Course
<code>price_intra</code> | <code>array</code> | The intra-organization Price of the Course
<code>duration</code> | <code>array</code> | The duration of the Course
<code>typicalLearningTime</code> | <code>array</code> | The typical learning time of the Course
<code>count</code> | <code>array</code> | The number of sessions of the Course
<code>nextstartdate</code> | <code>int</code> | The timestamp of the Course's next start date
<code>nextopendate</code> | <code>int</code> | The timestamp of the Course's next opening date
<code>locations</code> | <code>array</code> | The Premises where the Course is scheduled

## Search An Expression

```shell
curl "https://api.institut.io/YBhxbaKU/courses?expression=test"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "238",
        "score": 2.1576157,
        "title": "Test",
        "account": {
            "id": 10,
            "title": "Aldebaran OF"
        },
        "owner": {
            "id": 10,
            "title": "Aldebaran OF"
        },
        "mode": {
            "id": 0,
            "value": "on site"
        },
        "imagecover": {
            "file": "https://api.institut.io/uploads/images/5561fcb66eb7666a6247b94aa4dbae28.jpeg",
            "thumb": "https://api.institut.io/uploads/images/_5561fcb66eb7666a6247b94aa4dbae28.jpeg",
            "alt": "conseil"
        },
        "duration": {
            "canonical": 172800,
            "days": 2
        },
        "count": {
            "present": 1,
            "future": 0,
            "unscheduled": 0
        }
    }
]
```

This endpoint retrieves all Courses matching an expression.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?expression=<expression>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>expression</code> | <code>string</code> | The searched expression

### Response Fields

Name | Type | Description
--------- | --------- | -----------
<code>score</code> | <code>decimal</code> | The score of the Course

## Filter By Domain

### Using Domain titles

```shell
curl "https://api.institut.io/YBhxbaKU/courses?domains[titles]=Commercial,Agilité"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses linked to a Domain or one of its children.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?domains[titles]=<domain_titles>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>domain_titles</code> | <code>string</code> | The Domain titles, separated with comas

### Using Domain IDs

```shell
curl "https://api.institut.io/YBhxbaKU/courses?domains[ids]=4,14"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses linked to a Domain or one of its children.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?domains[ids]=<domain_ids>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>domain_ids</code> | <code>string</code> | The Domain IDs, separated with comas

## Filter By Mode

```shell
curl "https://api.institut.io/YBhxbaKU/courses?modes=onsite,mooc"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses which Mode matches the request.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?modes=<modes>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>modes</code> | <code>string</code> | The Mode names, separated with comas: <br> <code>onsite</code> - on site course <br> <code>onsiteintra</code> - on site intra-organization <br> <code>onsiteinter</code> - on site inter-organization <br> <code>elearning</code> - e-learning course <br> <code>tutored</code> - remote course with a tutor <br> <code>blended</code> - a course combining on site and remote training <br> <code>mooc</code> - MOOC (Massive Open Online Course) <br> <code>workshop</code> - Workshop <br> <code>seminar</code> - Seminar <br> <code>conference</code> - Conference <br> <code>serious</code> - Serious game <br> <code>mobile</code> - Mobile learning <br> <code>rapide</code> - Rapid learning

## Filter By Date

```shell
curl "https://api.institut.io/YBhxbaKU/courses?date[start]=1541238178"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?date[end]=1541238178"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?date[start]=1541238178&date[end]=1541238178"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses which scheduled dates match the request.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?dates[start]=<start_date>`

`GET https://api.institut.io/<api_key>/courses?dates[end]=<end_date>`

`GET https://api.institut.io/<api_key>/courses?dates[start]=<start_date>&dates[end]=<end_date>`

To convert a date to its timestamp before calling the API endpoint, there are several tools available such as <a href="https://helloacm.com/tools/unix-timestamp-converter/" target="&#95;blank">HelloACM's Unix timestamp converter</a>, which provides an API endpoint for Date String to TimeStamp conversion.

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>start_date</code> | <code>int</code> | The start date's timestamp
<code>end_date</code> | <code>int</code> | The end date's timestamp

## Filter By Price

```shell
curl "https://api.institut.io/YBhxbaKU/courses?price[min]=1000"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?price[max]=2000"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?price[min]=1000&price[max]=2000"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?price[type]=inter&price[max]=2000"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses which Price(s) match the request.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?price[min]=<minimum_price>`

`GET https://api.institut.io/<api_key>/courses?price[max]=<maximum_price>`

`GET https://api.institut.io/<api_key>/courses?price[min]=<minimum_price>&price[max]=<maximum_price>`

`GET https://api.institut.io/<api_key>/courses?price[type]=<price_type>&price[max]=<maximum_price>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>minimum_price</code> | <code>int</code> | The minimum Price
<code>maximum_price</code> | <code>int</code> | The maximum Price
<code>price_type</code> | <code>int</code> | The Price type: <br> <code>inter</code> - Price for inter-organization training course <br> <code>intra</code> - Price for intra-organization training course

## Filter By Duration

```shell
curl "https://api.institut.io/YBhxbaKU/courses?duration[min]=100000"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?duration[max]=500000"
```

> The above command returns JSON structured like this:

```json
[]
```

```shell
curl "https://api.institut.io/YBhxbaKU/courses?duration[min]=100000&duration[max]=500000"
```

> The above command returns JSON structured like this:

```json
[]
```

This endpoint retrieves all Courses which Duration matches the request.

### HTTP Request

`GET https://api.institut.io/<api_key>/courses?duration[min]=<minimum_duration>`

`GET https://api.institut.io/<api_key>/courses?duration[max]=<maximum_duration>`

`GET https://api.institut.io/<api_key>/courses?duration[min]=<minimum_duration>&duration[max]=<maximum_duration>`

### Query Parameters

Parameter | Type | Description
--------- | --------- | -----------
<code>minimum_duration</code> | <code>int</code> | The minimum Duration in seconds (refers to the canonical value of the Duration)
<code>maximum_duration</code> | <code>int</code> | The maximum Duration in seconds (refers to the canonical value of the Duration)

# Domains

A Domain is a training topic which Courses can be linked to.
A Domain can have a parent and several children.

## Get All Domains

```shell
curl "https://api.institut.io/YBhxbaKU/domains"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "13",
        "title": "Administration",
        "children": []
    },
    {
        "id": "4",
        "title": "Commercial",
        "children": [
            {
                "id": 6,
                "title": "Achats"
            },
            {
                "id": 5,
                "title": "Vente"
            }
        ]
    },
    {
        "id": "7",
        "title": "Management",
        "children": [
            {
                "id": 14,
                "title": "Agilité"
            },
            {
                "id": 9,
                "title": "Leadership"
            },
            {
                "id": 8,
                "title": "Négociation"
            }
        ]
    }
]
```

This endpoint retrieves all domains.

### HTTP Request

`GET https://api.institut.io/YBhxbaKU/domains`

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
curl "https://api.institut.io/YBhxbaKU/premises"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": "8",
        "title": "Aldebaran - Centre de Paris",
        "type": "training center",
        "rank": 1,
        "description": "Ceci est \r\nun test",
        "address1": "12 bd de la Gare",
        "address2": "BP 73894",
        "address3": null,
        "zipcode": "75001",
        "city": "Paris",
        "state": null,
        "country": "France",
        "latitude": null,
        "longitude": null,
        "email": "paris@aldebaran.fr",
        "phone": "04627291947",
        "fax": "0628294820"
    },
    {
        "id": "7",
        "title": "Aldebaran Headquarter",
        "type": "headquarter",
        "rank": 3,
        "description": "Il s'agit du siège social",
        "address1": "15 rue du Puits",
        "address2": "Route de la Rivière",
        "address3": "BP12983",
        "zipcode": "13245",
        "city": "Marseille",
        "state": "Bouches du Rhône",
        "country": "France",
        "latitude": null,
        "longitude": null,
        "email": "hq@aldebaran.fr",
        "phone": "0394857823",
        "fax": "0328475629"
    }
]
```

This endpoint retrieves all premises.

### HTTP Request

`GET https://api.institut.io/YBhxbaKU/premises`

### Response Fields

Field | Type | Description
--------- | ------- | -----------
<code>id</code> | <code>int</code> | The ID of the Premise
<code>title</code> | <code>string</code> | The name of the Premise
<code>type</code> | <code>string</code> | The type of the Premise: <br> <code>training center</code> - regular training center <br> <code>headquarter</code> - headquarter of the organisation <br> <code>offices</code> - offices of the organization, that are neither the headquarter nor a training center <br> <code>conference</code> - a conference hall that hosts the organization's events <br> <code>others</code> - any other type of premises
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
