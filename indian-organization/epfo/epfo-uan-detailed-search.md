# EPFO UAN Detailed Search

### &#xD;Introduction

UAN stands for **Universal Account Number**. EPFO allots a **12 Digit UAN** for every individual who becomes a member of EPFO. _The UAN remains the same throughout life_, although the Member ID/EPF Account numbers change whenever the employee changes jobs.&#x20;

### API Usecase

The EPFO UAN Basic Search API uses the employee UAN number to retrieve all the organisational details as well as the employee’s account details.

Similar to the Basic Search API, the EPFO UAN Detailed Search service returns a more detailed report on the particulars of the employee account like bank account number, IFSC code etc. As the name suggests, the objective of this API is to provide a more detailed report of the organisation employee. The API accepts the UAN and password of the employee portal as input to generate the details.

**The following information is generated:**

* Name&#x20;
* Mobile Number
* Email ID
* Bank account number
* IFSC Code
* Aadhaar number
* UAN Number
* PF account number
* Establishment Name
* Establishment Address
* Date of joining
* PF account holder
* Member's Name
* Date of birth
* Father's spouse name
* Relationship
* Establishment split address



### How to call the API

You will need to login before sending firm number request. You are required to pass the access token received from the login call, as authorization header in the EPFO UAN Basic Search request along with UAN.



### API Input Guidelines

Provide the correct **UAN Number** and **Password of the EPFO account**, provided by the **EPFO**



### Sample CURL Request

Use the following exchange parameters for EPFO UAN Detailed Search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization       | Required | String | Access Token             |
| ------------------- | -------- | ------ | ------------------------ |
| Content-Type        | Required | String | Application/JSON         |
| task                | Required | String | UAN detailed search      |
| essentials.uan      | Required | String | UAN of the employee      |
| essentials.password | Required | String | Password of EPFO account |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/epfos' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "uanDetailed",
    "essentials": {
        "uan": "<UAN number of Employee>",
        "password": "Password of EPFO account#"
    }
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME              | DESCRIPTION                                                     |
| --------------------------- | --------------------------------------------------------------- |
| result                      | The final response parameters are displayed here.               |
| result.name                 | The name of the employee being searched.                        |
| result.mobileNo             | The mobile number of the employee.                              |
| result.emailId              | The email id of the employee registered with UAN.               |
| result.bankAccountNo        | The bank account number that is linked with UAN.                |
| result.ifsc                 | The IFSC code of the bank whose account is linked to UAN.       |
| result.aadhaarNo            | The Aadhaar number of the employee.                             |
| result.uan                  | The universal account number of the employee.                   |
| result.pfaccountNo          | The PF account number of the employee linked to UAN.            |
| result.establishmentName    | The name of the establishment to which the employee belongs.    |
| result.establishmentAddress | The address of the establishment to which the employee belongs. |
| result.dateOfJoining        | The date of joining of the  employee.                           |
| result.pfAccountHeldBy      | The PF account holder name.                                     |
| result.memberName           | The member name of the PF account (nominee).                    |
| result.dateOfBirth          | The date of birth of the PF account member.                     |
| result.fatherSpouseName     | The father or spouse name of the PF member.                     |
| result.relationship         | The member relationship with the PF account holder.             |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "uan": "<UAN number of account holder>"
    },
    "id": "617d76b37157fd10dd4ec891",
    "patronId": "<Patron ID>",
    "task": "uanDetailed",
    "result": {
        "name": "Name of EPFO accout holder",
        "mobileNo": "817824XXXX",
        "emailId": "xxxxxxx@gmail.com",
        "bankAccountNo": "",
        "ifsc": "",
        "aadhaarNo": "",
        "uan": "10156068xxxx",
        "pfaccountNo": "PUPUN17530220000010082",
        "establishmentName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED, PUNE",
        "establishmentAddress": "18 B, KUBERA BAHAR BUNGLOWS, SOC 131 2 BANER PASHAN LINK ROAD PUNE PUNE",
        "dateOfJoining": "01/01/2020",
        "pfAccountHeldBy": "PUNE",
        "memberName": "Name of EPFO accout holder",
        "dateOfBirth": "D.O.B",
        "fatherSpouseName": "<Father's/ Spouse Name>",
        "relationship": "FATHER",
        "establishmentSplitAddress": {
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
                "PUNE CITY"
            ],
            "pincode": "411008",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "18 B,KUBERA BAHAR BUNGLOWS,SOC 131 2 BANER PASHAN LINK ROAD"
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







&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/03468e2f8eed4d0d8ea1)
