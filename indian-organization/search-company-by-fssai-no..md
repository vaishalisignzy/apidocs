# Search Company by FSSAI No.

### &#x20;&#xD;Introduction

The FSSAI is an acronym for the <mark style="color:orange;">Food Safety and Standards Authority of India</mark> is an autonomous body established under the _Ministry of Health & Family Welfare_, Government of India.                   &#x20;

All organisations which are a part of the food or agriculture industry are registered with a unique **14-digit FSSAI number** which is used by the Search by FSSAI API service by Signzy to retrieve the details of the registered organisation.

### How to call the API

You will need to login before sending a request. You are required to pass the access token received from the login call, as an authorization header in the FSSAI request along with licenseNumber.

### API Input Guidelines

Provide the correct **FSSAI number** issued by the Ministry of Health & Family Welfare. It is a 14 digit number.

**The following information is generated:**

* Licence Number
* Entity Name
* Status
* Licence Type
* Premises Address
* List of Products

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for FSSAI based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization            | Required | String | Access Token                   |
| ------------------------ | -------- | ------ | ------------------------------ |
| Content-Type             | Required | String | Application/JSON               |
| essentials.licenceNumber | Required | String | Licence Number issued by MoHFW |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/fssais' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "licenseNumber": "<FSSAI License Number to be searched for>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME            | DESCRIPTION                                                                                                                                                                                                                       |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials                | This contains the essential data for output.                                                                                                                                                                                      |
| essentials.licenseNumber  | The FSSAI license number is displayed here.                                                                                                                                                                                       |
| id                        | This contains the access token received during login request.                                                                                                                                                                     |
| patronId                  | This parameter is returned as userId parameter of login request.                                                                                                                                                                  |
| result                    | The final response parameters to be displayed are held in this parameter.                                                                                                                                                         |
| result.licenseType        | The type of license issued by FSSAI to the organization being searched.                                                                                                                                                           |
| result.entityName         | The name of the organization registered to the FSSAI number that is being searched.                                                                                                                                               |
| result.status             | The current status of the organization is displayed here.                                                                                                                                                                         |
| result.premissesAddress   | The address of the organization premises is shown here.                                                                                                                                                                           |
| premissesAddress.state    | The state where the organization is located.                                                                                                                                                                                      |
| premissesAddress.district | The district where the organization is located.                                                                                                                                                                                   |
| premissesAddress.address  | The address of the physical location of the organization is displayed here.                                                                                                                                                       |
| result.listOfProducts     | The list of products that are provided by the organization.                                                                                                                                                                       |
| result.splitAddress       | This parameter distinguishes the various parts of the address of the organization into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine  | The first line of the address is displayed by this parameter.                                                                                                                                                                     |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "licenseNumber": "10015043001238"
    },
    "id": "61884e4c7157fd10dd4f2c3c",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "licenseNumber": "10015043001238",
        "entityName": "KOLANKANNY & CO.",
        "status": "INACTIVE",
        "licenseType": "CENTRAL LICENSE",
        "premissesAddress": {
            "district": "",
            "address": "97/2, 2ND FLOOR, CAMELOT, LEWIS ROAD, COOKE TOWN",
            "state": "KARNATAKA",
            "pincode": "560005"
        },
        "listOfProducts": [
            {
                "slNo": "16",
                "foodProductCategory": "16 - PREPARED FOODS"
            },
            {
                "slNo": "15",
                "foodProductCategory": "15 - READY-TO-EAT SAVOURIES"
            }
        ],
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
            "addressLine": "97/2,2ND FLOOR,CAMELOT,LEWIS ROAD,COOKE TOWN KARNATAKA"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/b8e9e91ed1593d6faa51)
