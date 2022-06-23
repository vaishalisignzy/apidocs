# Search Company by Import Export Code (IEC)

### &#xD;Introduction

IEC <mark style="color:orange;">(Importer Exporter Code)</mark> number is a 10 digit code number issued to an exporter or importer by the regional office of the <mark style="color:orange;">Director General of Foreign Trade</mark> (DGFT), Department of Commerce, Government of India.&#x20;

### How to call the API

You will need to login before sending IEC code request. You are required to pass the access token received from the login call, as authorization header in the IEC request along with iecCode.

### API Input Guidelines

Provide the correct **FSSAI number** issued by the Ministry of Health & Family Welfare. It is a 14 digit number.

**The following information is generated:**

* IEC Code
* IEC Allotment Date
* File Number
* File Date
* Party Name and address
* Part Name
* Party Address
* Phone Number&#x20;
* Email
* Exporter Type
* Date of Establishment
* BIN Number
* Nature of Concern
* Banker Details
* Party Address
* Branches&#x20;
* Branch Details
* Director
* Director Details

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for IEC based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization      | Required | String | Access Token            |
| ------------------ | -------- | ------ | ----------------------- |
| Content-Type       | Required | String | Application/JSON        |
| essentials.iecCode | Required | String | IEC Code issued by DGFT |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/iecs' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "iecCode": "<IEC Code>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                | DESCRIPTION                                                                                                                                                                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                        | The final response parameters are contained in this parameter.                                                                                                                                                                                    |
| result.iec                    | The importer exporter code is displayed here.                                                                                                                                                                                                     |
| result.iecAllotmentDate       | The date of allotment of the IEC code to the organization is shown here.                                                                                                                                                                          |
| result.fileNumber             | The file number of the IEC member organization.                                                                                                                                                                                                   |
| resul.fileDate                | The date of filing for the IEC registration is displayed here.                                                                                                                                                                                    |
| result.partyNameAndAddress    | The name and address of the member organization that is registered with IEC.                                                                                                                                                                      |
| result.partyName              | The name of the organization is displayed here.                                                                                                                                                                                                   |
| result.partyAddress           | The address of the organization is displayed here.                                                                                                                                                                                                |
| result.email                  | The email ID of the member organization.                                                                                                                                                                                                          |
| result.exporterType           | This parameter shows the details about the type of exporter that the organization represents.                                                                                                                                                     |
| result.dateOfEstablishment    | The date of establishment of the organization is displayed here.                                                                                                                                                                                  |
| result.bin                    | The business identification number is displayed by this parameter.                                                                                                                                                                                |
| result.pan                    | The PAN number for the business is displayed by this parameter.                                                                                                                                                                                   |
| result.phone                  | The phone number information for the organization is displayed here.                                                                                                                                                                              |
| result.natureOfConcern        | This parameter displays the nature of the organization (i.e Private Limited).                                                                                                                                                                     |
| result.bankerDetail           | This parameter contains the banker information                                                                                                                                                                                                    |
| result.branches               | This parameter contains the branch information for the organization.                                                                                                                                                                              |
| branches.branch\_details      | This parameter contains the branch details and information about the organization.                                                                                                                                                                |
| branches.address              | The address for a particular branch of the organization is displayed here.                                                                                                                                                                        |
|  branches.splitAddress        | This parameter distinguishes the various parts of the address of the particular branch into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”.&#xD;        |
| branches.addressLine          | The first line of the address is displayed here.                                                                                                                                                                                                  |
| result.directors              | This parameter contains the details about the director members of the organization.                                                                                                                                                               |
| directors.directorName        | The name of the director is displayed here.                                                                                                                                                                                                       |
| directors.parentName          | The parent name for the director member is shown by this parameter.                                                                                                                                                                               |
| directors.address             | The address of the director.                                                                                                                                                                                                                      |
| directors.number              | The serial number assigned to the director is displayed here.                                                                                                                                                                                     |
| directors.splitAddress        | <p>This parameter distinguishes the various parts of the address of the director into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.</p><p></p>      |
| splitAddress.addressLine      | The first line of the address is displayed here.                                                                                                                                                                                                  |
| result.splitPartyAddress      | This parameter distinguishes the various parts of the registered address of the organization into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.&#xD; |
| splitPartyAddress.addressLine | The first line of the organization's registered address is displayed here.                                                                                                                                                                        |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "iecCode": "<IEC Code>"
    },
    "id": "61885c6c7157fd10dd4f2c3f",
    "patronId": "<Patron ID>",
    "result": {
        "iec": "0908018525",
        "iecAllotmentDate": "26/02/2009",
        "fileNumber": "09/04/130/02051/AM09/",
        "fileDate": "24/02/2009",
        "partyNameAndAddress": "BRAHMMAS AGRO INDUSTRIES PVT LTD PLOT NO. 324, BLOCK B, MLA & MP COLONY, ROAD NO.10C, JUBILEE HILLS, HYDERABAD.   AP. PIN-500033",
        "partyName": "BRAHMMAS AGRO INDUSTRIES PVT LTD",
        "partyAddress": "PLOT NO. 324, BLOCK B, MLA & MP COLONY, ROAD NO.10C, JUBILEE HILLS, HYDERABAD.   AP. PIN-500033",
        "phone": "08594232772",
        "email": "BRAHMMAS@YAHOO.COM",
        "exporterType": "2 MANUFACTURER EXPORTER",
        "dateOfEstablishment": "25/08/2008",
        "bin": "AADCB5485CFT001",
        "natureOfConcern": "3  PRIVATE LIMITED",
        "bankerDetail": "SBI, CHIRALA BR, PRAKASAM DIST A/C Type:1 CA A/C No  :30636014510",
        "splitPartyAddress": {
            "district": [
                "HYDERABAD"
            ],
            "state": [
                [
                    "TELANGANA",
                    "TG"
                ]
            ],
            "city": [
                "SHAIKPET"
            ],
            "pincode": "500033",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "BRAHMMAS AGRO INDUSTRIES PVT LTD PLOT NO.324,BLOCK B,MLA MP COLONY,ROAD NO.10C,JUBILEE HILLS AP"
        },
        "pan": "AADCB5485C",
        "branches": [
            {
                "1": "DESAIPET VILLAGE VETAPALEM MANDAL PRAKASAM DIST",
                "branchSerialNumber": "1",
                "pin": "0",
                "address": "DESAIPET VILLAGE VETAPALEM MANDAL PRAKASAM DIST",
                "splitAddress": {
                    "district": [
                        "PRAKASAM"
                    ],
                    "state": [
                        [
                            "ANDHRA PRADESH",
                            "AP"
                        ]
                    ],
                    "city": [
                        "DESAIPET"
                    ],
                    "pincode": "523187",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "VILLAGE VETALEM MANDAL DIST"
                }
            }
        ],
        "directors": [
            {
                "number": "1",
                "directorName": "B. SRINIVASA RAO",
                "parentName": "VENKATESWARLU",
                "address": "FLAT NO. 504, SMR VINAY PRANGANAM MADHAPUR, HITECHCITY, HYDERABAD PIN-500087 Phone/Email:09985431556",
                "splitAddress": {
                    "district": [
                        "HYDERABAD"
                    ],
                    "state": [
                        [
                            "TELANGANA",
                            "TG"
                        ]
                    ],
                    "city": [
                        "TIRUMALAGIRI"
                    ],
                    "pincode": "500087",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "FLAT NO.504,SMR VINAY PRANGANAM MADHAPUR,HITECH"
                }
            },
            {
                "number": "2",
                "directorName": "T. MASTAN REDDY",
                "parentName": "VENKAT REDDY",
                "address": "NEAR SOLMON CENTER, BOSE NAGAR, CHIRALA PIN-523155 Phone/Email:09704795383",
                "splitAddress": {
                    "district": [
                        "PRAKASAM"
                    ],
                    "state": [
                        [
                            "ANDHRA PRADESH",
                            "AP"
                        ]
                    ],
                    "city": [
                        "CHIRALA"
                    ],
                    "pincode": "523155",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "NEAR SOLMON CENTER,BOSE NAGAR"
                }
            }
        ],
        "statusCode": "0",
        "status": "NORMAL"
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/044e5b3d3def7851c71e)
