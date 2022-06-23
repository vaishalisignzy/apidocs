# Search Company by Professional Tax Number (PTRC)

### &#xD;Introduction

PTRC stands for <mark style="color:orange;">Professional Tax Registration Certificate</mark>. The function of a PTRC is to allow the employer to deduct and deposit professional tax from the salary of its employees. Each individual who is issued with PTRC is also assigned a unique 12-digit PTRC number.

### API Usecase

With the help of this API by Signzy, user can retrieve the details of an employee and the organisation using the unique PTRC number and the state where the employee is employed

### How to call the API

You will need to login before sending a Professional Tax Registration request. You are required to pass the access token received from the login call, as an authorization header in the PTRC request along with Professional Tax Number.

### API Input Guidelines

Provide the correct **Professional Tax number**. It is a 12 digit number.

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for Professional Tax Number based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization           | Required | String | Access Token                           |
| ----------------------- | -------- | ------ | -------------------------------------- |
| Content-Type            | Required | String | Application/JSON                       |
| task                    | Required | String | Registration number search             |
| essentials.memberNumber | Required | String | Membership number                      |
| essentials.Type         | Required | String | Membership type could be of ACS or FCS |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/ptrcs' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "professionalTaxNumber": "<Professional Tax Number>",
        "state": "<State to be searched for>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                                       |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                          | The final response parameters are displayed here.                                                                                                                                                                                                 |
| result.address1                                 | The first line of the registered address of the company .                                                                                                                                                                                         |
| result.address2                                 | The second line of the registered address of the company .                                                                                                                                                                                        |
| result.address3                                 | The third line of the registered address of the company.                                                                                                                                                                                          |
| result.talukaName                               | The taluka name of the registered address.                                                                                                                                                                                                        |
| result.streetName                               | The street name of the registered address.                                                                                                                                                                                                        |
| result.pinCode                                  | The pincode of the registered address.                                                                                                                                                                                                            |
| result.districtName                             | The district name of the registered address.                                                                                                                                                                                                      |
| result.cityName                                 | The city name of the registered address.                                                                                                                                                                                                          |
| result.effectiveOrCanceledDate                  | The date of effect or the date of cancellation.                                                                                                                                                                                                   |
| result.status                                   | The current status of the company.                                                                                                                                                                                                                |
| result.state                                    | The state of the company address.                                                                                                                                                                                                                 |
| result.tin                                      | The TIN number of the company.                                                                                                                                                                                                                    |
| result.principalAddress                         | The principal address of the company.                                                                                                                                                                                                             |
| result.dealerStatus                             | The present dealer status of the company.                                                                                                                                                                                                         |
| result.gstin                                    | The GST identification number.                                                                                                                                                                                                                    |
| result.dealerName                               | The dealer name of the company.                                                                                                                                                                                                                   |
| result.splitAddress                             |                                                                                                                                                                                                                                                   |
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
| result.gstnRecords                              | This parameter contains the details of the GST application.                                                                                                                                                                                       |
| gstnRecords.applicationStatus                   | The current application status is displayed here.                                                                                                                                                                                                 |
| gstnRecords.registrationName                    | The name to which the company has been registered.                                                                                                                                                                                                |
| gstnRecords.mobNum                              | The mobile number registered with GSTN.                                                                                                                                                                                                           |
| gstnRecords.regType                             | The type of registration as recorded with GSTN.                                                                                                                                                                                                   |
| gstnRecords.emailId                             | The email ID registered with GSTN records.                                                                                                                                                                                                        |
| gstnRecords.tinNumber                           | The TIN number of the company as available from GSTN records.                                                                                                                                                                                     |
| gstnRecords.gstinRefId                          | The GSTN reference id.                                                                                                                                                                                                                            |
| gstnRecords.gstin                               | The GST identification number.                                                                                                                                                                                                                    |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "professionalTaxNumber": "99522311536P",
        "state": "Maharashtra"
    },
    "id": "618862307157fd10dd4f2c42",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "address1": "",
        "address2": "",
        "address3": "",
        "talukaName": "",
        "streetName": "",
        "pinCode": "",
        "districtName": "",
        "cityName": "",
        "effectiveOrCanceledDate": "",
        "address": "",
        "status": "",
        "state": "MAHARASHTRA",
        "tin": "099522311536",
        "principalAddress": "",
        "dealerStatus": "",
        "gstin": "",
        "dealerName": "ADDTEQ SOFTWARE INDIA PVT LTD",
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
        "dataFromGstn": {
            "gstnDetailed": {
                "constitutionOfBusiness": "",
                "legalNameOfBusiness": "",
                "tradeNameOfBusiness": "",
                "centreJurisdiction": "",
                "stateJurisdiction": "",
                "registrationDate": "",
                "taxPayerDate": "",
                "gstinStatus": "",
                "cancellationDate": "",
                "natureOfBusinessActivities": [],
                "principalPlaceAddress": "",
                "principalPlaceBuildingNoFromGST": "",
                "principalPlaceBuildingNameFromGST": "",
                "principalPlaceFlatNo": "",
                "additionalPlaceAddress": "",
                "additionalPlaceBuildingNoFromGST": "",
                "additionalPlaceBuildingNameFromGST": "",
                "additionalPlaceFlatNo": "",
                "additionalPlaceSplitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [],
                    "addressLine": ""
                },
                "principalPlaceSplitAddress": {
                    "district": [],
                    "state": [
                        []
                    ],
                    "city": [],
                    "pincode": "",
                    "country": [],
                    "addressLine": ""
                }
            },
            "gstnRecords": [
                {
                    "applicationStatus": "",
                    "registrationName": "",
                    "mobNum": "",
                    "regType": "",
                    "emailId": "",
                    "tinNumber": "",
                    "gstinRefId": "",
                    "gstin": ""
                }
            ],
            "gstin": ""
        }
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/0d0e7922f1d955d19e33)

**Valid State List**

1\) Maharashtra
