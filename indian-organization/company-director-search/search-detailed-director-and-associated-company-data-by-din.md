# Search Detailed Director & Associated Company data by DIN

### &#xD;Introduction

DIN **(Director Identification Number)** is an 8**-digit unique identification number**, allotted by the Ministry of Corporate Affairs(MCA) to any person intending to be a Director or an existing director of a company.&#x20;

### API Usecase

This API behaves in a similar yet opposite role to the ROC Detailed Search API wherein it displays the organisational history of the director along with the details of the other director members employed at the organisation. This provides a much thorough output by taking the DIN as input.

**Director's information**

The API returns the following data about the director

* Din
* Name
* Designation
* Address
* Number of companies
* List of companies
* List of LLP's



**Company's information**

The API returns the following data about the company

* Company name
* ROC office
* Registration number
* Category
* Sub category
* Class
* Authorised capital
* Paid-up capital
* Number of members
* Date of incorporation
* Registered address
* Email-ID
* Whether Listed
* Last AGM date
* Balance sheet date
* Status for e-filing
* Address other than registered address
* Suspended at stock exchange
* CIN
* Director details



### How to call the API

Before going for ROC Director Quick search for organizations, you first need to create an '_Organization_' **object** and you need to pass the CIN as i**dentifier** in the request body.



### API Input Guidelines

Provide correct **8-digit unique identification number**, Provided by MCA to the director for whom information needs to be extracted.



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
    "accessToken": "dz187wk6navzyk7et66mdqrmnc7ml2dl",
    "id": "616832a418d6ad764a315622",
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
        "din": "05255419"
    }
}'

```
{% endtab %}
{% endtabs %}

Response

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                                                   |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| din                      | The director identification number of the company.                                                                                                                                                                            |
| designation              | The exact designation of the director in the company.                                                                                                                                                                         |
| address                  | The registered address of the director.                                                                                                                                                                                       |
| name                     | The name of the director.                                                                                                                                                                                                     |
| dob                      | The date of birth of the director.                                                                                                                                                                                            |
| noOfCompanies            | The number of companies that the director has been a part of.                                                                                                                                                                 |
| splitAddress             | This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine | The first line of the director address is shown by this parameter.                                                                                                                                                            |

| listOfCompanies                                                       | The list of companies to which the director belongs to/was previously employed.                                                                                                                                               |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| listOfCompanies.rocOffice                                             | The office name of the Registrar Of Companies to which the company being searched belongs to.                                                                                                                                 |
| listOfCompanies.registrationNumber                                    | The registration number of the company.                                                                                                                                                                                       |
| <p></p><p></p><p>listOfCompanies.category</p>                         | The type of category the company belongs to.                                                                                                                                                                                  |
| <p></p><p></p><p>listOfCompanies.subCategory</p>                      | The sub category to which the company belongs to.                                                                                                                                                                             |
| <p></p><p></p><p>listOfCompanies.class</p>                            | The class to which the company belongs.                                                                                                                                                                                       |
| <p></p><p></p><p>listOfCompanies.authorisedCapital</p>                | The amount of capital authorised to the company.                                                                                                                                                                              |
| <p></p><p></p><p>listOfCompanies.paidUpCapital</p>                    | The amount of paid up capital for the company being searched.                                                                                                                                                                 |
| <p></p><p></p><p>listOfCompanies.numberOfMembers</p>                  | The number of members associated with the company.                                                                                                                                                                            |
| <p></p><p></p><p>listOfCompanies.dateOfIncorporation</p>              | The date of incorporation of the company as registered with the CIN.                                                                                                                                                          |
| <p></p><p></p><p>listOfCompanies.registeredAddress</p>                | The registered address of the company.                                                                                                                                                                                        |
| <p></p><p></p><p>listOfCompanies.pan</p>                              | The PAN number of the company.                                                                                                                                                                                                |
| <p></p><p></p><p>listOfCompanies.emailId</p>                          | The registered email ID of the company.                                                                                                                                                                                       |
| <p></p><p></p><p>listOfCompanies.whetherListed</p>                    | This parameter shows whether the company is listed with the Registrar Of Companies.                                                                                                                                           |
| <p></p><p></p><p>listOfCompanies.lastAgmDate</p>                      | The date of the last annual general meeting.                                                                                                                                                                                  |
| <p></p><p></p><p>listOfCompanies.balanceSheetDate</p>                 | The available date on the balance sheet of the company.                                                                                                                                                                       |
| <p></p><p></p><p>listOfCompanies.statusForEfiling</p>                 | The current status of E-filing for the company.                                                                                                                                                                               |
| <p></p><p></p><p>listOfCompanies.addressOtherThanRegisteredOffice</p> | The address other than the registered office address of the company, if any.                                                                                                                                                  |
| <p></p><p></p><p>listOfCompanies.suspendedAtStockExchange</p>         | This parameter shows whether the company has been suspended at stock exchange.                                                                                                                                                |
| <p></p><p></p><p>listOfCompanies.natureOfBusiness</p>                 | The nature of business conducted by the company. For ex: Supplier of Services.                                                                                                                                                |
| <p></p><p></p><p>listOfCompanies.splitAddress</p>                     | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
| splitAddress.addressLine                                              | The first line of the company address is shown by this parameter.                                                                                                                                                             |
| cin                                                                   | The unique company identification number.                                                                                                                                                                                     |
| directorDetails                                                       | This parameter displays the details of the company director(s).                                                                                                                                                               |
| directorDetails.name                                                  | The name of the director.                                                                                                                                                                                                     |
| directorDetails.fatherName                                            | The father name of the director.                                                                                                                                                                                              |
| directorDetails.dob                                                   | The date of birth of the director.                                                                                                                                                                                            |
| directorDetails.pan                                                   | The PAN number of the company director.                                                                                                                                                                                       |
| directorDetails.din                                                   | The director identification number of the company.                                                                                                                                                                            |
| directorDetails.dscExpiryDate                                         | The date of expiry for the digital certificates of the director.                                                                                                                                                              |
| directorDetails.dateOfAppointment                                     | The date of appointment of the director to the company.                                                                                                                                                                       |
| directorDetails.designation                                           | The exact designation of the director in the company.                                                                                                                                                                         |
| directorDetails.address                                               | The registered address of the director.                                                                                                                                                                                       |
| directorDetails.splitAddress                                          | This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine                                              | The first line of the director address is shown by this parameter.                                                                                                                                                            |
| whetherDscRegistered                                                  | This parameter shows whether the digital certificates are registered and valid.                                                                                                                                               |

| listOfLLPs                                  | The list of LLP's to which the director was a member.                                                                                                                                                                         |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| listOfLLPs.rocOffice                        | The office name of the Registrar Of Companies to which the company being searched belongs to.                                                                                                                                 |
| listOfLLPs.registrationNumber               | The registration number of the company.                                                                                                                                                                                       |
| listOfLLPs.category                         | The type of category the company belongs to.                                                                                                                                                                                  |
| listOfLLPs.subCategory                      | The sub category to which the company belongs to.                                                                                                                                                                             |
| listOfLLPs.class                            | The class to which the company belongs.                                                                                                                                                                                       |
| listOfLLPs.authorisedCapital                | The amount of capital authorised to the company.                                                                                                                                                                              |
| listOfLLPs.paidUpCapital                    | The amount of paid up capital for the company being searched.                                                                                                                                                                 |
| listOfLLPs.numberOfMembers                  | The number of members associated with the company.                                                                                                                                                                            |
| listOfLLPs.dateOfIncorporation              | The date of incorporation of the company as registered with the CIN.                                                                                                                                                          |
| listOfLLPs.registeredAddress                | The registered address of the company.                                                                                                                                                                                        |
| listOfLLPs.pan                              | The PAN number of the company.                                                                                                                                                                                                |
| listOfLLPs.emailId                          | The registered email ID of the company.                                                                                                                                                                                       |
| listOfLLPs.whetherListed                    | This parameter shows whether the company is listed with the Registrar Of Companies.                                                                                                                                           |
| listOfLLPs.lastAgmDate                      | The date of the last annual general meeting.                                                                                                                                                                                  |
| listOfLLPs.balanceSheetDate                 | The available date on the balance sheet of the company.                                                                                                                                                                       |
| listOfLLPs.statusForEfiling                 | The current status of E-filing for the company.                                                                                                                                                                               |
| listOfLLPs.addressOtherThanRegisteredOffice | The address other than the registered office address of the company, if any.                                                                                                                                                  |
| listOfLLPs.suspendedAtStockExchange         | This parameter shows whether the company has been suspended at stock exchange.                                                                                                                                                |
| listOfLLPs.natureOfBusiness                 | The nature of business conducted by the company. For ex: Supplier of Services.                                                                                                                                                |
| listOfLLPs.splitAddress                     | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
| splitAddress.addressLine                    | The first line of the company address is shown by this parameter.                                                                                                                                                             |
| cin                                         | The unique company identification number.                                                                                                                                                                                     |
| directorDetails                             | This parameter displays the details of the company director(s).                                                                                                                                                               |
| directorDetails.name                        | The name of the director.                                                                                                                                                                                                     |
| directorDetails.fatherName                  | The father name of the director.                                                                                                                                                                                              |
| directorDetails.dob                         | The date of birth of the director.                                                                                                                                                                                            |
| directorDetails.pan                         | The PAN number of the company director.                                                                                                                                                                                       |
| directorDetails.din                         | The director identification number of the company.                                                                                                                                                                            |
| directorDetails.dscExpiryDate               | The date of expiry for the digital certificates of the director.                                                                                                                                                              |
| directorDetails.dateOfAppointment           | The date of appointment of the director to the company.                                                                                                                                                                       |
| directorDetails.designation                 | The exact designation of the director in the company.                                                                                                                                                                         |
| directorDetails.address                     | The registered address of the director.                                                                                                                                                                                       |
| splitAddress                                | This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine                    | The first line of the director address is shown by this parameter.                                                                                                                                                            |
| whetherDscRegistered                        | This parameter shows whether the digital certificates are registered and valid.                                                                                                                                               |
| hashKey                                     | The hash key value.                                                                                                                                                                                                           |
{% endtab %}

{% tab title="API Response" %}
```
{
    "target": "Organization",
    "itemId": "617521c1c9d0c71ff1c57629",
    "accessToken": "gk335usik1drws3hqy4f1hanpria63su",
    "task": "detailedSearchByDin",
    "id": "6175221ec9d0c71ff1c5762c",
    "essentials": {
        "din": "05255419"
    },
    "result": {
        "din": "05255419",
        "designation": "DIRECTOR",
        "dateOfAppointment": "18/05/2012",
        "address": "",
        "name": "ALOK GOYAL",
        "whetherDscRegistered": "YES",
        "dscExpiryDate": "24/09/2022",
        "fatherName": "",
        "dob": "-",
        "noOfCompanies": "9",
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
                "numberOfMembers": "0",
                "subCategory": "NON-GOVT COMPANY",
                "class": "PUBLIC",
                "companyType": "INDIAN COMPANY",
                "companyName": "ECLERX SERVICES LIMITED",
                "paidUpCapital": "369834010",
                "authorisedCapital": "500100000",
                "whetherListed": "LISTED",
                "dateOfIncorporation": "24/03/2000",
                "lastAgmDate": "29/09/2020",
                "registrationNumber": "125319",
                "registeredAddress": "SONAWALLA BUILDING1ST FLOOR 29 BANK S FORT MUMBAI MH 400023 IN",
                "activeCompliance": "ACTIVE COMPLIANT",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "31/03/2020",
                "category": "COMPANY LIMITED BY SHARES",
                "status": "ACTIVE",
                "cin": "L72200MH2000PLC125319",
                "rocOffice": "ROC-MUMBAI",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "",
                "addressOtherThanRegisteredOffice": "401,501 BLDG 14,401,501,601,702 BLDG 11, PLOT 3 (PART) SERENE PROPERTIES PVT LTD, AIROLI NAVI MUMBAI 400708 MH IN",
                "emailId": "investor@eclerx.com",
                "emailID": "investor@eclerx.com",
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
                    "pincode": "400024",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "SONAWALLA BUILDING1ST FLOOR 29 BANK S FORT"
                },
                "natureOfBusiness": "SOFTWARE PUBLISHING, CONSULTANCY AND SUPPLY [SOFTWARE PUBLISHING INCLUDES PRODUCTION, SUPPLY AND DOCUMENTATION OF READY-MADE (NON-CUSTOMIZED) SOFTWARE, OPERATING SYSTEMS SOFTWARE, BUSINESS & OTHER APPLICATIONS SOFTWARE, COMPUTER GAMES SOFTWARE FOR ALL PLATFORMS. CONSULTANCY INCLUDES PROVIDING THE BEST SOLUTION IN THE FORM OF CUSTOM SOFTWARE AFTER ANALYZING THE USER’S NEEDS AND PROBLEMS. CUSTOM SOFTWARE ALSO INCLUDES MADE-TO-ORDER SOFTWARE BASED ON ORDERS FROM SPECIFIC USERS. ALSO, INCLUDED ARE WRITING OF SOFTWARE OF ANY KIND FOLLOWING DIRECTIVES OF THE USERS; SOFTWARE MAINTENANCE, WEB-PAGE DESIGN].",
                "noOfDirectors": "11",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "00053199",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "11/08/2007",
                        "address": "",
                        "name": "PRADEEP DHARUPRAKASH KAPOOR",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "13/04/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "00276807",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "11/08/2007",
                        "address": "",
                        "name": "ANISH GHOSHAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "22/07/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "00281165",
                        "designation": "WHOLETIME DIRECTOR",
                        "dateOfAppointment": "24/03/2000",
                        "address": "",
                        "name": "PRIYADARSHAN MUNDHRA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "18/10/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "01698542",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "10/05/2000",
                        "address": "",
                        "name": "ANJAN MALIK",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "19/08/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "02692531",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "28/01/2021",
                        "address": "",
                        "name": "SRINJAY SENGUPTA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "14/11/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "03091772",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "18/05/2011",
                        "address": "",
                        "name": "BIREN CHANDRAKANT GABHAWALA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "16/07/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "AEJPG8265Q",
                        "designation": "CFO(KMP)",
                        "dateOfAppointment": "31/07/2014",
                        "address": "",
                        "name": "ROHITASH GUPTA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "08/05/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "18/05/2012",
                        "address": "",
                        "name": "ALOK GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "06828033",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "11/03/2014",
                        "address": "",
                        "name": "DEEPA KAPOOR",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "27/07/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "07679583",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "15/03/2017",
                        "address": "",
                        "name": "SHAILESH SHARAD KEKRE",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "16/04/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "AMMPB6578N",
                        "designation": "COMPANY SECRETARY",
                        "dateOfAppointment": "30/01/2018",
                        "address": "",
                        "name": "PRATIK RAMESHBHAI BHANUSHALI",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "14/06/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "0",
                "subCategory": "NON-GOVT COMPANY",
                "class": "PRIVATE",
                "companyType": "INDIAN COMPANY",
                "companyName": "QUICKO TECHNOSOFT LABS PRIVATE LIMITED",
                "paidUpCapital": "36928906",
                "authorisedCapital": "37449930",
                "whetherListed": "UNLISTED",
                "dateOfIncorporation": "14/10/2010",
                "lastAgmDate": "29/12/2020",
                "registrationNumber": "055487",
                "registeredAddress": "GROUND, 2ND AND 3RD FLOOR, NO. 443, 4TH SECTOR, 17TH CROSS, HSR LAYOUT BANGALORE BANGALORE KA 560102 IN",
                "activeCompliance": "ACTIVE COMPLIANT",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "31/03/2020",
                "category": "COMPANY LIMITED BY SHARES",
                "status": "ACTIVE",
                "cin": "U72200KA2010PTC055487",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "accounts@whatfix.com",
                "emailID": "accounts@whatfix.com",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE SOUTH"
                    ],
                    "pincode": "560102",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "GROUND,2ND AND 3RD FLOOR,NO.443,4TH SECTOR,17TH CROSS,HSR LAYOUT"
                },
                "natureOfBusiness": "SOFTWARE PUBLISHING, CONSULTANCY AND SUPPLY [SOFTWARE PUBLISHING INCLUDES PRODUCTION, SUPPLY AND DOCUMENTATION OF READY-MADE (NON-CUSTOMIZED) SOFTWARE, OPERATING SYSTEMS SOFTWARE, BUSINESS & OTHER APPLICATIONS SOFTWARE, COMPUTER GAMES SOFTWARE FOR ALL PLATFORMS. CONSULTANCY INCLUDES PROVIDING THE BEST SOLUTION IN THE FORM OF CUSTOM SOFTWARE AFTER ANALYZING THE USER’S NEEDS AND PROBLEMS. CUSTOM SOFTWARE ALSO INCLUDES MADE-TO-ORDER SOFTWARE BASED ON ORDERS FROM SPECIFIC USERS. ALSO, INCLUDED ARE WRITING OF SOFTWARE OF ANY KIND FOLLOWING DIRECTIVES OF THE USERS; SOFTWARE MAINTENANCE, WEB-PAGE DESIGN].",
                "noOfDirectors": "7",
                "statusForEfiling": "ACTIVE",
                "pan": "AAACQ2314E",
                "directorDetails": [
                    {
                        "din": "00521511",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "30/12/2015",
                        "address": "",
                        "name": "ASHISH GUPTA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "16/09/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "03164394",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "06/03/2019",
                        "address": "",
                        "name": "SHWETA BHATIA",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "29/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "03188138",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "14/10/2010",
                        "address": "",
                        "name": "NAMBURU MARUTHI PRIYA KANYAKA VARA KUMAR",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "03196693",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "14/10/2010",
                        "address": "",
                        "name": "KHADIM HUSSAIN ISMAIL BATTI",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "03/11/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "08/05/2017",
                        "address": "",
                        "name": "ALOK GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "08380470",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "12/02/2020",
                        "address": "",
                        "name": "TEJESHWI SHARMA",
                        "whetherDscRegistered": "EXPIRED",
                        "dscExpiryDate": "28/02/2021",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "09193886",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "09/06/2021",
                        "address": "",
                        "name": "NARENDRA RATHI",
                        "whetherDscRegistered": "NO",
                        "dscExpiryDate": "-",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "0",
                "subCategory": "NON-GOVT COMPANY",
                "class": "PRIVATE",
                "companyType": "INDIAN COMPANY",
                "companyName": "ISKCON FARM LANDS PRIVATE LIMITED",
                "paidUpCapital": "100000",
                "authorisedCapital": "100000",
                "whetherListed": "UNLISTED",
                "dateOfIncorporation": "01/05/2012",
                "lastAgmDate": "28/11/2020",
                "registrationNumber": "045790",
                "registeredAddress": "ESPACE - 271, NIRVANA COUNTRY, SOUTH CITY - 2, SECTOR - 50, GURGAON HR 122016 IN",
                "activeCompliance": "ACTIVE COMPLIANT",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "31/03/2020",
                "category": "COMPANY LIMITED BY SHARES",
                "status": "ACTIVE",
                "cin": "U01403HR2012PTC045790",
                "rocOffice": "ROC-DELHI",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "alokgoyal1971@gmail.com",
                "emailID": "alokgoyal1971@gmail.com",
                "splitAddress": {
                    "district": [
                        "GURGAON"
                    ],
                    "state": [
                        [
                            "HARYANA",
                            "HR"
                        ]
                    ],
                    "city": [
                        "GURGAON"
                    ],
                    "pincode": "122016",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "ESPACE 271,NIRVANA SOUTH 2,SECTOR 50"
                },
                "natureOfBusiness": "ACTIVITIES ESTABLISHING A CROP, PROMOTING ITS GROWTH OR PROTECTING IT FROM DISEASE AND INSECTS. TRANSPLANTATION OF RICE IN RICE FIELDS. HORTICULTURAL AND NURSERY SERVICES.",
                "noOfDirectors": "2",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "02678210",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "01/05/2012",
                        "address": "",
                        "name": "POOJA GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "13/07/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "01/05/2012",
                        "address": "",
                        "name": "ALOK GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
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
                        "dscExpiryDate": "16/10/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "0",
                "subCategory": "NON-GOVT COMPANY",
                "class": "PRIVATE",
                "companyType": "INDIAN COMPANY",
                "companyName": "930 TECHNOLOGIES PRIVATE LIMITED",
                "paidUpCapital": "146950",
                "authorisedCapital": "1100000",
                "whetherListed": "UNLISTED",
                "dateOfIncorporation": "23/08/2016",
                "lastAgmDate": "25/08/2021",
                "registrationNumber": "095921",
                "registeredAddress": "#21103, TOWER 21, PRESTIGE SHANTINIKETAN APARTMENT ITPL ROAD, WHITEFIELD, BANGALORE BANGALORE KA 560048 IN",
                "activeCompliance": "ACTIVE COMPLIANT",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "31/03/2021",
                "category": "COMPANY LIMITED BY SHARES",
                "status": "ACTIVE",
                "cin": "U74999KA2016PTC095921",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "vishal.gahlaut@gmail.com",
                "emailID": "vishal.gahlaut@gmail.com",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE NORTH"
                    ],
                    "pincode": "560048",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "21103,TOWER 21,PRESTIGE SHANTINIKETAN APARTMENT ITPL ROAD,WHITEFIELD"
                },
                "natureOfBusiness": "OTHER BUSINESS ACTIVITIES N.E.C.",
                "noOfDirectors": "3",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "05255419",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "06/07/2017",
                        "address": "",
                        "name": "ALOK GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "07573394",
                        "designation": "WHOLETIME DIRECTOR",
                        "dateOfAppointment": "23/08/2016",
                        "address": "",
                        "name": "VISHAL GAHLAUT",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "27/08/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "07596654",
                        "designation": "WHOLETIME DIRECTOR",
                        "dateOfAppointment": "23/08/2016",
                        "address": "",
                        "name": "VISHESH KUMAR",
                        "whetherDscRegistered": "EXPIRED",
                        "dscExpiryDate": "20/08/2020",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "0",
                "subCategory": "NON-GOVT COMPANY",
                "class": "PRIVATE",
                "companyType": "INDIAN COMPANY",
                "companyName": "LOADSHARE NETWORKS PRIVATE LIMITED",
                "paidUpCapital": "427491",
                "authorisedCapital": "2000000",
                "whetherListed": "UNLISTED",
                "dateOfIncorporation": "20/01/2017",
                "lastAgmDate": "29/12/2020",
                "registrationNumber": "099338",
                "registeredAddress": "NO.509, 3RD FLOOR 6TH CROSS, 6TH BLOCK, KORMANGALA BANGALORE BANGALORE KA 560095 IN",
                "activeCompliance": "ACTIVE COMPLIANT",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "31/03/2020",
                "category": "COMPANY LIMITED BY SHARES",
                "status": "ACTIVE",
                "cin": "U63090KA2017PTC099338",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "raghu@loadshare.net",
                "emailID": "raghu@loadshare.net",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE SOUTH"
                    ],
                    "pincode": "560095",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "NO.509,3RD FLOOR 6TH CROSS,6TH BLOCK,KORMANGALA"
                },
                "natureOfBusiness": "",
                "noOfDirectors": "3",
                "statusForEfiling": "ACTIVE",
                "pan": "AADCL2205J",
                "directorDetails": [
                    {
                        "din": "05255419",
                        "designation": "NOMINEE DIRECTOR",
                        "dateOfAppointment": "13/06/2018",
                        "address": "",
                        "name": "ALOK GOYAL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05326741",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "05/03/2019",
                        "address": "",
                        "name": "PRAMOD PULIYAMPATTA",
                        "whetherDscRegistered": "EXPIRED",
                        "dscExpiryDate": "27/02/2021",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "07700545",
                        "designation": "DIRECTOR",
                        "dateOfAppointment": "20/01/2017",
                        "address": "",
                        "name": "RAGHURAM TALLURI",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "22/10/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
        ],
        "listOfLLPs": [
            {
                "numberOfMembers": "",
                "subCategory": "",
                "class": "",
                "companyType": "LLP",
                "companyName": "STELLARIS ADVISORS LLP",
                "paidUpCapital": "",
                "authorisedCapital": "",
                "whetherListed": "",
                "dateOfIncorporation": "28/03/2016",
                "lastAgmDate": "-",
                "registrationNumber": "",
                "registeredAddress": "6, PURVA PARKRIDGE, GOSHALA ROAD, OUTER RING ROAD, MAHADEVAPURA, BANGALORE BANGALORE KA 560048 IN",
                "activeCompliance": "",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "-",
                "category": "",
                "status": "ACTIVE",
                "cin": "AAG-0546",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "OTHER BUSINESS ACTIVITIES",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "ritesh@stellarisvp.com",
                "emailID": "ritesh@stellarisvp.com",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE NORTH"
                    ],
                    "pincode": "560048",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "6,PURVA PARKRIDGE,GOSHALA ROAD,OUTER RING ROAD,MAHADEVAPURA"
                },
                "natureOfBusiness": "",
                "noOfDirectors": "3",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "02013700",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "28/03/2016",
                        "address": "",
                        "name": "CHOWDHRI RAHUL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "19/10/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "02129763",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "28/03/2016",
                        "address": "",
                        "name": "BANGLANI RITESH",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "30/03/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "20/05/2016",
                        "address": "",
                        "name": "GOYAL ALOK",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "",
                "subCategory": "",
                "class": "",
                "companyType": "LLP",
                "companyName": "STELLARIS PARTNERS 2 LLP",
                "paidUpCapital": "",
                "authorisedCapital": "",
                "whetherListed": "",
                "dateOfIncorporation": "10/10/2019",
                "lastAgmDate": "-",
                "registrationNumber": "",
                "registeredAddress": "NO.6 PURVA PARKRIDGE GOSHALA ROAD GARUDACHARPALYA MAHADEVAPURA, NORTH BANGALORE BANGALORE BANGALORE KA 560048 IN",
                "activeCompliance": "",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "-",
                "category": "",
                "status": "ACTIVE",
                "cin": "AAQ-7660",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "OTHER BUSINESS ACTIVITIES",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "chetan@stellarisvp.com",
                "emailID": "chetan@stellarisvp.com",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE NORTH"
                    ],
                    "pincode": "560048",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "NO.6 PURVA PARKRIDGE GOSHALA ROAD GARUDACHARPALYA MAHADEVAPURA,NORTH"
                },
                "natureOfBusiness": "",
                "noOfDirectors": "3",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "02013700",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "CHOWDHRI RAHUL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "19/10/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "02129763",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "BANGLANI RITESH",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "30/03/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "GOYAL ALOK",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
            },
            {
                "numberOfMembers": "",
                "subCategory": "",
                "class": "",
                "companyType": "LLP",
                "companyName": "STELLARIS VENTURE ADVISORS 2 LLP",
                "paidUpCapital": "",
                "authorisedCapital": "",
                "whetherListed": "",
                "dateOfIncorporation": "10/10/2019",
                "lastAgmDate": "-",
                "registrationNumber": "",
                "registeredAddress": "NO.6, PURVA PARKRIDGE GOSHALA ROAD GARUDACHARPALYA MAHADEVAPURA, NORTH BANGALORE BANGALORE BANGALORE KA 560048 IN",
                "activeCompliance": "",
                "suspendedAtStockExchange": "",
                "balanceSheetDate": "-",
                "category": "",
                "status": "ACTIVE",
                "cin": "AAQ-7653",
                "rocOffice": "ROC-BANGALORE",
                "countryOfIncorporation": "",
                "descriptionOfMainDivision": "OTHER BUSINESS ACTIVITIES",
                "addressOtherThanRegisteredOffice": "",
                "emailId": "chetan@stellarisvp.com",
                "emailID": "chetan@stellarisvp.com",
                "splitAddress": {
                    "district": [
                        "BANGALORE"
                    ],
                    "state": [
                        [
                            "KARNATAKA",
                            "KA"
                        ]
                    ],
                    "city": [
                        "BANGALORE NORTH"
                    ],
                    "pincode": "560048",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "NO.6,PURVA PARKRIDGE GOSHALA ROAD GARUDACHARPALYA MAHADEVAPURA,NORTH"
                },
                "natureOfBusiness": "",
                "noOfDirectors": "3",
                "statusForEfiling": "ACTIVE",
                "pan": "",
                "directorDetails": [
                    {
                        "din": "02013700",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "CHOWDHRI RAHUL",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "19/10/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "02129763",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "BANGLANI RITESH",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "30/03/2023",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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
                        "din": "05255419",
                        "designation": "DESIGNATED PARTNER",
                        "dateOfAppointment": "10/10/2019",
                        "address": "",
                        "name": "GOYAL ALOK",
                        "whetherDscRegistered": "YES",
                        "dscExpiryDate": "24/09/2022",
                        "pan": "",
                        "noOfCompanies": "",
                        "fatherName": "",
                        "dob": "-",
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

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronId.../organizations" method="post" summary="Search Detailed Director & Company Data by DIN" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronId.../organizations`

\




\


This method is used to search for the complete details of the director and company by the Director identification Number (DIN)
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

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/50b1873a9014d0b52730)

**Director's information**

The API returns the following data about the company

1. din
2. name
3. dob
4. designation
5. address
6. noOfCompanies
7. listOfCompanies
8. listOfLLPs

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

#### Creating ROC DIN Director search \`hunt\` request.

Use the following exchange parameters for ROC DIN search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/hunts" method="post" summary="ROC DIN Detailed search `hunt` request" %}
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
Task to be performed - quickSearchByDin
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
          "MH",
          "MAHARASHTRA"
        ]
      ],
      "district": [
        "PUNE"
      ],
      "city": [],
      "pincode": "411021",
      "country": [
        "IN",
        "IND",
        "INDIA"
      ],
      "addressLine": "...addressLine..."
  },
  "listOfCompanies": [{
    "companyName": "...companyName...",
    "rocOffice": "...rocOffice...",
    "registrationNumber": "...registrationNumber...",
    "category": "...category...",
    "subCategory": "...subCategory...",
    "class": "...class...",
    "authorisedCapital": "...authorisedCapital...",
    "paidUpCapital": "...paidUpCapital...",
    "numberOfMembers": "...numberOfMembers...",
    "dateOfIncorporation": "...dateOfIncorporation...",
    "registeredAddress": "...registeredAddress...",
    "pan": "...pan...",
    "emailId": "...emailId...",
    "whetherListed": "...whetherListed...",
    "lastAgmDate": "...lastAgmDate...",
    "balanceSheetDate": "...balanceSheetDate...",
    "statusForEfiling": "...statusForEfiling...",
    "natureOfBusiness": "...natureOfBusiness...",
    "splitAddress": {
      "state": [
        [
          "MH",
          "MAHARASHTRA"
        ]
      ],
      "district": [
        "PUNE"
      ],
      "city": [],
      "pincode": "411021",
      "country": [
        "IN",
        "IND",
        "INDIA"
      ],
      "addressLine": "...addressLine..."
    },
    "cin": "...cin...",
    "directorDetails": [
      {
        "name": "...name...",
        "fatherName": "...fatherName...",
        "dob": "...dob...",
        "pan": "...pan...",
        "din": "...din...",
        "dscExpiryDate": "...dscExpiryDate...",
        "dateOfAppointment": "...dateOfAppointment...",
        "designation": "...designation...",
        "address": "...address...",
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
        "whetherDscRegistered": "...whetherDscRegistered..."
      }
    ]
  }],
  "listOfLLPs": [{
    "companyName": "...companyName...",
    "rocOffice": "...rocOffice...",
    "registrationNumber": "...registrationNumber...",
    "category": "...category...",
    "subCategory": "...subCategory...",
    "class": "...class...",
    "authorisedCapital": "...authorisedCapital...",
    "paidUpCapital": "...paidUpCapital...",
    "numberOfMembers": "...numberOfMembers...",
    "dateOfIncorporation": "...dateOfIncorporation...",
    "registeredAddress": "...registeredAddress...",
    "pan": "...pan...",
    "emailId": "...emailId...",
    "whetherListed": "...whetherListed...",
    "lastAgmDate": "...lastAgmDate...",
    "balanceSheetDate": "...balanceSheetDate...",
    "statusForEfiling": "...statusForEfiling...",
    "natureOfBusiness": "...natureOfBusiness...",
    "splitAddress": {
      "state": [
        [

        ]
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
    "cin": "...cin...",
    "directorDetails": [
      {
        "name": "...name...",
        "fatherName": "...fatherName...",
        "dob": "...dob...",
        "pan": "...pan...",
        "din": "...din...",
        "dscExpiryDate": "...dscExpiryDate...",
        "dateOfAppointment": "...dateOfAppointment...",
        "designation": "...designation...",
        "address": "...address...",
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
        "whetherDscRegistered": "...whetherDscRegistered...",
        "$$hashKey": "...hashKey..."
      }
    ]
  }]
  }
```
{% endswagger-response %}
{% endswagger %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/50b1873a9014d0b52730)

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "target": "Organization",
    "itemId": "....id-of-the-organzation-object-created.....",
    "accessToken": ".....access-token-from-the-organization-creation-request.....",
    "task": "detailedSearchByDin",
    "essentials": {
    	"din": ".....director-din-to-search-for...."
    }
  }
```


{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/50b1873a9014d0b52730)
