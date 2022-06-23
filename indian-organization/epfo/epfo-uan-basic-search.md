# EPFO UAN Basic Search(API 404)





### Introduction

UAN stands for **Universal Account Number**. EPFO allots a **12 Digit UAN** for every individual who becomes a member of EPFO. _The UAN remains the same throughout life_, although the Member ID/EPF Account numbers change whenever the employee changes jobs.&#x20;

### API Usecase

The EPFO UAN Basic Search API uses the employee UAN number to retrieve all the organisational details as well as the employee’s account details.

**The following information is generated:**

* Establishment ID
* Establishment Name
* Validity Status
* Establishment Status
* Establishment Details
* PAN Status
* Primary Business Activity
* ESIC Code
* Ownership Type
* Date of the setup of establishment
* Detailed Address
* EPFO Office Name
* EPF Office address&#x20;
* EPFO Zone
* EPFO Region
* Employee name search response



### How to call the API

You will need to login before sending firm number request. You are required to pass the access token received from the login call, as authorization header in the EPFO UAN Basic Search request along with UAN.



### API Input Guidelines

Provide correct **UAN Number** and **Password of EPFO account**, that's provided by the **EPFO**



### Sample CURL Request

Use the following exchange parameters for EPFO UAN Basic Search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization            | Required | String | Access Token                     |
| ------------------------ | -------- | ------ | -------------------------------- |
| Content-Type             | Required | String | Application/JSON                 |
| task                     | Required | String | Employee name search             |
| essentials.uan           | Required | String | UAN of the employee              |
| essentials.employeeName  | Required | String | Employee name to be searched for |
| essentials.employeeMonth | Required | String |                                  |
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


| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                     |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                          | The final response parameters are contained here.                                                                                                                                                                               |
| result.pfNumbers                                | This parameter displays the PF numbers of the employees of the organization.                                                                                                                                                    |
|                                                 |                                                                                                                                                                                                                                 |
| result.establishmentId                          | The establishment ID for which EPFO details are being searched.                                                                                                                                                                 |
| result.establishmentName                        | The name of the establishment.                                                                                                                                                                                                  |
| result.validityStatus                           | This parameter displays the details of the validity status like establishment status, portal registration status and post coverage status.                                                                                      |
| result.establishmentStatus                      | The details about the establishment coverage are displayed here like exemption, working, coverage section, actionable status and date of coverage.                                                                              |
| result.establishmentDetails                     | This parameter displays the details of the establishment registered under EPFO.                                                                                                                                                 |
| establishmentDetails.panstatus                  | The pan status of the establishment.                                                                                                                                                                                            |
| establishmentDetails.sectionApplicable          | The section of EPFo that is applicable to the establishment being searched.                                                                                                                                                     |
| establishmentDetails.primaryBusinessActivity    | The primary business activity of the establishment.                                                                                                                                                                             |
| establishmentDetails.esicCode                   | The ESIC code assigned to the establishment.                                                                                                                                                                                    |
| establishmentDetails.ownershipType              | The ownership type of the establishment is displayed by this parameter.                                                                                                                                                         |
| establishmentDetails.dateOfSetupOfEstablishment | The date of setup of the establishment as registered with EPFO.                                                                                                                                                                 |
| establishmentDetails.address                    | The address of the establishment registered under EPFO.                                                                                                                                                                         |
| establishmentDetails.pincode                    | The pincode of the establishment address.                                                                                                                                                                                       |
| establishmentDetails.city                       | The city of the establishment address.                                                                                                                                                                                          |
| establishmentDetails.district                   | The district of the establishment address.                                                                                                                                                                                      |
| establishmentDetails.state                      | The state of the establishment address.                                                                                                                                                                                         |
| establishmentDetails.country                    | The country of the establishment address.                                                                                                                                                                                       |
| establishmentDetails.epfoOfficeName             | The EPFO office name under which establishment is registered.                                                                                                                                                                   |
| establishmentDetails.epfoOfficeAddress          | The EPFO office address under which establishment is registered.                                                                                                                                                                |
| establishmentDetails.zone                       | The EPFO zone under which establishment is registered.                                                                                                                                                                          |
| establishmentDetails.region                     | The EPFO region under which establishment is registered.                                                                                                                                                                        |
| establishmentDetails.splitAddress               | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
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

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |







