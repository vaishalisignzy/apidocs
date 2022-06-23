# Search Architect (COA) details by Registration No.



### &#xD;Introduction

The **Council of Architecture** is a regulatory authority under the Government of India, under the _provisions of the Architects Act, 1972_ which is charged with the responsibility of regulating the education and practice of the profession of architects throughout India besides maintaining the register of architects. All registered architects are provided with a COA Registration Number. &#x20;



### API Usecase

Using the unique COA Reg Number as input, this Signzy API can retrieve the details and particulars of the registered architect.&#x20;

**The following information is generated:**

* Email ID
* Registration Number
* Mobile number
* Validity
* Architect Name
* Qualification
* Address
* Disciplinary Action
* Address



### How to call the API

You will need to login before sending Registration number request. You are required to pass the access token received from the login call, as authorization header in the Search Architecture by Registration Number request along with Registration Number.



### API Input Guidelines

Provide the correct **COA Number**&#x20;



### Sample CURL Request

Use the following exchange parameters for Search Architecture by Registration Number

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization                 | Required | String | Access Token                  |
| ----------------------------- | -------- | ------ | ----------------------------- |
| Content-Type                  | Required | String | Application/JSON              |
| task                          | Required | String | Registration number search    |
| essentials.registrationNumber | Required | String | Architect registration number |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/coas' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "registrationNumberSearch",
    "essentials": {
        "registrationNumber": "< Architect Registration number>"
    }
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME            | DESCRIPTION                                                                                                                                                                                                                  |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                    | The final response parameters are contained here.                                                                                                                                                                            |
| result.emailId            | The email ID of the architect being searched.                                                                                                                                                                                |
| result.registrationNumber | The registration number of the architect who is being searched.                                                                                                                                                              |
| result.mobile             | The mobile number of the architect is shown by this parameter.                                                                                                                                                               |
| result.validity           | The validy of the registration number for the architect being searched.                                                                                                                                                      |
| result.architectName      | The name of the architect is displayed by this parameter.                                                                                                                                                                    |
| result.qualification      | The qualification of the registered architect is shown as output here.                                                                                                                                                       |
| result.address            | The address of the architect.                                                                                                                                                                                                |
| result.disciplinaryAction | This parameter shows the details of any disciplinary action that has been taken against the architect.                                                                                                                       |
| result.splitAddress       | This parameter distinguishes the various parts of the address of the architect into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA” |
| splitAddress.addressLine  | This parameter displays the first line of the registered address.                                                                                                                                                            |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "registrationNumber": "<Registration number to be searched for>"
    },
    "id": "617e984b7157fd10dd4ecc33",
    "patronId": "<Patron ID>",
    "task": "registrationNumberSearch",
    "result": {
        "emailId": "ar.shivinmehta@gmail.com",
        "registrationNumber": "CA/2017/82888",
        "mobile": "9646744655",
        "validity": "31/12/2028",
        "architectName": "MS. SHIVIN  MEHTA",
        "qualification": "BACHELOR OF  ARCHITECTURE",
        "address": "339, ASHOKA COLONY, OPP KALPANA CHAWLA MEDICAL COLLEGE, KARNAL, KARNAL, HARYANA -  132001",
        "disciplinaryAction": "NO",
        "splitAddress": {
            "district": [
                "KARNAL"
            ],
            "state": [
                [
                    "HARYANA",
                    "HR"
                ]
            ],
            "city": [
                "CHAK NALVI PAR (116)"
            ],
            "pincode": "132001",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "339,ASHOKA COLONY,OPP KALPANA CHAWLA MEDICAL COLLEGE"
        }
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

****

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |





&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c613c319ce8ce6f00aaa)
