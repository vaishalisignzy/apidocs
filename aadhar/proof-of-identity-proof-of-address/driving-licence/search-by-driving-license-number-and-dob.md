---
description: DL Number Based Search
---

# Search by Driving License Number & D.O.B

### Introduction

This is a very interesting feature developed by SIGNZY wherein the details of the user can easily be verified by entering the DL number and DOB of the licence holder. The service can easily use this information to verify and generate the user details such as Name, Address, Father Name etc.



> &#x20;       **Please Note:**&#x20;>

> * Card details should be manually validated, preferably by the card owner, before sending it for DL Number Based Search.
> * For DL Number Based Search of driving licence , licence number ,date of birth in format (dd/mm/yyyy) are mandatory.

### API Usecase

This API uses DL number and D.O.B of the user and provide the details of that particular user. It helps in auto-generating the details for the user without having to manually provide the information. Following information is generated:&#x20;

* Name
* Father/Husband Name
* Address
* District
* Pincode
* State
* Country
* Class of vehicle details

### How to call the API

You will need to login before sending a search request. You are required to pass the access token received from the login call, as an authorization header.

### API Input Guidelines

* DL number of the person (MH12XXXXXXXXXXX)
* D.O.B of the person (dd/mm/yyyy)nput Parameters



### Sample CURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                                  | Compulsory/Optional |
| --------------- | -------------------------------------------- | ------------------- |
| type            | Type of Identity                             | Compulsory          |
| email           |                                              |                     |
| callbackurl     | URL where response will be posted            | Compulsory          |
| images          | Front and Back side Image of Driving licence | Compulsory          |


{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<PATRON ID>/identities' \
--header 'Authorization: AUTH' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
                "type": "drivingLicence",
                "email": "ankur.rand@signzy.com",
                "callbackUrl": "https://www.w3schools.com",
                "images": []
            }'

```


{% endtab %}
{% endtabs %}

****

**Response**

{% tabs %}
{% tab title="Response Parameters" %}
| Parameters Name | Description |
| --------------- | ----------- |
| accessToken     |             |
| autoRecognition |             |
| verification    |             |
| forgeryCheck    |             |
| id              |             |
| patronId        |             |


{% endtab %}

{% tab title="Sample Response" %}
```
{
    "type": "drivingLicence",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [],
    "accessToken": "xvn5ekazz1d45kfoaetnt7hw69w7qr23c",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "617fd6617157fd10dd4edc58",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2:** Hit Snoops API&#x20;

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Response                                        |
| --------------- | ----------------------------------------------- |
| service         | Type of Signzy service - “identity extraction”  |
| itemId          | Contains the identity item id                   |
| accessToken     | URL where response will be posted               |
| task            | The type of task performed - “Auto Recognition” |
| essentials      | Contains the essential output data              |


{% endtab %}

{% tab title="Snoops Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "service": "Identity",
    "itemId": "<Identity object ID>",
    "accessToken": "<Identity Access Token>",
    "task": "fetch",
    "essentials": {
        "dob": "<D.O.B>",
        "number": "<DL Number>"
    }
}'
```
{% endtab %}
{% endtabs %}

###

### Sample API Response

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                                   | DESCRIPTION                                                                                                                                                                                                                    |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| result                                           | The final response parameters are contained here.                                                                                                                                                                              |
| result.dlNumber                                  | The driving license number that is being searched is displayed by this parameter.                                                                                                                                              |
| result.dob                                       | The date of birth of the license holder.                                                                                                                                                                                       |
| result.badgedetails                              | The badge details of the driving license holder(in case of certain commercial vehicles) are displayed by this parameter.                                                                                                       |
| badgedetails.badgeIssueDate                      | The date of issue of the badge is displayed by this parameter.                                                                                                                                                                 |
| badgedetails.badgeNo                             | The badge number of the driver.                                                                                                                                                                                                |
| badgedetails.classofvehicle                      | The class of vehicle to which the vehicle belongs to is displayed by this parameter.                                                                                                                                           |
| result.dlValidity                                | The validity information of the driving license is displayed by this parameter.                                                                                                                                                |
| dlValidity.nonTransport                          | The driving license issued is for a vehicle of non transport category.                                                                                                                                                         |
| dlValidity.to                                    | The date from which the driving license is valid.                                                                                                                                                                              |
| dlValidity.from                                  | The date till which the driving license will be valid.                                                                                                                                                                         |
| result.hazardousValidTill                        | For certain transport vehicles, this parameter displays the validity till which the vehicle is declared fit.                                                                                                                   |
| hazardousValidTill.transport                     | The driving license issued is for a vehicle of the transport category.                                                                                                                                                         |
| hazardousValidTill.from                          | The date from which the vehicle is declared fit.                                                                                                                                                                               |
| hazardousValidTill.to                            | The date upto which the vehicle is declared fit.                                                                                                                                                                               |
| result.detailsOfDrivingLicence                   | This parameter contains the details of the driving license like vehicle and owner information.                                                                                                                                 |
| detailsOfDrivingLicence.dateOfIssue              | The date of issue for the driving license is displayed here.                                                                                                                                                                   |
| detailsOfDrivingLicence.detailsOfLastTransaction | This parameter displays the details of last transaction, if any, on the driving license.                                                                                                                                       |
| detailsOfDrivingLicence.status                   | This parameter displays the status of the last transaction.                                                                                                                                                                    |
| detailsOfDrivingLicence.lastTransactedAt         | This parameter shows the details of the location of the last transaction.                                                                                                                                                      |
| detailsOfDrivingLicence.name                     | The name of the driving license holder.                                                                                                                                                                                        |
| detailsOfDrivingLicence.fatherOrHusbandName      | This parameter provides the name of the father or spouse name.                                                                                                                                                                 |
| detailsOfDrivingLicence.address                  | The address information of the driving license holder is displayed here.                                                                                                                                                       |
| detailsOfDrivingLicence.addressList              | This parameter contains the list of addresses that is registered to the driving license holder.                                                                                                                                |
| addressList.completeAddress                      | The complete address of the owner is shown here.                                                                                                                                                                               |
| addressList.type                                 | This determines the type of address that is registered to the driving license.                                                                                                                                                 |
| addressList.splitAddress                         | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine                         | The first line of the address is displayed here.                                                                                                                                                                               |
| addressList.photo                                | The photo of the DL holder is displayed here.                                                                                                                                                                                  |
| result.covDetails                                | This parameter contains the details about the class of vehicle to which the driving license is registered.                                                                                                                     |
| covDetails.covCategory                           | The category information to which the class of vehicle belongs to.                                                                                                                                                             |
| covDetails.classOfVehicle                        | The class of vehicle to which the registered vehicle belongs to.                                                                                                                                                               |
| covDetails.covIssueDate                          | The date of issue for the class of vehicle is displayed by this parameter.                                                                                                                                                     |
{% endtab %}

{% tab title="API Response " %}
```
{
            "dlNumber": "DL-042011014XXX",
            "dob": "09/02/1976",
            "badgeDetails": [
                {
                    "badgeIssueDate": "",
                    "badgeNo": "",
                    "classOfVehicle": [
                        "ADPVEH"
                    ]
                }
            ],
            "dlValidity": {
                "nonTransport": {
                    "to": "08/02/2026",
                    "from": "01/03/2011"
                },
                "hazardousValidTill": "",
                "transport": {
                    "to": "",
                    "from": ""
                },
                "hillValidTill": ""
            },
            "detailsOfDrivingLicence": {
                "dateOfIssue": "01/03/2011",
                "dateOfLastTransaction": "",
                "status": "",
                "lastTransactedAt": "",
                "name": "ANURAG BREJA",
                "fatherOrHusbandName": "BODH RAJ BREJA",
                "addressList": [
                    {
                        "completeAddress": "HNO-178 A2/B MIG FLATS                           PASCHIM VIHAR,DELHI                              110063",
                        "type": "permanent",
                        "splitAddress": {
                            "district": [
                                "WEST DELHI"
                            ],
                            "state": [
                                [
                                    "DELHI",
                                    "DL"
                                ]
                            ],
                            "city": [
                                "DELHI"
                            ],
                            "pincode": "110063",
                            "country": [
                                "IN",
                                "IND",
                                "INDIA"
                            ],
                            "addressLine": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR,DELHI"
                        }
                    },
                    {
                        "completeAddress": "HNO-178 A2/B MIG FLATS                           PASCHIM VIHAR,DELHI                              110063",
                        "type": "temporary",
                        "splitAddress": {
                            "district": [
                                "WEST DELHI"
                            ],
                            "state": [
                                [
                                    "DELHI",
                                    "DL"
                                ]
                            ],
                            "city": [
                                "DELHI"
                            ],
                            "pincode": "110063",
                            "country": [
                                "IN",
                                "IND",
                                "INDIA"
                            ],
                            "addressLine": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR,DELHI"
                        }
                    }
                ],
                "address": "HNO-178 A2/B MIG FLATS                           PASCHIM VIHAR,DELHI                              110063",
                "photo": "https://persist.signzy.tech/api/files/213024611/download/6147a181e6694e51a0f35e0d257bd28b54f6509206864a7cbc53c2043d3c918a.jpeg",
                "splitAddress": {
                    "district": [
                        "WEST DELHI"
                    ],
                    "state": [
                        [
                            "DELHI",
                            "DL"
                        ]
                    ],
                    "city": [
                        "DELHI"
                    ],
                    "pincode": "110063",
                    "country": [
                        "IN",
                        "IND",
                        "INDIA"
                    ],
                    "addressLine": "HNO-178 A2/B MIG FLATS PASCHIM VIHAR,DELHI"
                },
                "covDetails": [
                    {
                        "covCategory": "NT",
                        "classOfVehicle": "ADPVEH",
                        "covIssuedate": "01/03/2011"
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

###

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/47eeafb04c3aba2ffb3b)

