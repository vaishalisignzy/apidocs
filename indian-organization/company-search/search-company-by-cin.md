---
description: >-
  This API allows to extract details of the company just by providing CIN as
  input.
---

# Search Company by CIN

### Introduction

Corporate Identification Number is abbreviated as CIN it's **a unique identification number that is assigned by the ROC** (Registrar of Companies) of various states under the MCA (Ministry of Corporate Affairs) to the registered companies.

### API Usecase

This API is used to retrieve basic details about the company just by entering the company's CIN as input. It helps in auto-generating the details for the user without having to manually provide the information. The following information is generated:&#x20;

* Company name
* Company type
* Paid-up capital
* Authorized capital
* Date of incorporation
* Registration number
* Registered address
* Number of directors
* Status of filing
* Category
* Sub-category

### How to call the API

Before going for further ROC detailed searches for organizations, you first need to create an '_Organization'_ **object** and you need to pass the _CIN_ as an **identifier** in the request body.

### API Input Guidelines

Provide correct CIN, it is **a unique 21 digit alpha-numeric number** provided to every registered company by the **ROC (Registrar of Companies).**

{% hint style="info" %}
You can get CIN from our API [Search by Company Name](search-by-company-name.md)&#x20;
{% endhint %}

###

### Sample CURL Request

### **Step 1**: Creating Organisation Object

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                            |
| -------------- | ----------------- | --------- | -------------------------------------- |
| Authorization  | Required          | Object    | Access Token                           |
| Content-Type   | Required          | String    | Application/JSON                       |
| identifier     | Required          | String    | Contains the unique identifier ID      |
| service        | Required          | String    | Type of service - ROC                  |
| callbackUrl    | Required          | String    | URL where the response will be posted  |
{% endtab %}

{% tab title="Response" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/organizations' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Authorization: <Access-Token>' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "identifier": "<Unique Identifier ID>",
    "service": "roc",
    "callbackUrl": "https://www.w3schools.com"
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters " %}
| **Parameter Name** | Description                                         |
| ------------------ | --------------------------------------------------- |
| callbackUrl        | URL where response will be posted                   |
| accessToken        | Access token from the organization creation request |
| id                 |                                                     |
| patronId           | Unique user id                                      |
| identifier         | Contains the unique identifier ID                   |
| service            | Type of service - ROC                               |
{% endtab %}

{% tab title="Response" %}
```
{
    "callbackUrl": "https://www.w3schools.com",
    "accessToken": "4wb1hqom61wnaugc69bneagzf1qdpf7en",
    "id": "61551ff8f0e8db4b7318ea6d",
    "patronId": "6140962af6d4030eae0496e0",
    "identifier": "<Unique Identifier ID>",
    "service": "roc"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2**: Hunt for Organisation

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                                         |
| -------------- | ----------------- | --------- | --------------------------------------------------- |
| Content-Type   | Required          | String    | Application/JSON                                    |
| target         | Required          | String    | Organization                                        |
| itemId         | Required          | String    | ID of the Organization object created               |
| accessToken    | Required          | String    | Access token from the organization creation request |
| task           | Required          | String    | Task to be performed - Company search by CIN        |
| essentials     | Required          | Object    | Contains essential input data                       |
| cin            | Required          | String    | Company's CIN to search                             |


{% endtab %}

{% tab title="Response" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/hunts' \
--header 'Content-Type: application/json' \
--data-raw '{
    "target": "Organization",
    "itemId": "<ID of the Organisation object created>",
    "accessToken": "<Access Token from organisation creation request>",
    "task": "quickSearchByCin",
    "essentials": {
        "cin": "<CIN of the company to be searched for>"
    }
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name                          | Description                                                                                                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result.numberofMembers                  | Number of members in the company                                                                                                                                                                                                |
| result.subCategory                      | Whether the company is a Government or Non-Govt company                                                                                                                                                                         |
| result.class                            | The class to which the company belongs.                                                                                                                                                                                         |
| result.companyType                      | The type of company - Public or Private limited.                                                                                                                                                                                |
| result.companyName                      | Registered name of the company                                                                                                                                                                                                  |
| result.paidUpCapital                    | Amount of money a company receives in exchange for a share of the company                                                                                                                                                       |
| result.authorisedCapital                | The maximum amount of share capital that the company is authorized                                                                                                                                                              |
| result.whetherListed                    | Whether listed on Exchange ( NSE, BSE) or not                                                                                                                                                                                   |
| result.dateofIncorporation              | Date on which company got incorporated                                                                                                                                                                                          |
| result.registrationNumber               | Registration number of the company got from ROC                                                                                                                                                                                 |
| result.registeredAddress                | The Registered address of the company                                                                                                                                                                                           |
| result.category                         | Which type of limited company it is whether Limited by shares or Limited by Guarantee                                                                                                                                           |
| result.cin                              | CIN (Corporate Identification Number) of the company                                                                                                                                                                            |
| result.rocOffice                        | Registrar to which company comes under                                                                                                                                                                                          |
| result.noOfDirectors                    | Number of directors the company has                                                                                                                                                                                             |
| result.addressOtherThanRegisteredOffice | Any other registered address of the company                                                                                                                                                                                     |
| result.emailId                          | Registered email Id of the company with the ROC                                                                                                                                                                                 |
| result.splitAddress                     | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, Pincode and country. For the country category, acceptable values are “IN”, ”IND” and ”INDIA”. |
| result.natureOfBusiness                 | The nature of the business conducted by the company. For ex: Supplier of Services.                                                                                                                                              |
| result.activeCompliance                 |                                                                                                                                                                                                                                 |
| result.status                           | Whether a company is in operation or not                                                                                                                                                                                        |
| result.statusForEfiling                 | Whether company is filing its return on regular basis or not with ROC. If yes than Active else Inactive                                                                                                                         |


{% endtab %}

{% tab title="API Response" %}
```
{
    "target": "Organization",
    "itemId": "61551e24f0e8db4b7318ea5b",
    "accessToken": "u2ig3e1uhcpgok3c6enbbgxarpdsozkre",
    "task": "quickSearchByCin",
    "id": "615523a1f0e8db4b7318eaa0",
    "essentials": {
        "cin": "U74999PN2015PTC157118"
    },
    "result": {
        "numberOfMembers": "0",
        "subCategory": "NON-GOVT COMPANY",
        "class": "PRIVATE",
        "companyType": "INDIAN COMPANY",
        "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
        "paidUpCapital": "111190.0",
        "authorisedCapital": "1000000.0",
        "whetherListed": "UNLISTED",
        "dateOfIncorporation": "03/11/2015",
        "registrationNumber": "157118",
        "registeredAddress": "18 B, KUBERA BAHAR BUNGLOWS, SOC 131 2, BANER PASHAN LINK ROAD PUNE MH 411021 IN",
        "category": "COMPANY LIMITED BY SHARES",
        "cin": "U74999PN2015PTC157118",
        "rocOffice": "ROC-PUNE",
        "noOfDirectors": "2",
        "addressOtherThanRegisteredOffice": "",
        "emailId": "arpitratan@gmail.com",
        "emailID": "arpitratan@gmail.com",
        "splitAddress": {
            "district": [
                "PUNE"
            ],
            "state": [
                [
                    "MAHARASHTRA",
                    "MH"
                ]
            ],
            "city": [
                "PUNE"
            ],
            "pincode": "411021",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "18 B,KUBERA BAHAR BUNGLOWS,SOC 131 2,BANER PASHAN LINK ROAD"
        },
        "natureOfBusiness": "OTHER BUSINESS ACTIVITIES N.E.C.",
        "activeCompliance": "",
        "status": "ACTIVE",
        "statusForEfiling": "ACTIVE"
    }
}
```
{% endtab %}
{% endtabs %}



### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |

