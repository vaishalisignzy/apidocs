# Search Detailed Company and Director Details by CIN

### Introduction

The ROC Detailed Search API, as the name suggests it returns details of the company along with the in-depth detail of the directors including all company's or LLP's name and their CIN/ LLPIN in which he/she is appointed as a director.

### API Usecase

This API is used to retrieve basic details about the company just by entering the company's CIN as input. It helps in auto-generating the details for the user without having to manually provide the information. The following information is generated:&#x20;

**Information about the Company**

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

**Information about the Directors**

* DIN
* Designation
* Date of appointment
* Address of director
* Name of Director
* Whether DSC required
* DSC expiry date
* PAN number of director
* Number of companies
* Father's name of the Director
* D.O.B of the director
* LLPIN/ CIN
* LLP name/ Company name
* Begin Date
* End Date

### How to call the API

Before going for further ROC detailed searches for organizations, you first need to create an '_Organization'_ **object** and you need to pass the _CIN_ as an **identifier** in the request body.

### API Input Guidelines

Provide correct CIN, it is **a unique 21 digit alpha-numeric number** provided to every registered company by the **ROC (Registrar of Companies).**

{% hint style="info" %}
You can get CIN from our API [Search by Company Name](search-by-company-name.md)&#x20;
{% endhint %}

### Sample CURL Request

### **Step 1**: Creating Organisation Object

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                        |
| -------------- | ----------------- | --------- | ---------------------------------- |
| Authorization  | Required          | String    | Access Token                       |
| Content-Type   | Required          | String    | Application/JSON                   |
| identifier     | Required          | String    | Contains the unique identifier ID  |
| service        | Required          | String    | Type of service - ROC              |
| callbackUrl    | Required          | String    | URL where response will be posted  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/organizations' \
--header 'Connection: keep-alive' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--data-raw '{
    "identifier": "U74900MH2011PTC216800",
    "service": "roc",
    "callbackUrl": "https://www.w3schools.com"
}'

```
{% endtab %}
{% endtabs %}

****

**Response Details**

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
    "accessToken": "p19ncaiwggm3e8mwa33jikv44596l06d",
    "id": "6155a6e5f0e8db4b7318fce9",
    "patronId": "6140962af6d4030eae0496e0",
    "identifier": "U74900MH2011PTC216800",
    "service": "roc"
}
```
{% endtab %}
{% endtabs %}

****

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
| cin            | Required          | String    | Company's CIN to searc                              |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/hunts' \
--header 'Connection: keep-alive' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Content-Type: application/json' \
--data-raw '{
    "target": "Organization",
    "itemId": "6155a6a7f0e8db4b7318fcd5",
    "accessToken": "mw4esyjkdrty7562uxqvwq9jyukvlws7u",
    "task": "simpleSearchByCin",
    "essentials": {
    "cin": "U74999PN2015PTC157118"
    
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
| directorDetails                         | This parameter displays the details of the company director(s).                                                                                                                                                                 |
| directorDetails.din                     | The director identification number of the company.                                                                                                                                                                              |
| directorDetails.dateOfAppointment       | The date of appointment of the director to the company.                                                                                                                                                                         |
| directorDetails.address                 | The registered address of the director.                                                                                                                                                                                         |
| directorDetails.name                    | The name of the director.                                                                                                                                                                                                       |
| directorDetails.whetherDscRegistered    | This parameter shows whether the digital cerificates are registered and valid.                                                                                                                                                  |
| directorDetails.dscExpiryDate           | The date of expiry for the digital certificates of the director.                                                                                                                                                                |
| directorDetails.pan                     | The PAN number of the company director.                                                                                                                                                                                         |
| directorDetails.name                    | The name of the director.                                                                                                                                                                                                       |
| directorDetails.fatherName              | The father name of the director.                                                                                                                                                                                                |
| directorDetails.dob                     | The date of birth of the director.                                                                                                                                                                                              |
| otherDirectorships                      | This parameter shows whether the director of the company being searched has been a director of other companies and shows the details.                                                                                           |
| otherDirectorships.listOfCompanies      | This parameter shows the information about the companies of which the director has served as director.                                                                                                                          |
| listOfCompanies.cin                     | The company identification number.                                                                                                                                                                                              |
| listOfCompanies.companyName             | The company name for which the director is a member director.                                                                                                                                                                   |
| listOfCompanies.beginDate               | Commencement date of the directorship.                                                                                                                                                                                          |
| listOfCompanies..endDate                | The end date of the directorship.                                                                                                                                                                                               |
| otherDirectorships.listOfLLPs           | This parameter shows the information about the companies of which the director has served as director.                                                                                                                          |
| listOfLLP.llpin                         | Limited Liability Partnership Identification Number (LLPIN) is a unique 7 digit alphanumeric code assigned to LLPs by the Registrar of Companies during company incorporation.                                                  |
| listOfLLPs.llpName                      | Name of the LLP                                                                                                                                                                                                                 |
| listOfLLPs.beginDate                    | Commencement date of the directorship.                                                                                                                                                                                          |
| listOfLLPs.endDate                      | End date of directorship                                                                                                                                                                                                        |
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "target": "Organization",
    "itemId": "615e7968bd40d75f8360f2d7",
    "accessToken": "ht05986ftqquumcrzyrofb6axizm6j",
    "task": "detailedSearchByCin",
    "id": "615e79e4bd40d75f8360f2eb",
    "essentials": {
        "cin": "U74999PN2015PTC157118"
    },
    "result": {
        "numberOfMembers": "0",
        "subCategory": "NON-GOVT COMPANY",
        "class": "PRIVATE",
        "companyType": "INDIAN COMPANY",
        "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
        "paidUpCapital": "1100100",
        "authorisedCapital": "2100000",
        "whetherListed": "UNLISTED",
        "dateOfIncorporation": "03/11/2015",
        "lastAgmDate": "29/12/2020",
        "registrationNumber": "157118",
        "registeredAddress": "18 B, KUBERA BAHAR BUNGLOWS, SOC 131 2, BANER PASHAN LINK ROAD PUNE MH 411021 IN",
        "activeCompliance": "ACTIVE COMPLIANT",
        "suspendedAtStockExchange": "",
        "balanceSheetDate": "31/03/2020",
        "category": "COMPANY LIMITED BY SHARES",
        "status": "ACTIVE",
        "cin": "U74999PN2015PTC157118",
        "rocOffice": "ROC-PUNE",
        "countryOfIncorporation": "",
        "descriptionOfMainDivision": "",
        "addressOtherThanRegisteredOffice": "",
        "emailId": "arpit@signzy.com",
        "emailID": "arpit@signzy.com",
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
        "noOfDirectors": "6",
        "statusForEfiling": "ACTIVE",
        "pan": "AAWCS3552Q",
        "directorDetails": [
            {
                "din": "05255419",
                "designation": "NOMINEE DIRECTOR",
                "dateOfAppointment": "13/03/2019",
                "address": "",
                "name": "ALOK GOYAL",
                "whetherDscRegistered": "YES",
                "dscExpiryDate": "24/09/2022",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "L72200MH2000PLC125319",
                            "companyName": "ECLERX SERVICES LIMITED",
                            "beginDate": "23/08/2012",
                            "endDate": "-"
                        },
                        {
                            "cin": "U72200KA2010PTC055487",
                            "companyName": "QUICKO TECHNOSOFT LABS PRIVATE LIMITED",
                            "beginDate": "08/05/2017",
                            "endDate": "-"
                        },
                        {
                            "cin": "U01403HR2012PTC045790",
                            "companyName": "ISKCON FARM LANDS PRIVATE LIMITED",
                            "beginDate": "01/05/2012",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "13/03/2019",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999KA2016PTC095921",
                            "companyName": "930 TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "07/07/2017",
                            "endDate": "-"
                        },
                        {
                            "cin": "U63090KA2017PTC099338",
                            "companyName": "LOADSHARE NETWORKS PRIVATE LIMITED",
                            "beginDate": "13/06/2018",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": [
                        {
                            "llpin": "AAG-0546",
                            "llpName": "STELLARIS ADVISORS LLP",
                            "beginDate": "20/05/2016",
                            "endDate": "-"
                        },
                        {
                            "llpin": "AAQ-7660",
                            "llpName": "STELLARIS PARTNERS 2 LLP",
                            "beginDate": "10/10/2019",
                            "endDate": "-"
                        },
                        {
                            "llpin": "AAQ-7653",
                            "llpName": "STELLARIS VENTURE ADVISORS 2 LLP",
                            "beginDate": "10/10/2019",
                            "endDate": "-"
                        }
                    ]
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            },
            {
                "din": "06673269",
                "designation": "DIRECTOR",
                "dateOfAppointment": "03/11/2015",
                "address": "",
                "name": "ARPIT RATAN",
                "whetherDscRegistered": "YES",
                "dscExpiryDate": "11/10/2021",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "U74999PN2013PTC149042",
                            "companyName": "RAU AGRO SERVICES PRIVATE LIMITED",
                            "beginDate": "07/10/2013",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999PN2013PTC149043",
                            "companyName": "RAU HOSPITALITY SERVICES PRIVATE LIMITED",
                            "beginDate": "07/10/2013",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999PN2013PTC149021",
                            "companyName": "JBRC HR SOLUTIONS PRIVATE LIMITED",
                            "beginDate": "03/10/2013",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "03/11/2015",
                            "endDate": "-"
                        },
                        {
                            "cin": "U67100MH2021PTC362743",
                            "companyName": "WAYNE SECURE DIGITAL RTA PRIVATE LIMITED",
                            "beginDate": "25/06/2021",
                            "endDate": "-"
                        },
                        {
                            "cin": "U80902KA2021NPL151048",
                            "companyName": "FORTAP FOUNDATION",
                            "beginDate": "26/08/2021",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": []
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            },
            {
                "din": "06770480",
                "designation": "DIRECTOR",
                "dateOfAppointment": "24/11/2016",
                "address": "",
                "name": "ANKIT RATAN",
                "whetherDscRegistered": "YES",
                "dscExpiryDate": "23/03/2023",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "24/11/2016",
                            "endDate": "-"
                        },
                        {
                            "cin": "U67100MH2021PTC362743",
                            "companyName": "WAYNE SECURE DIGITAL RTA PRIVATE LIMITED",
                            "beginDate": "25/06/2021",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": []
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            },
            {
                "din": "07169578",
                "designation": "DIRECTOR",
                "dateOfAppointment": "16/10/2020",
                "address": "",
                "name": "BALAJI SRINIVASA",
                "whetherDscRegistered": "YES",
                "dscExpiryDate": "16/04/2023",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "16/10/2020",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": [
                        {
                            "llpin": "AAM-2989",
                            "llpName": "UNITARY INVESTMENT MANAGEMENT LLP",
                            "beginDate": "12/02/2020",
                            "endDate": "-"
                        }
                    ]
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            },
            {
                "din": "08126225",
                "designation": "DIRECTOR",
                "dateOfAppointment": "05/12/2020",
                "address": "",
                "name": "PIYUSH KHARBANDA",
                "whetherDscRegistered": "YES",
                "dscExpiryDate": "02/07/2022",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "05/12/2020",
                            "endDate": "-"
                        },
                        {
                            "cin": "U72900MH2016PTC282573",
                            "companyName": "ONEMI TECHNOLOGY SOLUTIONS PRIVATE LIMITED",
                            "beginDate": "26/12/2018",
                            "endDate": "-"
                        },
                        {
                            "cin": "U74999KA2017FTC105264",
                            "companyName": "VERTEX VENTURES SEA MANAGEMENT INDIA PRIVATE LIMITED",
                            "beginDate": "27/09/2018",
                            "endDate": "-"
                        },
                        {
                            "cin": "U72900KA2019PTC129117",
                            "companyName": "PLUS HEALTH TECH VENTURES PRIVATE LIMITED",
                            "beginDate": "20/05/2021",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": []
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            },
            {
                "din": "08163212",
                "designation": "DIRECTOR",
                "dateOfAppointment": "20/06/2018",
                "address": "",
                "name": "ANKUR PANDEY",
                "whetherDscRegistered": "EXPIRED",
                "dscExpiryDate": "06/06/2020",
                "pan": "",
                "noOfCompanies": "",
                "fatherName": "",
                "dob": "-",
                "otherDirectorships": {
                    "listOfCompanies": [
                        {
                            "cin": "U74999PN2015PTC157118",
                            "companyName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                            "beginDate": "29/09/2018",
                            "endDate": "-"
                        }
                    ],
                    "listOfLLPs": []
                },
                "splitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": ""
                }
            }
        ]
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
|             |                                        |







#### Creating Organization Object

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronId.../organizations" method="post" summary="Search Company by CIN" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronId.../organizations`

\




\


This method is used to search for the thorough details of a company by its Company identification Number (CIN)
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Access Token
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="identifier" type="string" %}
Contains the unique identifier ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="service" type="string" %}
Type of service - roc
{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackURL" type="string" %}
The call back URL
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
        "callbackUrl": "...callback...",
        "accessToken": "...accestoken....",
        "id": "....id...",
        "patronId": "....patronid...",
        "identifier": "...identifier...",
        "service": "roc"
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "identifier": "U74900MH2011PTC216800",
      "service": "roc",
      "callbackUrl": "...callback..."
    }

```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                            |
| -------------- | ---------------------------------------------------------------------- |
| callbackUrl    | This parameter contains the URl where the response is to be posted.    |
| accesstoken    | The access token that is received during login request.                |
| id             | The parameter which contains the userId received during login request. |
| identifier     | The unique identifier ID.                                              |
| service        | The type of Signzy service - "roc search".                             |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/d2ce147287219f4213ce)



**Company's information**

The API returns the following data about the company

1. companyName
2. rocOffice
3. registrationNumber
4. category
5. subCategory
6. class
7. authorisedCapital
8. paidUpCapital
9. numberOfMembers
10. dateOfIncorporation
11. registeredAddress
12. emailId
13. whetherListed
14. lastAgmDate
15. balanceSheetDate
16. statusForEfiling
17. addressOtherThanRegisteredOffice
18. suspendedAtStockExchange
19. cin
20. directorDetails

**Director's information**

For each director of the company you will receive the following information.

1. din
2. designation
3. dateOfAppointment
4. address
5. dscExpiryDate
6. name
7. whetherDscRegistered
8. fatherName
9. dob
10. pan
11. OtherDirectorships

**For OtherDirectorships's information**

For each OtherDirectorship of the director you will receive the following information.

1. companyName
2. beginDate
3. cin
4. endDate

#### Creating ROC Detailed search \`hunt\` request

Use the following exchange parameters for ROC search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/hunts" method="post" summary="ROC Detailed search `hunt` request" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/hunts`

\




\


This method creates a ROC Detailed Search Hunt request
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="target" type="string" %}
Organization
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemId" type="string" %}
id-of-the-organzation-object-created
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="string" %}
access-token-from-the-organization-creation-request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Task" type="string" %}
Task to be performed - detailedSearchByCin
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.cin" type="string" %}
company's-cin-to-search-for
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
      "companyName": "...company name...",
      "rocOffice": "...roc office....",
      "registrationNumber": "....Reg. number....",
      "category": "...category",
      "subCategory": "...subcategory...",
      "class": "...class...",
      "authorisedCapital": "..authorisedCapital..",
      "paidUpCapital": "...paidUpCapital...",
      "numberOfMembers": "....numberOfMembers..",
      "dateOfIncorporation": "...dateOfIncorporation...",
      "registeredAddress": "...registeredAddress..",
      "emailId": "..emailId....",
      "whetherListed": "...whetherListed...",
      "lastAgmDate": "...lastAgmDate...",
      "balanceSheetDate": "31/03/2016",
      "statusForEfiling": "Active",
      "addressOtherThanRegisteredOffice": "",
      "suspendedAtStockExchange": "",
      "cin": "...cin...",
      "natureOfBusiness": "...natureOfBusiness...",
      "directorDetails": [{
        "din": "....din...",
        "designation": "....designation...",
        "dateOfAppointment": "03/11/2015",
        "address": "...address...",
        "dscExpiryDate": "...dscExpiryDate..",
        "name": "....name....",
        "whetherDscRegistered": "Yes",
        "splitAddress": {
          "state": [
            []
          ],
          "district": [],
          "city": [],
          "pincode": "...pincode...",
          "country": ["IN", "IND", "INDIA"],
          "addressLine": ".....address line...."
        },
        "fatherName": "...fatherName...",
        "dob": "08/03/1988",
        "pan": "",
        "otherDirectorships": {
          "listOfLLPs": [],
          "listOfCompanies": [{
            "cin": "...cin....",
            "companyName": ".....company name....",
            "beginDate": ".....begindate...",
            "endDate": "...end date...."
          }, {
            "cin": "...cin....",
            "companyName": ".....company name....",
            "beginDate": ".....begindate...",
            "endDate": "...end date...."
          }, {
            "cin": "...cin....",
            "companyName": ".....company name....",
            "beginDate": ".....begindate...",
            "endDate": "...end date...."
          }, {
            "cin": "...cin....",
            "companyName": ".....company name....",
            "beginDate": ".....begindate...",
            "endDate": "...end date...."
          }],
          "din": "...din..."
        }
      }
      }],
      "splitAddress": {
        "state": [
          [

          ]
        ],
        "district": ...dist..,
        "city": ...city...,
        "pincode": "..pincode...",
        "country": ["IN", "IND", "INDIA"],
        "addressLine": ".....addressLine...."
      },
      "pan": ""
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
  {
    "target": "Organization",
    "itemId": "....id-of-the-organzation-object-created.....",
    "accessToken": ".....access-token-from-the-organization-creation-request.....",
    "task": "detailedSearchByCin",
    "essentials": {
    	"cin": ".....company's-cin-to-search-for...."
    }
  }

```
{% endtab %}

{% tab title="Response Parameters" %}


| PARAMETER NAME                    | DESCRIPTION                                                                                                                                                                                                                           |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| companyName                       | The name of the company.                                                                                                                                                                                                              |
| rocOffice                         | The office name of the Registrar Of Companies to which the company being searched belongs to.                                                                                                                                         |
| registrationNumber                | The registration number of the company.                                                                                                                                                                                               |
| category                          | The type of category the company belongs to.                                                                                                                                                                                          |
| subCategory                       | The sub category to which the company belongs to.                                                                                                                                                                                     |
| class                             | The class to which the company belongs.                                                                                                                                                                                               |
| authorisedCapital                 | The amount of capital authorised to the company.                                                                                                                                                                                      |
| paidUpCapital                     | The amount of paid up capital for the company being searched.                                                                                                                                                                         |
| numberOfMembers                   | The number of members associated with the company.                                                                                                                                                                                    |
| dateOfIncorporation               | The date of incorporation of the company as registered with the CIN.                                                                                                                                                                  |
| registeredAddress                 | The registered address of the company.                                                                                                                                                                                                |
| pan                               | The PAN number of the company.                                                                                                                                                                                                        |
| emailId                           | The registered email ID of the company.                                                                                                                                                                                               |
| whetherListed                     | This parameter shows whether the company is listed with the Registrar Of Companies.                                                                                                                                                   |
| lastAgmDate                       | The date of the last annual general meeting.                                                                                                                                                                                          |
| balanceSheetDate                  | The available date on the balance sheet of the company.                                                                                                                                                                               |
| statusForEfiling                  | The current status of E-filing for the company.                                                                                                                                                                                       |
| addressOtherThanRegisteredOffice  | The address other than the registered office address of the company, if any.                                                                                                                                                          |
| suspendedAtStockExchange          | This parameter shows whether the company has been suspended at stock exchange.                                                                                                                                                        |
| natureOfBusiness                  | The nature of business conducted by the company. For ex: Supplier of Services.                                                                                                                                                        |
| splitAddress                      | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.          |
| splitAddress.addressLine          | The first line of the company address is shown by this parameter.                                                                                                                                                                     |
| cin                               | The unique company identification number.                                                                                                                                                                                             |
| directorDetails                   | This parameter displays the details of the company director(s).                                                                                                                                                                       |
| directorDetails.name              | The name of the director.                                                                                                                                                                                                             |
| directorDetails.fatherName        | The father name of the director.                                                                                                                                                                                                      |
| directorDetails.dob               | The date of birth of the director.                                                                                                                                                                                                    |
| directorDetails.pan               | The PAN number of the company director.                                                                                                                                                                                               |
| directorDetails.din               | The director identification number of the company.                                                                                                                                                                                    |
| directorDetails.dscExpiryDate     | The date of expiry for the digital certificates of the director.                                                                                                                                                                      |
| directorDetails.dateOfAppointment | The date of appointment of the director to the company.                                                                                                                                                                               |
| directorDetails.designation       | The exact designation of the director in the company.                                                                                                                                                                                 |
| directorDetails.address           | The registered address of the director.                                                                                                                                                                                               |
| directorDetails.splitAddress      | This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.         |
| splitAddress.addressLine          | The first line of the director address is shown by this parameter.                                                                                                                                                                    |
| whetherDscRegistered              | This parameter shows whether the digital cerificates are registered and valid.                                                                                                                                                        |
| otherDirectorships                | This parameter shows whether the director of the company being searched has been a director of other companies and shows the details.                                                                                                 |
| otherDirectorships.listOfLLPs     | This parameter shows the information about the companies of which the director has served as director.                                                                                                                                |
| listOfLLPs.listOfCompanies        | The list of companies for which the director is a member.                                                                                                                                                                             |
| listOfCompanies.cin               | The company identification number.                                                                                                                                                                                                    |
| listOfCompanies.companyName       | The company name for which the director is a member director.                                                                                                                                                                         |
| listOfCompanies.beginDate         | The begin date of the directorship.                                                                                                                                                                                                   |
| listOfCompanies..endDate          | The end date of the directorship.                                                                                                                                                                                                     |
| otherDirectorships.splitAddress   | This parameter distinguishes the various parts of the address of the director company into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| otherDirectorships.pan            | The PAN number of the company where the director was a member.                                                                                                                                                                        |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/d2ce147287219f4213ce)
