# Search by VAT Number

### &#xD;Introduction

**Value Added Tax** (VAT) is a major source of revenue for all Indian states and union territories _(except Andaman and Nicobar Islands and Lakshadweep)_. VAT was introduced as an indirect tax in the Indian taxation system to replace the existing general sales tax. The Value Added Tax Act (2005) and associated VAT rules came into effect beginning April 1, 2005 in many Indian states.&#x20;

### API Usecase

Signzy’s unique API - **Search by VAT number** utilises the VAT number to generate the details of the business/dealer like Name, Address etc for which the VAT number is registered.

**The following information is generated about the Business dealer:**

* Registration Status
* CST Status&#x20;
* PAN
* Dealer's Name
* Dealer's Address
* Registration Date&#x20;
* Cancellation Date



### How to call the API

You will need to login before sending VAT number request. You are required to pass the access token received from the login call, as an authorization header in the VAT request along with vatNumber.



### API Input Guidelines

Provide correct **11-digit unique VAT number**, that's allotted by **the Commercial Tax Department** of each State Government.



### Sample CURL Request

Use the following exchange parameters for VAT based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String | Access Token             |
| -------------------- | -------- | ------ | ------------------------ |
| Content-Type         | Required | String | Application/JSON         |
| essentials.vatNumber | Required | String | VAT number of the delear |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/vats' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '
{
    "essentials": {
    	"vatNumber": "<Company's VAT to be search for>"
    }
  }
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters " %}
| **PARAMETER NAME**       | **DESCRIPTION**                                                                                                                                                                                                                          |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                   | This contains the final response parameters to be displayed.                                                                                                                                                                             |
| result.cstStatus         | The central sales tax status for the VAT number.                                                                                                                                                                                         |
| result.pan               | The PAN number of the VAT holder.                                                                                                                                                                                                        |
| result.status            | The status of the VAT is displayed here.                                                                                                                                                                                                 |
| result.ownerName         | The VAT holder name is displayed here.                                                                                                                                                                                                   |
| result.dealer            | The dealer name associated with the VAT.                                                                                                                                                                                                 |
| result.address           | The address of the business associated with the VAT is displayed here.                                                                                                                                                                   |
| result.regDate           | The registration date of the business associated with the VAT is displayed by this parameter.                                                                                                                                            |
| result.cancelDate        | The cancellation date for the VAT is mentioned here.                                                                                                                                                                                     |
| result.splitAddress      | This parameter distinguishes the various parts of the address of the VAT holder's business into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA” |
| splitAddress.addressLine | This parameter contains the first line of the address.                                                                                                                                                                                   |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "vatNumber": "<VAT Number>"
    },
    "id": "617bd7b87157fd10dd4eb2e0",
    "patronId": "6140962af6d4030eae0496e0",
    "result": [
        {
            "registrationStatus": "ACTIVE",
            "cstStatus": "ACTIVE",
            "pan": "AAOPD9447N",
            "status": "",
            "ownerName": "",
            "dealer": "UNICORN TRADING",
            "address": "F 161,RICHMOND PARK,DLF PHASE IV HARYANA",
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
                "addressLine": "F 161,RICHMOND PARK,DLF PHASE IV HARYANA"
            },
            "regDate": "07/05/2016",
            "cancelDate": ""
        }
    ]
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
|             |                                        |





&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/d32dfcae209f7880b155)
