# Search Director & Associated Company data by DIN

### Introduction

DIN **(Director Identification Number)** is an 8**-digit unique identification number**, allotted by the Ministry of Corporate Affairs(MCA) to any person intending to be a Director or an existing director of a company.&#x20;

### API Usecase

This API would help users to extract details of any particular director by using the director's DIN. Additionally to the information provided under [Quick Search by DIN](search-director-data-by-din.md), **this API also pulls information about the existing Directorship in other companies/ LLP's.**&#x20;

The following information will be generated**:**

* DIN
* Designation
* Date of appointment
* Name of Director
* Whether DSC required
* DSC expiry date
* PAN number of director
* Number of companies
* Father's name of the Director
* D.O.B of the director
* Address of director
* **CIN/ LLPIN**
* **Company Name**
* **Begin Date**
* **End Date**



### How to call the API

Before going for ROC Director Quick search for organizations, you first need to create an '_Organization_' **object** and you need to pass the DIN as i**dentifier** in the request body.



### API Input Guidelines

Provide correct **8-digit unique identification number i.e DIN**, Provided by MCA to the director for whom information needs to be extracted.



### Sample CURL Request

### **Step 1**: Creating Organisation Object

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                        |
| -------------- | ----------------- | --------- | ---------------------------------- |
| Authorization  | Required          | Object    | Access Token                       |
| Content-Type   | Required          | String    | Application/JSON                   |
| identifier     | Required          | String    | Contains the unique identifier ID  |
| service        | Required          | String    | Type of service - ROC              |
| callbackUrl    | Required          | String    | URL where response will be posted  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/organizations' \
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
    "accessToken": "cepk22e4y2wac5q777uwfyvzgig54l3o",
    "id": "616b90a018d6ad764a316077",
    "patronId": "6140962af6d4030eae0496e0",
    "identifier": "U74900MH2011PTC216800",
    "service": "roc"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2**: Hunt for Organisation

#### Creating ROC DIN Quick search 'hunt' request.

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

{% tab title="Hunt Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/hunts' \
--header 'Connection: keep-alive' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Content-Type: application/json' \
--data-raw '{
    "target": "Organization",
    "itemId": "<ID of the organisation object created>",
    "accessToken": "<Access token from the organisation creation request>",
    "task": "quickSearchByDin",
    "essentials": {
        "din": "00031051"
    }
}'
```
{% endtab %}
{% endtabs %}



{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name              | Description                                                                                                                                                                                                                     |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result.din                  | The director identification number of the company.                                                                                                                                                                              |
| result.designation          | Director's designation in the company                                                                                                                                                                                           |
| result.dateOfAppointment    | The date of appointment of the director to the company.                                                                                                                                                                         |
| result.Address              | The registered address of the director.                                                                                                                                                                                         |
| result.name                 | Name of the director                                                                                                                                                                                                            |
| result.whetherDscRegistered | This parameter shows whether the digital cerificates are registered and valid.                                                                                                                                                  |
| result.dscExpiryDate        | The date of expiry for the digital certificates of the director.                                                                                                                                                                |
| result.fatherName           | Father's name of the director.                                                                                                                                                                                                  |
| result.dob                  | Date of birth of Director                                                                                                                                                                                                       |
| result.noOfCompanies        |                                                                                                                                                                                                                                 |
| result.splitAddress         | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, Pincode and country. For the country category, acceptable values are “IN”, ”IND” and ”INDIA”. |
| result.listOfCompanies      |                                                                                                                                                                                                                                 |
| listOfCompanies.cin         | CIN (Corporate Identification Number) of the company                                                                                                                                                                            |
| listOfCompanies.companyName | Name of the company                                                                                                                                                                                                             |
| listOfCompanies.beginDate   | Commencement date of the directorship.                                                                                                                                                                                          |
| listOfCompanies.endDate     | End date of directorship                                                                                                                                                                                                        |
{% endtab %}

{% tab title="API Response" %}
```
{
    "target": "Organization",
    "itemId": "616a660418d6ad764a3159a3",
    "accessToken": "2c5iaz9a7vgt0fq3n59c7sj8tq2i2v9ei",
    "task": "simpleSearchByDin",
    "id": "616a674418d6ad764a3159b5",
    "essentials": {
        "din": "00031051"
    },
    "result": {
        "din": "00031051",
        "designation": "DIRECTOR",
        "dateOfAppointment": "23/08/2003",
        "address": "",
        "name": "ANANT JAIVANT TALAULICAR",
        "whetherDscRegistered": "YES",
        "dscExpiryDate": "25/03/2023",
        "fatherName": "",
        "dob": "-",
        "noOfCompanies": "15",
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
        },
        "listOfCompanies": [
            {
                "cin": "L72200PN1990PLC059594",
                "companyName": "BIRLASOFT LIMITED",
                "beginDate": "29/08/2018",
                "endDate": "-"
            },
            {
                "cin": "L34102MH1999PLC123296",
                "companyName": "ENDURANCE TECHNOLOGIES LIMITED",
                "beginDate": "25/08/2021",
                "endDate": "-"
            },
            {
                "cin": "L31901TN1984PLC011021",
                "companyName": "INDIA NIPPON ELECTRICALS LIMITED",
                "beginDate": "16/08/2019",
                "endDate": "-"
            },
            {
                "cin": "U50300PN2000PLC014889",
                "companyName": "CUMMINS AUTO SERVICES LIMITED",
                "beginDate": "05/06/2003",
                "endDate": "-"
            },
            {
                "cin": "U51909MH1952PLC014972",
                "companyName": "CUMMINS SALES AND SERVICE INDIA LIMITED",
                "beginDate": "20/03/2003",
                "endDate": "-"
            },
            {
                "cin": "L34102PN1958PLC011172",
                "companyName": "FORCE MOTORS LIMITED",
                "beginDate": "29/03/2019",
                "endDate": "-"
            },
            {
                "cin": "U74210DL1981PLC011261",
                "companyName": "JAKSON ENGINEERS LIMITED",
                "beginDate": "21/01/2021",
                "endDate": "-"
            },
            {
                "cin": "U74899DL1997PLC088808",
                "companyName": "JAKSON LIMITED",
                "beginDate": "21/01/2021",
                "endDate": "-"
            },
            {
                "cin": "L74999MH1934PLC002093",
                "companyName": "EVEREST INDUSTRIES LIMITED",
                "beginDate": "27/08/2020",
                "endDate": "-"
            },
            {
                "cin": "L29130HR1986PLC081555",
                "companyName": "THE HI-TECH GEARS LIMITED",
                "beginDate": "29/09/2018",
                "endDate": "-"
            },
            {
                "cin": "L74999PN2018PLC174192",
                "companyName": "KPIT TECHNOLOGIES LIMITED",
                "beginDate": "28/08/2019",
                "endDate": "-"
            },
            {
                "cin": "U80100MH2020NPL339827",
                "companyName": "USHAJAIVANT FOUNDATION",
                "beginDate": "19/05/2020",
                "endDate": "-"
            },
            {
                "cin": "U85300MH2021NPL368090",
                "companyName": "EVEREST FOUNDATION",
                "beginDate": "24/09/2021",
                "endDate": "-"
            }
        ],
        "listOfLLPs": [
            {
                "llpin": "AAO-3366",
                "llpName": "TRIHANS TRADING LLP",
                "beginDate": "20/02/2019",
                "endDate": "-"
            },
            {
                "llpin": "AAO-7276",
                "llpName": "REMEX FINANCE LLP",
                "beginDate": "01/04/2019",
                "endDate": "-"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/237e97585fba5da6bf15)

#### Creating Organization Object

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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b21893a1af921c8fef86)

****

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/hunts" method="post" summary="ROC DIN Simple search `hunt` request" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/hunts`

\




\


This method creates a ROC Simple Search Hunt request
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
Task to be performed - simpleSearchByDin
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.din" type="string" %}
company's-din-to-search-for
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "din": "..din..",
    "designation": "..designation..",
    "address": "..address..",
    "name": "..name..",
    "dob": "..dob..",
    "noOfCompanies": "..noOfCompanies..",
    "splitAddress": {
      "state": [
        [

        ]
      ],
      "district": [

      ],
      "city": [],
      "pincode": "...pincode...",
      "country": [
        "IN",
        "IND",
        "INDIA"
      ],
      "addressLine": "...addressLine..."
  },
  "listOfCompanies": [{
      "cinin": "..cinin..",
      "companyName": "..companyName..",
      "beginDate": "..beginDate..",
      "endDate": "..endDate..."
  }],
  "listOfLLPs": [{
        "llpin": "..llpin..",
        "llpName": "..llpName..",
        "beginDate": "..beginDate..",
        "endDate": "..endDate..."
    }]
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
    "task": "simpleSearchByDin",
    "essentials": {
    	"din": ".....director-din-to-search-for...."
    }
  }
```


{% endtab %}

{% tab title="Response parameters" %}
| PARAMETER NAME              | DESCRIPTION                                                                                                                                                                                                                   |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| din                         | The director identification number of the company.                                                                                                                                                                            |
| designation                 | The exact designation of the director in the company.                                                                                                                                                                         |
| address                     | The registered address of the director.                                                                                                                                                                                       |
| name                        | The name of the director.                                                                                                                                                                                                     |
| dob                         | The date of birth of the director.                                                                                                                                                                                            |
| noOfCompanies               | The number of companies that the director has been a part of.                                                                                                                                                                 |
| splitAddress                | This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine    | The first line of the director address is shown by this parameter.                                                                                                                                                            |
| listOfCompanies             | The list of companies that the director has been a part of or previously employed.                                                                                                                                            |
| listOfCompanies.cin         | The company identification number.                                                                                                                                                                                            |
| listOfCompanies.companyName | The company name of which the director was a member.                                                                                                                                                                          |
| listOfCompanies.beginDate   | The begin date of the director with the company.                                                                                                                                                                              |
| listOfCompanies.endDate     | The end date of the director with the company.                                                                                                                                                                                |
| listOfLLPs                  | The name of the LLP where the director had been a partner.                                                                                                                                                                    |
| listOfLLPs.llpin            | The identification number of the director with the LLP.                                                                                                                                                                       |
| listOfLLPs.llpName          | The name of the LLP.                                                                                                                                                                                                          |
| listOfLLPs.beginDate        | The begin date of the director with the LLP.                                                                                                                                                                                  |
| listOfLLPs.endDate          | The end date of the director with the LLP.                                                                                                                                                                                    |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/b21893a1af921c8fef86)
