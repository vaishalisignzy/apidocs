# Detailed Search by GSTIN

### &#xD;Introduction

Every GST Certificate holds a unique 15-digit alphanumeric GST Identification Number or GSTIN for the business. This is just like the ID number on any other ID card. Using the GSTIN Based Search API, Signzy uses its proprietary algorithms to extract the details of the GSTIN-registered business and its owner.

### API Usecase

Similar to GSTIN Search API, the detailed search is designed with the objective of generating even more details about the business and its owner using the GSTIN.&#x20;

**The following information will be extracted :**

* Reference ID
* TIN Number
* Registration Type
* Constitution of business
* Legal name of business
* Trade name of business
* Centre Jurisdiction
* State Jurisdiction
* Registration Date
* Date of tax payment
* Tax payer type
* Cancellation date
* Nature of business activities
* Principal place of address

### How to call the API

You will need to login before sending PAN Number request. You are required to pass the access token received from the login call, as authorization header in the GSTIN request along with GSTIN Number.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTIN based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization    | Required | String | Access Token                          |
| ---------------- | -------- | ------ | ------------------------------------- |
| Content-Type     | Required | String | Application/JSON                      |
| task             | Required | String | Type of task - GSTIN DETAILED SEARCH  |
| essentials.gstin | Required | String | GSTIN number to be searched           |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/gstns' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "<TASK-Detailed GSTIN Search>",
    "essentials": {
        "gstin": "<GSTIN Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME                          | DESCRIPTION                                                                                                                                                                                                                                        |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| task                                    | The type of task to be performed - "detailed GSTIN Search"                                                                                                                                                                                         |
| essentials                              | This parameter contains the essential data for generating output.                                                                                                                                                                                  |
| essentials.gstIn                        | The GST identification number that is required for the GST Search.                                                                                                                                                                                 |
| id                                      | The access token that was received during login request.                                                                                                                                                                                           |
| patronId                                | This parameter is returned as userId parameter of login request.                                                                                                                                                                                   |
| result                                  | The final response parameters are displayed here.                                                                                                                                                                                                  |
| result.gstnRecords                      | The detailed information associated with the records of the GST number are contained in this parameter.                                                                                                                                            |
| gstnRecords.tinNumber                   | The TIN number associated with the GST number is displayed by this parameter.                                                                                                                                                                      |
| gstnRecords.regType                     | The type of registration done for the GST number being searched is displayed by this parameter.                                                                                                                                                    |
| gstnRecords.gstinRefId                  | The reference ID associated with the GSTIN is contained in this parameter.                                                                                                                                                                         |
| gstnRecords.applicationStatus           | The current status of the application of the GST number.                                                                                                                                                                                           |
| gstnRecords.registrationName            | The registration name of the individual/business owner associated with the GST number.                                                                                                                                                             |
| gstnRecords.mobNum                      | The mobile number of the individual/ business owner associated with the GST number.                                                                                                                                                                |
| gstnRecords.emailId                     | The email ID of the individual/ business owner associated with the GST number.                                                                                                                                                                     |
| gstnRecords.gstin                       | The GST identification number for which PAN number is being searched.                                                                                                                                                                              |
| result.gstnDetailed                     | This parameter provides detailed information about the owner/business to which the GST number has been assigned.                                                                                                                                   |
| gstnDetailed.constitutionOfBusiness     | This parameter denotes the type of company or organisation i.e Public or Private Limited Company.                                                                                                                                                  |
| gstnDetailed.legalNameOfBusiness        | The legal name of the business as registered with the GST number.                                                                                                                                                                                  |
| gstnDetailed.tradeNameOfBusiness        | The trading/commercial name under which the company/organization operates.                                                                                                                                                                         |
| gstnDetailed.centreJurisdiction         | This parameter assigns a code that depicts jurisdiction of the central government on the company.                                                                                                                                                  |
| gstnDetailed.stateJurisdiction          | This parameter assigns a code that depicts jurisdiction of the state government on the company.                                                                                                                                                    |
| gstnDetailed.registrationDate           | The date of registration of GST for the business/organization is displayed by this parameter.                                                                                                                                                      |
| gstnDetailed.taxPayerDate               | The due date for the taxpayer associated with the GST number.                                                                                                                                                                                      |
| gstnDetailed.taxPayerType               | This parameter denotes the type of taxpayer i.e regular taxpayer.                                                                                                                                                                                  |
| gstnDetailed.gstinStatus                | The current status of the GST identification number is active/inactive.                                                                                                                                                                            |
| gstnDetailed.cancellationDate           | This parameter shows the date of cancellation for the GST if applicable.                                                                                                                                                                           |
| gstnDetailed.natureOfBusinessActivities | This parameter shows the type of business provider. Ex: Supplier of Services.                                                                                                                                                                      |
| gstnDetailed.complianceRating           | The compliance rating that has been assigned to the business/organization.                                                                                                                                                                         |
| gstnDetailed.directorNames              | The names of the directors are contained in this parameter.                                                                                                                                                                                        |
| gstnDetailed.principalPlaceAddress      | This parameter contains the details of the principal address of the business/organization.                                                                                                                                                         |
| principalPlaceAddress.emailId           | The email ID of the business.                                                                                                                                                                                                                      |
| principalPlaceAddress.address           | The principal address of the business/organization.                                                                                                                                                                                                |
| principalPlaceAddress.natureOfBusiness  | The type of business/organization.                                                                                                                                                                                                                 |
| principalPlaceAddress.mobile            | The mobile number registered to the owner/business with the GST.                                                                                                                                                                                   |
| principalPlaceAddress.lastUpdatedDate   | This parameter contains the date when the details were last updated for the particular business/organization.                                                                                                                                      |
| principalPlaceAddress.splitAddress      | This parameter distinguishes the various parts of the address of the principal place address into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD;  |
| gstnDetailed.additionalPlaceAddress     | This parameter contains the details of the additional address of the business/organization.                                                                                                                                                        |
| additionalPlaceAddress.emailId          | The email ID of the additional place address of the business.                                                                                                                                                                                      |
| additionalPlaceAddress.address          | The additional address of the business/organization.                                                                                                                                                                                               |
| additionalPlaceAddress.natureOfBusiness | The additional type of business/organization.                                                                                                                                                                                                      |
| additionalPlaceAddress.mobile           | The mobile number registered to the additional address of the owner/business with the GST.                                                                                                                                                         |
| additionalPlaceAddress.lastUpdatedDate  | This parameter contains the date when the details were last updated for the additional place address of the particular business/organization.                                                                                                      |
| additionalPlaceAddress.splitAddress     | This parameter distinguishes the various parts of the address of the additional place address into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD; |
| splitaddress.addressLine                | The first line of the registered principal/additional address is displayed by this parameter.                                                                                                                                                      |
| gstnDetailed.gstin                      | The GST identification number.                                                                                                                                                                                                                     |
{% endtab %}

{% tab title="Response" %}
```
{
    "task": "<TASK - Detailed GSTIN Search>",
    "essentials": {
        "gstin": "<GSTIN NUMBER>"
    },
    "id": "<Access token received from login request>",
    "patronId": "<Patron ID>",
    "result": {
        "gstnDetailed": {
            "constitutionOfBusiness": "PROPRIETORSHIP",
            "legalNameOfBusiness": "SAGAR MAHESHKUMAR PATEL",
            "tradeNameOfBusiness": "ASHISH ENGINEERING WORKS",
            "centreJurisdiction": "COMMISSIONERATE - MUMBAI-WEST,DIVISION - DIVISION X,RANGE - RANGE-I",
            "stateJurisdiction": "STATE - MAHARASHTRA,ZONE - MUMBAI_SOUTH_WEST,DIVISION - KANDIVALI,CHARGE - MALAD-WEST_704 (JURISDICTIONAL OFFICE)",
            "registrationDate": "01/07/2017",
            "taxPayerDate": "",
            "taxPayerType": "REGULAR",
            "gstinStatus": "ACTIVE",
            "cancellationDate": "",
            "natureOfBusinessActivities": [
                "OFFICE / SALE OFFICE"
            ],
            "principalPlaceLatitude": "",
            "principalPlaceLongitude": "",
            "principalPlaceStreet": "",
            "principalPlaceLocality": "",
            "principalPlaceCity": "",
            "principalPlaceDistrict": "",
            "principalPlaceState": "",
            "principalPlacePincode": "",
            "additionalPlaceLatitude": "",
            "additionalPlaceLongitude": "",
            "additionalPlaceStreet": "",
            "additionalPlaceLocality": "",
            "additionalPlaceCity": "",
            "additionalPlaceDistrict": "",
            "additionalPlaceState": "",
            "additionalPlacePincode": "",
            "complianceRating": "NA",
            "additionalPlaceAddress": [
                {
                    "emailId": "sagar@celltone21.com",
                    "address": "179, Bombay Talkies Compound, Opp. Shed No. 35, Malad West, Mumbai Suburban, Maharashtra, 400064",
                    "natureOfBusiness": "OFFICE / SALE OFFICE",
                    "mobile": "9987059994",
                    "lastUpdatedDate": "NA",
                    "splitAddress": {
                        "district": [
                            "MUMBAI"
                        ],
                        "state": [
                            [
                                "MAHARASHTRA",
                                "MH"
                            ]
                        ],
                        "city": [
                            "MUMBAI"
                        ],
                        "pincode": "400064",
                        "country": [
                            "IN",
                            "IND",
                            "INDIA"
                        ],
                        "addressLine": "179,BOMBAY TALKIES COMPOUND,OPP.SHED NO.35,MALAD WEST,SUBURBAN"
                    }
                }
            ],
            "directorNames": [
                "SAGAR MAHESHKUMAR PATEL"
            ],
            "principalPlaceAddress": {
                "emailId": "sagar@celltone21.com",
                "address": "A-1102, 11th, Rustomjee Riviera Bldg.,, Marve Road, Malad West, Mumbai Suburban, Maharashtra, 400064",
                "natureOfBusiness": "OFFICE / SALE OFFICE",
                "mobile": "9987059994",
                "lastUpdatedDate": "NA",
                "splitAddress": {
                    "district": [
                        "MUMBAI"
                    ],
                    "state": [
                        [
                            "MAHARASHTRA",
                            "MH"
                        ]
                    ],
                    "city": [
                        "MUMBAI"
                    ],
                    "pincode": "400064",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "A-1102,11TH,RUSTOMJEE RIVIERA BLDG.MARVE ROAD,MALAD WEST,SUBURBAN"
                }
            }
        },
        "gstnRecords": [
            {
                "applicationStatus": "",
                "registrationName": "SAGAR MAHESHKUMAR PATEL",
                "mobNum": "",
                "regType": "",
                "emailId": "",
                "tinNumber": "",
                "gstinRefId": "",
                "gstin": "27AOKPP9482P1ZQ"
            }
        ],
        "gstin": "27AOKPP9482P1ZQ",
        "annualAggregateTurnOver": "Slab: Rs. 40 lakhs to 1.5 Cr.",
        "grossTotalIncome": "NA",
        "grossTotalIncomeFinancialYear": "",
        "filingStatus": [
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "September",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "11/10/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "August",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "09/09/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "July",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "11/08/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "June",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "10/07/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "May",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "21/06/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "April",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "26/05/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "March",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "09/04/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "February",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "09/03/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "January",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "09/02/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "December",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "12/01/2021",
                "gstType": "GSTR1",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "September",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "18/10/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "August",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "22/09/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "July",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "18/08/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "June",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "16/07/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "May",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "01/07/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2021-2022",
                "monthOfFiling": "April",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "14/06/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "March",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "18/04/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "February",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "19/03/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "January",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "19/02/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2020-2021",
                "monthOfFiling": "December",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "22/01/2021",
                "gstType": "GSTR3B",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            },
            {
                "filingYear": "2017-2018",
                "monthOfFiling": "Annual",
                "methodOfFilling": "ONLINE",
                "dateOfFiling": "06/08/2019",
                "gstType": "GSTR9",
                "annualReturn": "NA",
                "gstStatus": "Filed"
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |



Use the following exchange parameters for GSTIN based search

{% swagger baseUrl="https://production.signzy.tech" path="/api/v2/patrons/...patronID.../gstns" method="post" summary=" GSTIN Search " %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../gstns`

\




\


This method is used to extract the details of GST certificates using GSTIN
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - GSTIN Search
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.gstin" type="string" %}
GSTIN for which the details are required.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "task" : "detailedGstinSearch",
    "essentials": {
         "gstin": "..gstin.."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result":{
        "gstnRecords": [
          {
            "regType": "..registrationType...",
            "emailId": "..emailId...",
            "applicationStatus": "...application Status...",
            "registrationName": "...registered Name...",
            "gstinRefId": "...GSTIN Reference Id...",
            "tinNumber": "...Tin Number...",
            "mobNum": "...Mobile Number...",
            "gstin": "...gstin Number..."
        }

        ],
        "gstnDetailed": {
            "constitutionOfBusiness": "....Constitution Of Business...",
            "legalNameOfBusiness": "....Name Of Business...",
            "centreJurisdiction": "....Centre Of Jurisdiction...",
            "stateJurisdiction": "....State Of Jurisdiction...",
            "registrationDate": "...Date of Registration...",
            "taxPayerDate": "...Tax Payer Date...",
            "gstinStatus": "..GSTIN Status...",
            "cancellationDate": "..cancellation Date...",
            "natureOfBusinessActivities": [
              "...Nature of Business Activities..."
            ],
            "complianceRating": "...complianceRating...",
            "directorNames": [
              "...directorNames..."
            ],
            "principalPlaceAddress": {
                 "emailId": "..emailId..",
                 "address": "..address..",
                 "natureOfBusiness": "...natureOfBusiness...",
                 "mobile": "...mobile...",
                 "lastUpdatedDate": "",
                 "splitAddress": {
                     "state": [
                       []
                     ],
                     "district": [],
                     "city": [],
                     "pincode": "...pincode...",
                     "country": [
                       "IN",
                       "IND",
                       "INDIA"
                     ],
                     "addressLine": "...addressLine..."
                 }
             },
             "additionalPlaceAddress": [
                 {
                 "emailId": "..emailId..",
                 "address": "..address..",
                 "natureOfBusiness": "...natureOfBusiness...",
                 "mobile": "...mobile...",
                 "lastUpdatedDate": "",
                   "splitAddress": {
                       "state": [
                         []
                       ],
                       "district": [],
                       "city": [],
                       "pincode": "...pincode...",
                       "country": [
                         "IN",
                         "IND",
                         "INDIA"
                       ],
                       "addressLine": "...addressLine..."
                   }
               }],
            "gstin": "...gstin Number..."
        }
    }
  }
```
{% endswagger-response %}
{% endswagger %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/1273d661cf8d0da23469)
