# Search GST details based on PAN No.

### &#xD;Introduction

All GST certificates are registered with the PAN number of the business towards which GST has been issued. Using this PAN Number, the State where the business is located and the email id of the business, the API can search and extract the GST details for future use.ng only on the [GST Portal,](https://cleartax.in/s/cleartax-guide-on-gst-portal) and the government does not issue any physical certificate.&#x20;

**The following information will be extracted :**

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

You will need to login before sending PAN Number request. You are required to pass the access token received from the login call, as authorization header in the PAN to GST request along with other parameters.

### API Input Guidelines

* Provide Correct PAN number registered on GST portal
* State to which PAN is registered for

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for PAN based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required  | String | Access Token                             |
| -------------------- | --------- | ------ | ---------------------------------------- |
| Content-Type         | Required  | String | Application/JSON                         |
| task                 | Required  | String | Type of task - PAN search                |
| essentials.panNumber | Required  | String | PAN number required for GST certificate. |
| essentials.state     | Required  | String | State name in which PAN is registrered   |
| essentials.email     | Required  | String | Required email of Business/ Individuals  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<PATRON ID>/gstns' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "panSearch",
    "essentials": {
        "panNumber": "<PAN Number>",
        "state": "<State>",
        "email": "<E-mail ID>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                                                      |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| task                                            | The type of task to be performed - "PAN Search"                                                                                                                                                                                                                  |
| essentials                                      | This parameter contains the essential data for generating output.                                                                                                                                                                                                |
| essentials.panNumber                            | The PAN number that is required for the GST Search.                                                                                                                                                                                                              |
| essentials.state                                | The state to which the PAN number is registered.                                                                                                                                                                                                                 |
| essentials.email                                | The email ID registered with the owner of the PAN number.                                                                                                                                                                                                        |
| id                                              | The access token that was received during login request.                                                                                                                                                                                                         |
| patronId                                        | This parameter is returned as userId parameter of login request.                                                                                                                                                                                                 |
| result                                          | The final response parameters are displayed here.                                                                                                                                                                                                                |
| result.gstnRecords                              | The detailed information associated with the records of the GST number are contained in this parameter.                                                                                                                                                          |
| gstnRecords.tinNumber                           | The TIN number associated with the GST number is displayed by this parameter.                                                                                                                                                                                    |
| gstnRecords.regType                             | The type of registration done for the GST number being searched is displayed by this parameter.                                                                                                                                                                  |
| gstnRecords.gstinRefId                          | The reference ID associated with the GSTIN is contained in this parameter.                                                                                                                                                                                       |
| gstnRecords.applicationStatus                   | The current status of the application of the GST number.                                                                                                                                                                                                         |
| gstnRecords.registrationName                    | The registration name of the individual/business owner associated with the GST number.                                                                                                                                                                           |
| gstnRecords.mobNum                              | The mobile number of the individual/ business owner associated with the GST number.                                                                                                                                                                              |
| gstnRecords.emailId                             | The email ID of the individual/ business owner associated with the GST number.                                                                                                                                                                                   |
| gstnRecords.gstin                               | The GST identification number for which PAN number is being searched.                                                                                                                                                                                            |
| result.gstnDetailed                             | This parameter provides detailed information about the owner/business to which the GST number has been assigned.                                                                                                                                                 |
| gstnDetailed.constitutionOfBusiness             | This parameter denotes the type of company or organisation i.e Public or Private Limited Company.                                                                                                                                                                |
| gstnDetailed.legalNameOfBusiness                | The legal name of the business as registered with the GST number.                                                                                                                                                                                                |
| gstnDetailed.tradeNameOfBusiness                | The trading/commercial name under which the company/organization operates.                                                                                                                                                                                       |
| gstnDetailed.centreJurisdiction                 | This parameter assigns a code that depicts jurisdiction of the central government on the company.                                                                                                                                                                |
| gstnDetailed.stateJurisdiction                  | This parameter assigns a code that depicts jurisdiction of the state government on the company.                                                                                                                                                                  |
| gstnDetailed.registrationDate                   | The date of registration of GST for the business/organization is displayed by this parameter.                                                                                                                                                                    |
| gstnDetailed.taxPayerDate                       | The due date for the taxpayer associated with the GST number.                                                                                                                                                                                                    |
| gstnDetailed.taxPayerType                       | This parameter denotes the type of taxpayer i.e regular taxpayer.                                                                                                                                                                                                |
| gstnDetailed.gstinStatus                        | The current status of the GST identification number is active/inactive.                                                                                                                                                                                          |
| gstnDetailed.cancellationDate                   | This parameter shows the date of cancellation for the GST if applicable.                                                                                                                                                                                         |
| gstnDetailed.natureOfBusinessActivities         | This parameter shows the type of business provider. Ex: Supplier of Services.                                                                                                                                                                                    |
| gstnDetailed.principalPlaceAddress              | The address of the business/organization as registered with GST number.                                                                                                                                                                                          |
| gstnDetailed.principalPlaceLatitude             | The latitude coordinates of the principal place of address.                                                                                                                                                                                                      |
| gstnDetailed.principalPlaceLongitude            | The longitude coordinates of the principal place of address.                                                                                                                                                                                                     |
| gstnDetailed.principalPlaceBuildingNameFromGST  | The name of the building where the business/organization is located.                                                                                                                                                                                             |
| gstnDetailed.principalPlaceBuildingNoFromGST    | The building number where the business/organization is located.                                                                                                                                                                                                  |
| gstnDetailed.principalPlaceFlatNo               | The flat number in the building where the business/organization is located.                                                                                                                                                                                      |
| gstnDetailed.principalPlaceStreet               | The street name where the business/organization is located.                                                                                                                                                                                                      |
| gstnDetailed.principalPlaceLocality             | The locality where the business/organization is located.                                                                                                                                                                                                         |
| gstnDetailed.principalPlaceCity                 | The city where the business/organization is located.                                                                                                                                                                                                             |
| gstnDetailed.principalPlaceDistrict             | The district where the business/organization is located.                                                                                                                                                                                                         |
| gstnDetailed.principalPlaceState                | The state where the business/organization is located.                                                                                                                                                                                                            |
| gstnDetailed.principalPlacePincode              | The pincode where the business/organization is located.                                                                                                                                                                                                          |
| gstnDetailed.additionalPlaceAddress             | This parameter displays the address for any secondary/branch office associated with the business/organization.                                                                                                                                                   |
| gstnDetailed.additionalPlaceLatitude            | The latitude coordinates of the additional place of address.                                                                                                                                                                                                     |
| gstnDetailed.additionalPlaceLongitude           | The longitude coordinates of the additional place of address.                                                                                                                                                                                                    |
| gstnDetailed.additionalPlaceBuildingNameFromGST | The name of the building where the additional place of the business/organization is located.                                                                                                                                                                     |
| gstnDetailed.additionalPlaceBuildingNoFromGST   | The building number of the additional place of the business/organization is located.                                                                                                                                                                             |
| gstnDetailed.additionalPlaceFlatNo              | The flat number of the building where the additional place of the business/organization is located.                                                                                                                                                              |
| gstnDetailed.additionalPlaceStreet              | The street name of the building where the additional place of the business/organization is located.                                                                                                                                                              |
| gstnDetailed.additionalPlaceLocality            | The locality of the building where the additional place of the business/organization is located.                                                                                                                                                                 |
| gstnDetailed.additionalPlaceCity                | The city where the additional place of the business/organization is located.                                                                                                                                                                                     |
| gstnDetailed.additionalPlaceDistrict            | The district where the additional place of the business/organization is located.                                                                                                                                                                                 |
| gstnDetailed.additionalPlaceState               | The state where the additional place of the business/organization is located.                                                                                                                                                                                    |
| gstnDetailed.additionalPlacePincode             | The pincode where the additional place of the business/organization is located.                                                                                                                                                                                  |
| gstnDetailed.gstin                              | The GST identification number.                                                                                                                                                                                                                                   |
| gstnDetailed.additionalPlaceSplitAddress        | <p>This parameter distinguishes the various parts of the address of the additional place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.</p><p></p> |
| gstnDetailed.principalPlaceSplitAddress         | This parameter distinguishes the various parts of the address of the principal place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD;            |
{% endtab %}

{% tab title="Response" %}
```
{
    "task": "panSearch",
    "essentials": {
        "panNumber": "<PAN NUMBER>",
        "state": "Maharashtra",
        "email": "ankit@signzy.com"
    },
    "id": "<Acc>",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "gstnDetailed": [
            {
                "constitutionOfBusiness": "PRIVATE LIMITED COMPANY",
                "legalNameOfBusiness": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                "tradeNameOfBusiness": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                "centreJurisdiction": "RANGE-IV",
                "stateJurisdiction": "DECCAN-GYMKHANA_501",
                "registrationDate": "01/07/2017",
                "taxPayerDate": "",
                "taxPayerType": "REGULAR",
                "gstinStatus": "ACTIVE",
                "cancellationDate": "",
                "natureOfBusinessActivities": [
                    "SERVICE PROVISION"
                ],
                "principalPlaceAddress": "BANER PASHAN LINK ROAD SOC 131 2 18 B, KUBERA BAHAR BUNGLOWS,PUNE,PUNE,PUNE,MAHARASHTRA,411021",
                "principalPlaceLatitude": "",
                "principalPlaceLongitude": "",
                "principalPlaceBuildingNameFromGST": "SOC 131 2",
                "principalPlaceBuildingNoFromGST": "18 B, KUBERA BAHAR BUNGLOWS",
                "principalPlaceFlatNo": "BANER PASHAN LINK ROAD",
                "principalPlaceStreet": "PUNE",
                "principalPlaceLocality": "PUNE",
                "principalPlaceCity": "",
                "principalPlaceDistrict": "PUNE",
                "principalPlaceState": "MAHARASHTRA",
                "principalPlacePincode": "411021",
                "additionalPlaceAddress": "101, C WING MARATHON INNOVA CORPORATE CENTRE 603 COWORKING,GANAPATRAO KADAM MARG, LOWER PAREL,MUMBAI,MUMBAI CITY,MAHARASHTRA,400013",
                "additionalPlaceLatitude": "",
                "additionalPlaceLongitude": "",
                "additionalPlaceBuildingNameFromGST": "Marathon Innova Corporate Centre",
                "additionalPlaceBuildingNoFromGST": "603 Coworking",
                "additionalPlaceFlatNo": "101, C Wing",
                "additionalPlaceStreet": "Ganapatrao Kadam Marg, Lower Parel",
                "additionalPlaceLocality": "Mumbai",
                "additionalPlaceCity": "",
                "additionalPlaceDistrict": "Mumbai City",
                "additionalPlaceState": "Maharashtra",
                "additionalPlacePincode": "400013",
                "additionalAddressArray": [
                    {
                        "address": "101, C WING 603 COWORKING,GANAPATRAO KADAM MARG, LOWER PAREL,MUMBAI,MAHARASHTRA,400013",
                        "flatNo": "101, C Wing",
                        "street": "D.K. Sandhu Marg",
                        "locality": "Mumbai",
                        "buildingNo": "603 Coworking",
                        "buildingName": "Marathon Innova Corporate Centre",
                        "district": "Mumbai City",
                        "city": "",
                        "state": "Maharashtra",
                        "pincode": "400013",
                        "latitude": "",
                        "longitude": ""
                    }
                ],
                "lastUpdatedDate": "26/10/2021",
                "principalPlaceSplitAddress": {
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
                    "addressLine": "BANER PASHAN LINK ROAD SOC 131 2 18 B,KUBERA BAHAR BUNGLOWS PUNE,MAHARASHTRA"
                },
                "additionalPlaceSplitAddress": {
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
                    "pincode": "400013",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "101,C WING MARATHON INNOVA CORPORATE CENTRE 603 COWORKING,GANAPATRAO KADAM MARG,LOWER PAREL MAHARASHTRA"
                }
            }
        ],
        "gstnRecords": [
            {
                "applicationStatus": "",
                "registrationName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
                "mobNum": "",
                "regType": "",
                "emailId": "",
                "tinNumber": "",
                "gstinRefId": "",
                "gstin": "27AAWCS3552Q1ZA"
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





{% swagger baseUrl="https://production.signzy.tech" path="/api/v2/patrons/...patronID.../gstns" method="post" summary=" GST Search Using PAN" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../gstns`

\




\


This method is used to extract the details of GST certificates using PAN
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - PAN Search
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.panNumber" type="string" %}
PAN number required for the GST certificate
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.state" type="string" %}
Registered State of the PAN.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.email" type="string" %}
Registered Email of the business/individual
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "task": "panSearch",
  "essentials": {
    "panNumber": "..panNumber..",
    "state": "..state..",
    "email": "..email.."
  },
  "id": "...accessToken...",
  "patronId": "...patronId...",
  "result": {
    "gstnRecords": [
      {
        "tinNumber": "...tinNumber...",
        "regType": "...regType...",
        "gstinRefId": "...gstinRefId...",
        "applicationStatus": "...applicationStatus...",
        "registrationName": "...registrationName...",
        "mobNum": "...mobNum...",
        "emailId": "...emailId...",
        "gstin": "...gstin...",
      }
    ],
    "gstnDetailed": [
      [
        {
          "constitutionOfBusiness": "...constitutionOfBusiness...",
          "legalNameOfBusiness": "...legalNameOfBusiness...",
          "tradeNameOfBusiness": "...tradeNameOfBusiness...",
          "centreJurisdiction": "...centreJurisdiction...",
          "stateJurisdiction": "...stateJurisdiction...",
          "registrationDate": "...registrationDate...",
          "taxPayerDate": "...taxPayerDate...",
          "taxPayerType": "...taxPayerType...",
          "gstinStatus": "...gstinStatus...",
          "cancellationDate": "...cancellationDate...",
          "natureOfBusinessActivities": [],
          "principalPlaceAddress": "...principalPlaceAddress...",
          "principalPlaceLatitude": "...principalPlaceLatitude...",
          "principalPlaceLongitude": "...principalPlaceLongitude...",
          "principalPlaceBuildingNameFromGST": "...principalPlaceBuildingNameFromGST...",
          "principalPlaceBuildingNoFromGST": "...principalPlaceBuildingNoFromGST...",
          "principalPlaceFlatNo": "...principalPlaceFlatNo...",
          "principalPlaceStreet": "...principalPlaceStreet...",
          "principalPlaceLocality": "...principalPlaceLocality...",
          "principalPlaceCity": "...principalPlaceCity...",
          "principalPlaceDistrict": "...principalPlaceDistrict...",
          "principalPlaceState": "...principalPlaceState...",
          "principalPlacePincode": "...principalPlacePincode...",
          "additionalPlaceAddress": "...additionalPlaceAddress...",
          "additionalPlaceLatitude": "...additionalPlaceLatitude...",
          "additionalPlaceLongitude": "...additionalPlaceLongitude...",
          "additionalPlaceBuildingNameFromGST": "...additionalPlaceBuildingNameFromGST...",
          "additionalPlaceBuildingNoFromGST": "...additionalPlaceBuildingNoFromGST...",
          "additionalPlaceFlatNo": "...additionalPlaceFlatNo...",
          "additionalPlaceStreet": "...additionalPlaceStreet...",
          "additionalPlaceLocality": "...additionalPlaceLocality...",
          "additionalPlaceCity": "...additionalPlaceCity...",
          "additionalPlaceDistrict": "...additionalPlaceDistrict...",
          "additionalPlaceState": "...additionalPlaceState...",
          "additionalPlacePincode": "...additionalPlacePincode...",
          "gstin": "...gstin...",
          "rawOutput": {
            "stjCd": "...stjCd...",
            "stj": "...stj...",
            "lgnm": "...lgnm...",
            "dty": "...dty...",
            "adadr": [],
            "cxdt": "...cxdt...",
            "gstin": "...gstin...",
            "nba": [
              "Supplier of Services"
            ],
            "lstupdt": "...lstupdt...",
            "rgdt": "...rgdt...",
            "ctb": "...ctb...",
            "pradr": {
              "addr": {
                "bnm": "...bnm...",
                "loc": "...loc...",
                "st": "...st...",
                "bno": "...bno...",
                "stcd": "...stcd...",
                "dst": "...dst...",
                "city": "...city...",
                "flno": "...flno...",
                "lt": "...lt...",
                "pncd": "...pncd...",
                "lg": "...lg...",
              },
              "ntr": "...ntr...",
            },
            "tradeNam": "...tradeNam...",
            "sts": "...sts...",
            "ctjCd": "...ctjCd...",
            "ctj": "...ctj...",
          },
          "additionalPlaceSplitAddress": {
            "district": [],
            "state": [
              []
            ],
            "city": [],
            "pincode": "...pincode...",
            "country": [],
            "addressLine": "...addressLine...",
          },
          "principalPlaceSplitAddress": {
              "district": [],
              "state": [
                []
              ],
              "city": [],
              "pincode": "...pincode...",
              "country": [
                "IN",
                "IND",
                "INDIA"
              ],
              "addressLine": "...addressLine...",
            }
          }
        ]
      ]
    }
  }
```
{% endswagger-response %}
{% endswagger %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/94d5f70ae3f8d2edabed)

**Valid State and Union Territory List**

1 ) ANDAMAN AND NICOBAR ISLANDS\
2 ) ANDHRA PRADESH\
3 ) ANDHRA PRADESH (NEW)\
4 ) ARUNACHAL PRADESH\
5 ) ASSAM\
6 ) BIHAR\
7 ) CHANDIGARH\
8 ) CHATTISGARH\
9 ) DADRA AND NAGAR HAVELI\
10 ) DAMAN AND DIU\
11 ) DELHI\
12 ) GOA\
13 ) GUJARAT\
14 ) HARYANA\
15 ) HIMACHAL PRADESH\
16 ) JAMMU AND KASHMIR\
17 ) JHARKHAND\
18 ) KARNATAKA\
19 ) KERALA\
20 ) LAKSHADWEEP ISLANDS\
21 ) MADHYA PRADESH\
22 ) MAHARASHTRA\
23 ) MANIPUR\
24 ) MEGHALAYA\
25 ) MIZORAM\
26 ) NAGALAND\
27 ) ODISHA\
28 ) PONDICHERRY\
29 ) PUNJAB\
30 ) RAJASTHAN\
31 ) SIKKIM\
32 ) TAMIL NADU\
33 ) TELANGANA\
34 ) TRIPURA\
35 ) UTTAR PRADESH
