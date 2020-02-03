---
title: PayQin Assurance API

language_tabs: # must be one of https://git.io/vQNgJ
 
 - Code


search: true
---

# Introduction

The API of PayQin Insurance allows you to calculate the price of different insurance: health insurance, home insurance, car insurance, travel insurance.
Its calculations are based on data provided by the user :

• Travel Insurance: Duration, age, and destination

• Health Insurance: The number of children, the desired formula

• Car Insurance: Professional situation, energy (petrol, diesel), power, payload in tonnes, new value, market value, duration, desired coverage.

# Description

> Parameters :

```javascript
method : POST
headers : "Content-Type: 'application/json'"
Access Key :
APP_KEY = C85Gv9wJaijGRZid20sGbIArm6KYSZmPMB1sVCquTulgh3n2UazTvopGoxJB
```

`Description of the interaction with PayQin Assurance API` 

1. You need to recover the data entered by your users, convert them to JSON format, then send them to PayQin API.

2. PayQin processes the data received, performs the calculations and sends you the insurance price and the name of the companies offering

# Insurance

## Travel Insurance


> Example data you need to send to get the price :

```json
{
"duration" : 180,
"destination" : "d1",
"age" : "0-1"
}

```

> Example json response you should receive :

```json
[
  {
  "society" : "SAHAM ASSURANCE",
  "price" : 15500,
  },
  {
  "society" : "COMA ASSURANCE",
  "price" : 34436,
  }
]

```

API access link : `http://assurance.payqin.com/api/public/api/voyage`

### Body parameters :
Param (data expected) | Type | Description
--------- | ------- | -----------
duration | integer | The duration of the stay
age | string | The age range to which the traveler belongs
destination|string| The destination of the trip

Expected data and designations :

### • duration
Duration | Designation 
--------- | ------- 
7 | 1 week 
10 | 10 days 
15 | 15 days
21 | 21 days
30 | 30 days
45 | 45 days
60 | 60 days
91 | 91 days
180 | 6 month
365 | 1 year

### • age
Age ranges | Designation
--------- | ------- 
0-1 | Babies 
2-11 | Children 
12-80 | Adults

### • destination
Destinations | Designation (Saham Assurance) | Designation (Coma Assurance)
--------- | ------- |-----
d1 | West africa | Africa and Asia
d2 | Shenghen and north africa | Europe |
d3 | Worldwide | Worldwide | Worldwide

## Health Insurance

> Example data you need to send to get the price :

```json
{
  "formula" : "acacia",
  "children_number" : 4
}

```

> Example json response you should receive :

```json
{
"price": 411000,
"society": "VITALIS"
}
```
API access link :  `http://assurance.payqin.com/api/public/api/sante`

### Body parameters :
Param (data expected) | Type | Description
--------- | ------- | -----------
formula | string | The desired formula
children | integer | The number of children

Expected data and designations :

### • formula

Formulas |
-------  |
acacia |
iroko |
ebene |

### • children_number

You can return any numerical number, representing the number of dependent children (1, etc.)

## Car Insurance

> Example data you need to send to get the price :

```json
{
"category" : "CATSOCI",
"formula" : "tout",
"duration" : 3,
"professional_situation" : "religieux",
"new_value" : 15000000,
"market_value" : 10000000,
"payload" : "1.01 à 3T",
"energy" : "ESSENCE",
"power" : "1 à 2"
}

```

> Example json response you should receive :

```json
[
    {
    "Societe": "SAHAM",
    "MontantTotal": 417979.04,
    "Duree": 3,
    "formule": "tout",
    "ResponsabiliteCivile": 17250.52, 
    "IndividuelConducteur": 980, 
    "DefenseRecours": 2226, 
    "Incendie": 14112, 
    "VolMainsArmees": 14112,
    "BrisDeGlace": 11340, 
    "AvanceRecours": 4200, 
    "CollisionComplet": 283500,
    "Reduction": {"ResponsabiliteCivile" : 10, "type" : "percentage" },
    "MontantAccessoire": 5000, 
    "Taxe": 52857.063,
    "MontantCedeao": 1000,
    "currency" : "XOF"
    },
    {
    "Societe": "SUNU",
    "MontantTotal": 376726.631,
    "Duree": 3,
    "formule": "tout", 
    "ResponsabiliteCivile": 17250.52, 
    "IndividuelConducteur": 3360, 
    "DefenseRecours": 2226,
     "Incendie": 6174,
      "VolMainsArmees": 13230, 
      "BrisDeGlace": 85050, 
      "AvanceRecours": 4200, 
      "CollisionComplet": 181440,
      "Reduction": {"ResponsabiliteCivile" : 10, "type" : "percentage" },
      "MontantAccessoire": 5000, 
      "Taxe": 47629.813 ,
      "MontantCedeao": 1000,
      "currency" : "XOF"
    },
    {
    "Societe": "ALLIANZ",
    "MontantTotal": 259261.997,
    "Duree": 3,
    "formule": "tout",
     "ResponsabiliteCivile": 17250.52, 
     "IndividuelConducteur": 3360, 
     "DefenseRecours": 2226, 
     "Incendie": 5644.8, 
     "VolMainsArmees": 15876,
      "BrisDeGlace": 7938, 
      "AvanceRecours": 4200,
      "CollisionComplet": 151200,
      "Reduction": {"ResponsabiliteCivile" : 10, "type" : "percentage" },
      "MontantAccessoire": 5000,
       "Taxe": 32754.379,
      "MontantCedeao": 1000,
      "currency" : "XOF"
    },
    {
    "Societe": "SIDAM",
    "MontantTotal": 230872.274,
    "Duree": 3,
    "formule": "tout", 
    "ResponsabiliteCivile": 16429,
     "IndividuelConducteur": 3360, 
     "DefenseRecours": 2226, 
     "Incendie": 11466,
      "VolMainsArmees": 10584, 
      "BrisDeGlace": 15120, 
      "AvanceRecours": 4200, 
      "CollisionComplet": 124740,
    "Reduction": {"ResponsabiliteCivile" : 10, "type" : "percentage" },
    "MontantAccessoire": 5000, 
    "Taxe": 29161.255,
    "MontantCedeao": 1000,
    "currency" : "XOF"
    
    }
]

```

API access link `http://assurance.payqin.com/api/public/api/automobile`

### Body parameters :
Param (data expected) | Type | Description
--------- | ------- | -----------
category | string | The type of vehicle |
professional_situation | string | Socio-professional situation |
energy | string | Energy of the car |
power | string | The power of the car |
payload | string | Car payload |
new_value | integer | new value of the car |
market_value | integer | market value of the car |
duration | integer | The duration of the insurance in months |
formula | string | The desired formula | 

Expected data and designations :

### • category : 

Vehicles categories | Designation | 
--------- | ------- | 
CATPERSO | Personal vehicle | 
CATUTILE | Commercial vehicle | 
CATSOCI |Company vehicle |

### • professional_situation :

Socio-professional situation | Designation | 
--------- | ------- | 
religieux | religious| 
autre | worker, etc| 

### • energy :

Energies | Designation | 
--------- | ------- | 
ESSENCE | petrol| 
DIESEL | diesel| 

<aside class="warning">You must send either “ESSENCE” or “DIESEL”, but not both at the same time</aside>

### • power :

Essence | Diesel| 
--------- | ------- | 
1 à 2 | 1| 
3 à 6 | 2 à 4| 
7 à 9 | | 5 à 6 |
10 à 11 | 7 à 8 |
12 et plus | 9 et plus

<aside class="warning">If you send petrol or diesel you must also send the value of the associated power which is in the table above.</aside>

### • payload 

Payload (in tonnes) |
--------- |
jusqu’à 1T |  
1.01 à 3T | 
3.01 à 5T | 
5.01 à 8T | 
8.01 à 11T | 
11.01 à 13T |
13.01 à 15T |
plus de 15T |
tracteur routier |

### • new_value

You can return the new price of the car digitally

### • market_value

You can return the market value of the car in figures

### • duration

Duration in months (1, 3, 6, 12)

### • formula

The formula you want to subscribe to

Formulas | Designation| 
--------- | ------- | 
simple | Simple third| 
ameliore | Third party improved| 
collision | Third Collision |
tout | All risks |

# Users

## Get user by email

### HTTP Request : 

`POST assurance.payqin.com/api/public/api/user`

> Example data you need to send to get user infos :

```json
{
"email" : "judejerks@gmail.com"
}

```

> Example json data you should receive :

```json

{
  "success": true,
  "user": [
    {
      "id": 104,
      "firstname": "Jude",
      "lastname": "Ette",
      "email": "Judejerks@gmail.com",
      "phone": "+22589463461",
      "birthday": "1991-06-14",
      "customerNumber": "5e00b4da2790c",
      "shopId": "5dd690046f0d90123988958f",
      "has_payqin_account": 1,
      "created_at": "2019-12-23",
      "updated_at": "2019-12-23"
    }
  ]
}


```