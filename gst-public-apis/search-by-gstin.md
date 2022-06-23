# Search by GSTIN

### Introduction

Every GST Certificate holds a unique 15-digit alphanumeric GST Identification Number or GSTIN for the business. This is just like the ID number on any other ID card. Using the GSTIN Based Search API, Signzy uses its proprietary algorithms to extract the details of the GSTIN-registered business and its owner.

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

You will need to login before sending PAN Number request. You are required to pass the access token received from the login call, as authorization header in the GSTIN request along with GSTIN Number

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for VAT based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization    | Required | String | Access Token                      |
| ---------------- | -------- | ------ | --------------------------------- |
| Content-Type     | Required | String | Application/JSON                  |
| task             | Required | String | Type of task - GSTIN BASIC SEARCH |
| essentials.gstin | Required | String | GSTIN number to be searched       |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/gstns' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "<TASK>",
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
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                                       |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| task                                            | The type of task to be performed - "GSTIN Search"                                                                                                                                                                                                 |
| essentials                                      | This parameter contains the essential data for generating output.                                                                                                                                                                                 |
| essentials.panNumber                            | The GST number that is required for the GST Search.                                                                                                                                                                                               |
| essentials.state                                | The state to which the GST number is registered.                                                                                                                                                                                                  |
| essentials.email                                | The email ID registered with the owner of the GST number.                                                                                                                                                                                         |
| id                                              | The access token that was received during login request.                                                                                                                                                                                          |
| patronId                                        | This parameter is returned as userId parameter of login request.                                                                                                                                                                                  |
| result                                          | The final response parameters are displayed here.                                                                                                                                                                                                 |
| result.gstnRecords                              | The detailed information associated with the records of the GST number are contained in this parameter.                                                                                                                                           |
| gstnRecords.tinNumber                           | The TIN number associated with the GST number is displayed by this parameter.                                                                                                                                                                     |
| gstnRecords.regType                             | The type of registration done for the GST number being searched is displayed by this parameter.                                                                                                                                                   |
| gstnRecords.gstinRefId                          | The reference ID associated with the GSTIN is contained in this parameter.                                                                                                                                                                        |
| gstnRecords.applicationStatus                   | The current status of the application of the GST number.                                                                                                                                                                                          |
| gstnRecords.registrationName                    | The registration name of the individual/business owner associated with the GST number.                                                                                                                                                            |
| gstnRecords.mobNum                              | The mobile number of the individual/ business owner associated with the GST number.                                                                                                                                                               |
| gstnRecords.emailId                             | The email ID of the individual/ business owner associated with the GST number.                                                                                                                                                                    |
| gstnRecords.gstin                               | The GST identification number for which PAN number is being searched.                                                                                                                                                                             |
| result.gstnDetailed                             | This parameter provides detailed information about the owner/business to which the GST number has been assigned.                                                                                                                                  |
| gstnDetailed.constitutionOfBusiness             | This parameter denotes the type of company or organisation i.e Public or Private Limited Company.                                                                                                                                                 |
| gstnDetailed.legalNameOfBusiness                | The legal name of the business as registered with the GST number.                                                                                                                                                                                 |
| gstnDetailed.tradeNameOfBusiness                | The trading/commercial name under which the company/organization operates.                                                                                                                                                                        |
| gstnDetailed.centreJurisdiction                 | This parameter assigns a code that depicts jurisdiction of the central government on the company.                                                                                                                                                 |
| gstnDetailed.stateJurisdiction                  | This parameter assigns a code that depicts jurisdiction of the state government on the company.                                                                                                                                                   |
| gstnDetailed.registrationDate                   | The date of registration of GST for the business/organization is displayed by this parameter.                                                                                                                                                     |
| gstnDetailed.taxPayerDate                       | The due date for the taxpayer associated with the GST number.                                                                                                                                                                                     |
| gstnDetailed.taxPayerType                       | This parameter denotes the type of taxpayer i.e regular taxpayer.                                                                                                                                                                                 |
| gstnDetailed.gstinStatus                        | The current status of the GST identification number is active/inactive.                                                                                                                                                                           |
| gstnDetailed.cancellationDate                   | This parameter shows the date of cancellation for the GST if applicable.                                                                                                                                                                          |
| gstnDetailed.natureOfBusinessActivities         | This parameter shows the type of business provider. Ex: Supplier of Services.                                                                                                                                                                     |
| gstnDetailed.principalPlaceAddress              | The address of the business/organization as registered with GST number.                                                                                                                                                                           |
| gstnDetailed.principalPlaceLatitude             | The latitude coordinates of the principal place of address.                                                                                                                                                                                       |
| gstnDetailed.principalPlaceLongitude            | The longitude coordinates of the principal place of address.                                                                                                                                                                                      |
| gstnDetailed.principalPlaceBuildingNameFromGST  | The name of the building where the business/organization is located.                                                                                                                                                                              |
| gstnDetailed.principalPlaceBuildingNoFromGST    | The building number where the business/organization is located.                                                                                                                                                                                   |
| gstnDetailed.principalPlaceFlatNo               | The flat number in the building where the business/organization is located.                                                                                                                                                                       |
| gstnDetailed.principalPlaceStreet               | The street name where the business/organization is located.                                                                                                                                                                                       |
| gstnDetailed.principalPlaceLocality             | The locality where the business/organization is located.                                                                                                                                                                                          |
| gstnDetailed.principalPlaceCity                 | The city where the business/organization is located.                                                                                                                                                                                              |
| gstnDetailed.principalPlaceDistrict             | The district where the business/organization is located.                                                                                                                                                                                          |
| gstnDetailed.principalPlaceState                | The state where the business/organization is located.                                                                                                                                                                                             |
| gstnDetailed.principalPlacePincode              | The pincode where the business/organization is located.                                                                                                                                                                                           |
| gstnDetailed.additionalPlaceAddress             | This parameter displays the address for any secondary/branch office associated with the business/organization.                                                                                                                                    |
| gstnDetailed.additionalPlaceLatitude            | The latitude coordinates of the additional place of address.                                                                                                                                                                                      |
| gstnDetailed.additionalPlaceLongitude           | The longitude coordinates of the additional place of address.                                                                                                                                                                                     |
| gstnDetailed.additionalPlaceBuildingNameFromGST | The name of the building where the additional place of the business/organization is located.                                                                                                                                                      |
| gstnDetailed.additionalPlaceBuildingNoFromGST   | The building number of the additional place of the business/organization is located.                                                                                                                                                              |
| gstnDetailed.additionalPlaceFlatNo              | The flat number of the building where the additional place of the business/organization is located.                                                                                                                                               |
| gstnDetailed.additionalPlaceStreet              | The street name of the building where the additional place of the business/organization is located.                                                                                                                                               |
| gstnDetailed.additionalPlaceLocality            | The locality of the building where the additional place of the business/organization is located.                                                                                                                                                  |
| gstnDetailed.additionalPlaceCity                | The city where the additional place of the business/organization is located.                                                                                                                                                                      |
| gstnDetailed.additionalPlaceDistrict            | The district where the additional place of the business/organization is located.                                                                                                                                                                  |
| gstnDetailed.additionalPlaceState               | The state where the additional place of the business/organization is located.                                                                                                                                                                     |
| gstnDetailed.additionalPlacePincode             | The pincode where the additional place of the business/organization is located.                                                                                                                                                                   |
| gstnDetailed.gstin                              | The GST identification number.                                                                                                                                                                                                                    |
| gstnDetailed.principalPlaceSplitAddress         | This parameter distinguishes the various parts of the address of the principal place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
| gstnDetailed.additionalPlaceSplitAddress        | This parameter distinguishes the various parts of the address of the additional place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
{% endtab %}

{% tab title="Response" %}
```
{
    "task": "<Type of task to be performed>",
    "essentials": {
        "gstin": "<GSTIN Number>"
    },
    "id": "<Access token from login request>",
    "patronId": "<Patron ID>",
    "result": {
        "gstnDetailed": {
            "constitutionOfBusiness": "PROPRIETORSHIP",
            "legalNameOfBusiness": "SAGAR MAHESHKUMAR PATEL",
            "tradeNameOfBusiness": "ASHISH ENGINEERING WORKS",
            "centreJurisdiction": "RANGE-I",
            "stateJurisdiction": "MALAD-WEST_704",
            "registrationDate": "01/07/2017",
            "taxPayerDate": "",
            "taxPayerType": "REGULAR",
            "gstinStatus": "ACTIVE",
            "cancellationDate": "",
            "natureOfBusinessActivities": [
                "OFFICE / SALE OFFICE"
            ],
            "principalPlaceAddress": "11TH RUSTOMJEE RIVIERA BLDG., A-1102,MARVE ROAD,MALAD WEST,MUMBAI SUBURBAN,MAHARASHTRA,400064",
            "principalPlaceLatitude": "",
            "principalPlaceLongitude": "",
            "principalPlaceBuildingNameFromGST": "RUSTOMJEE RIVIERA BLDG.,",
            "principalPlaceBuildingNoFromGST": "A-1102",
            "principalPlaceFlatNo": "11TH",
            "principalPlaceStreet": "MARVE ROAD",
            "principalPlaceLocality": "MALAD WEST",
            "principalPlaceCity": "",
            "principalPlaceDistrict": "MUMBAI SUBURBAN",
            "principalPlaceState": "MAHARASHTRA",
            "principalPlacePincode": "400064",
            "additionalPlaceAddress": "BOMBAY TALKIES COMPOUND 179,OPP. SHED NO. 35,MALAD WEST,MUMBAI SUBURBAN,MAHARASHTRA,400064",
            "additionalPlaceLatitude": "",
            "additionalPlaceLongitude": "",
            "additionalPlaceBuildingNameFromGST": "Bombay Talkies Compound",
            "additionalPlaceBuildingNoFromGST": "179",
            "additionalPlaceFlatNo": "",
            "additionalPlaceStreet": "Opp. Shed No. 35",
            "additionalPlaceLocality": "Malad West",
            "additionalPlaceCity": "",
            "additionalPlaceDistrict": "Mumbai Suburban",
            "additionalPlaceState": "Maharashtra",
            "additionalPlacePincode": "400064",
            "additionalAddressArray": [
                {
                    "address": "179,OPP. SHED NO. 35,MALAD WEST,MAHARASHTRA,400064",
                    "flatNo": "",
                    "street": "D.K. Sandhu Marg",
                    "locality": "Malad West",
                    "buildingNo": "179",
                    "buildingName": "Bombay Talkies Compound",
                    "district": "Mumbai Suburban",
                    "city": "",
                    "state": "Maharashtra",
                    "pincode": "400064",
                    "latitude": "",
                    "longitude": ""
                }
            ],
            "lastUpdatedDate": "07/09/2019",
            "principalPlaceSplitAddress": {
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
                "addressLine": "11TH RUSTOMJEE RIVIERA BLDG.A-1102,MARVE ROAD,MALAD WEST,SUBURBAN,MAHARASHTRA"
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
                "pincode": "400064",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "BOMBAY TALKIES COMPOUND 179,OPP.SHED NO.35,MALAD WEST,SUBURBAN,MAHARASHTRA"
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
        "gstin": "27AOKPP9482P1ZQ"
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
GSTIN for which the details are required
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
  	"result": {
  		"gstnRecords": [{
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
            "tradeNameOfBusiness": "....Trade Name Of Business...",
  			"centreJurisdiction": "....Centre Of Jurisdiction...",
  			"stateJurisdiction": "....State Of Jurisdiction...",
  			"registrationDate": "...Date of Registration...",
  			"taxPayerDate": "...Tax Payer Date...",
            "taxPayerType": "...Tax Payer Type...",
            "gstinStatus": "..GSTIN Status...",
  			"cancellationDate": "..cancellation Date...",
  			"natureOfBusinessActivities": [
  				"...Nature of Business Activities..."
  			],
  			"principalPlaceAddress": "...Principal Address of the entity registered in GST...",
            "principalPlaceLatitude": "...Principal Latitude of the entity registered in GST...",
            "principalPlaceLongitude": "...Principal Longitude of the entity registered in GST...",
            "principalPlaceBuildingNameFromGST": "...Bulding Name of Principal Address of the entity registered in GST...",
  			"principalPlaceBuildingNoFromGST": "...Bulding No of Principal Address of the entity registered in GST...",
  			"principalPlaceFlatNo": "...Flat No of Principal Address of the entity registered in GST...",
            "principalPlaceStreet": "...Street of Principal Address of the entity registered in GST...",
            "principalPlaceLocality": "...Locality of Principal Address of the entity registered in GST...",
            "principalPlaceCity":"...City of Principal Address of the entity registered in GST...",
            "principalPlaceDistrict":"...District of Principal Address of the entity registered in GST...",
            "principalPlaceState":"...State of Principal Address of the entity registered in GST...",
            "principalPlacePincode":"...Pincode of Principal Address of the entity registered in GST...",
  			"additionalPlaceAddress": "...Additional Address of the entity registered in GST...",
            "additionalPlaceLatitude": "...Additional Latitude of the entity registered in GST...",
            "additionalPlaceLongitude": "...Additional Longitude of the entity registered in GST...",
            "additionalPlaceBuildingNameFromGST": "...Bulding Name of Additional Address of the entity registered in GST...",
            "additionalPlaceBuildingNoFromGST": "...Bulding No of Additional Address of the entity registered in GST...",
  			"additionalPlaceFlatNo": "...Flat No of Additional Address of the entity registered in GST...",
            "additionalPlaceStreet": "...Street of Additional Address of the entity registered in GST...",
            "additionalPlaceLocality": "...Locality of Additional Address of the entity registered in GST...",
            "additionalPlaceCity":"...City of Additional Address of the entity registered in GST...",
            "additionalPlaceDistrict":"...District of Additional Address of the entity registered in GST...",
            "additionalPlaceState":"...State of Additional Address of the entity registered in GST...",
            "additionalPlacePincode":"...Pincode of Additional Address of the entity registered in GST...",
  			"principalPlaceSplitAddress": {
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
  			},
  			"additionalPlaceSplitAddress": {
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
  		"gstin": "...gstin Number..."
  	}
  }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "task" : "gstinSearch",
    "essentials": {
      "gstin": "..gstin.."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                                       |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| task                                            | The type of task to be performed - "GSTIN Search"                                                                                                                                                                                                 |
| essentials                                      | This parameter contains the essential data for generating output.                                                                                                                                                                                 |
| essentials.panNumber                            | The GST number that is required for the GST Search.                                                                                                                                                                                               |
| essentials.state                                | The state to which the GST number is registered.                                                                                                                                                                                                  |
| essentials.email                                | The email ID registered with the owner of the GST number.                                                                                                                                                                                         |
| id                                              | The access token that was received during login request.                                                                                                                                                                                          |
| patronId                                        | This parameter is returned as userId parameter of login request.                                                                                                                                                                                  |
| result                                          | The final response parameters are displayed here.                                                                                                                                                                                                 |
| result.gstnRecords                              | The detailed information associated with the records of the GST number are contained in this parameter.                                                                                                                                           |
| gstnRecords.tinNumber                           | The TIN number associated with the GST number is displayed by this parameter.                                                                                                                                                                     |
| gstnRecords.regType                             | The type of registration done for the GST number being searched is displayed by this parameter.                                                                                                                                                   |
| gstnRecords.gstinRefId                          | The reference ID associated with the GSTIN is contained in this parameter.                                                                                                                                                                        |
| gstnRecords.applicationStatus                   | The current status of the application of the GST number.                                                                                                                                                                                          |
| gstnRecords.registrationName                    | The registration name of the individual/business owner associated with the GST number.                                                                                                                                                            |
| gstnRecords.mobNum                              | The mobile number of the individual/ business owner associated with the GST number.                                                                                                                                                               |
| gstnRecords.emailId                             | The email ID of the individual/ business owner associated with the GST number.                                                                                                                                                                    |
| gstnRecords.gstin                               | The GST identification number for which PAN number is being searched.                                                                                                                                                                             |
| result.gstnDetailed                             | This parameter provides detailed information about the owner/business to which the GST number has been assigned.                                                                                                                                  |
| gstnDetailed.constitutionOfBusiness             | This parameter denotes the type of company or organisation i.e Public or Private Limited Company.                                                                                                                                                 |
| gstnDetailed.legalNameOfBusiness                | The legal name of the business as registered with the GST number.                                                                                                                                                                                 |
| gstnDetailed.tradeNameOfBusiness                | The trading/commercial name under which the company/organization operates.                                                                                                                                                                        |
| gstnDetailed.centreJurisdiction                 | This parameter assigns a code that depicts jurisdiction of the central government on the company.                                                                                                                                                 |
| gstnDetailed.stateJurisdiction                  | This parameter assigns a code that depicts jurisdiction of the state government on the company.                                                                                                                                                   |
| gstnDetailed.registrationDate                   | The date of registration of GST for the business/organization is displayed by this parameter.                                                                                                                                                     |
| gstnDetailed.taxPayerDate                       | The due date for the taxpayer associated with the GST number.                                                                                                                                                                                     |
| gstnDetailed.taxPayerType                       | This parameter denotes the type of taxpayer i.e regular taxpayer.                                                                                                                                                                                 |
| gstnDetailed.gstinStatus                        | The current status of the GST identification number is active/inactive.                                                                                                                                                                           |
| gstnDetailed.cancellationDate                   | This parameter shows the date of cancellation for the GST if applicable.                                                                                                                                                                          |
| gstnDetailed.natureOfBusinessActivities         | This parameter shows the type of business provider. Ex: Supplier of Services.                                                                                                                                                                     |
| gstnDetailed.principalPlaceAddress              | The address of the business/organization as registered with GST number.                                                                                                                                                                           |
| gstnDetailed.principalPlaceLatitude             | The latitude coordinates of the principal place of address.                                                                                                                                                                                       |
| gstnDetailed.principalPlaceLongitude            | The longitude coordinates of the principal place of address.                                                                                                                                                                                      |
| gstnDetailed.principalPlaceBuildingNameFromGST  | The name of the building where the business/organization is located.                                                                                                                                                                              |
| gstnDetailed.principalPlaceBuildingNoFromGST    | The building number where the business/organization is located.                                                                                                                                                                                   |
| gstnDetailed.principalPlaceFlatNo               | The flat number in the building where the business/organization is located.                                                                                                                                                                       |
| gstnDetailed.principalPlaceStreet               | The street name where the business/organization is located.                                                                                                                                                                                       |
| gstnDetailed.principalPlaceLocality             | The locality where the business/organization is located.                                                                                                                                                                                          |
| gstnDetailed.principalPlaceCity                 | The city where the business/organization is located.                                                                                                                                                                                              |
| gstnDetailed.principalPlaceDistrict             | The district where the business/organization is located.                                                                                                                                                                                          |
| gstnDetailed.principalPlaceState                | The state where the business/organization is located.                                                                                                                                                                                             |
| gstnDetailed.principalPlacePincode              | The pincode where the business/organization is located.                                                                                                                                                                                           |
| gstnDetailed.additionalPlaceAddress             | This parameter displays the address for any secondary/branch office associated with the business/organization.                                                                                                                                    |
| gstnDetailed.additionalPlaceLatitude            | The latitude coordinates of the additional place of address.                                                                                                                                                                                      |
| gstnDetailed.additionalPlaceLongitude           | The longitude coordinates of the additional place of address.                                                                                                                                                                                     |
| gstnDetailed.additionalPlaceBuildingNameFromGST | The name of the building where the additional place of the business/organization is located.                                                                                                                                                      |
| gstnDetailed.additionalPlaceBuildingNoFromGST   | The building number of the additional place of the business/organization is located.                                                                                                                                                              |
| gstnDetailed.additionalPlaceFlatNo              | The flat number of the building where the additional place of the business/organization is located.                                                                                                                                               |
| gstnDetailed.additionalPlaceStreet              | The street name of the building where the additional place of the business/organization is located.                                                                                                                                               |
| gstnDetailed.additionalPlaceLocality            | The locality of the building where the additional place of the business/organization is located.                                                                                                                                                  |
| gstnDetailed.additionalPlaceCity                | The city where the additional place of the business/organization is located.                                                                                                                                                                      |
| gstnDetailed.additionalPlaceDistrict            | The district where the additional place of the business/organization is located.                                                                                                                                                                  |
| gstnDetailed.additionalPlaceState               | The state where the additional place of the business/organization is located.                                                                                                                                                                     |
| gstnDetailed.additionalPlacePincode             | The pincode where the additional place of the business/organization is located.                                                                                                                                                                   |
| gstnDetailed.gstin                              | The GST identification number.                                                                                                                                                                                                                    |
| gstnDetailed.principalPlaceSplitAddress         | This parameter distinguishes the various parts of the address of the principal place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
| gstnDetailed.additionalPlaceSplitAddress        | This parameter distinguishes the various parts of the address of the additional place of business into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/047ecfe8e4663b71995e)
