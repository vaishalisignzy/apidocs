# Search Director data by DIN

### Introduction

DIN **(Director Identification Number)** is an 8**-digit unique identification number**, allotted by the Ministry of Corporate Affairs(MCA) to any person intending to be a Director or an existing director of a company.&#x20;

### API Usecase

This API would help any person to extract details of any particular director by using director's DIN. The following information will be generated.

**Information about the director**

* DIN
* Designation
* Date of appointment
* Address of director
* Name of Director
* Whether DSC required
* DSC expiry date
* PAN number of director
* Number of companies
* Father's name of the Director
* D.O.B of the director



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
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/organizations' \
--header 'Authorization: <AUTH>' \
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
    "accessToken": "<Token>",
    "id": "616832a418d6ad764a315622",
    "patronId": "<Patron ID>",
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
        "din": "00031051"
    }
}'
```
{% endtab %}
{% endtabs %}



{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name                          | Description                                                                                                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result.numberofMembers                  | Number of members in the company                                                                                                                                                                                                |
| result.subCategory                      | Whether the company is a Government or Non-Govt company                                                                                                                                                                         |
| result.class                            | The class to which the company belongs.                                                                                                                                                                                         |
| result.companyType                      | The type of company - Public or Private limited.                                                                                                                                                                                |
| result.companyName                      | Registered name of the company                                                                                                                                                                                                  |
| result.paidUpCapital                    | Amount of money a company receives in exchange for a share of the company                                                                                                                                                       |
| result.authorisedCapital                | The maximum amount of share capital that the company is authorized                                                                                                                                                              |
| result.whetherListed                    | Whether listed on Exchange ( NSE, BSE) or not                                                                                                                                                                                   |
| result.dateofIncorporation              | Date on which company got incorporated                                                                                                                                                                                          |
| result.registrationNumber               | Registration number of the company got from ROC                                                                                                                                                                                 |
| result.registeredAddress                | The Registered address of the company                                                                                                                                                                                           |
| result.category                         | Which type of limited company it is whether Limited by shares or Limited by Guarantee                                                                                                                                           |
| result.cin                              | CIN (Corporate Identification Number) of the company                                                                                                                                                                            |
| result.rocOffice                        | Registrar to which company comes under                                                                                                                                                                                          |
| result.noOfDirectors                    | Number of directors the company has                                                                                                                                                                                             |
| result.addressOtherThanRegisteredOffice | Any other registered address of the company                                                                                                                                                                                     |
| result.emailId                          | Registered email Id of the company with the ROC                                                                                                                                                                                 |
| result.splitAddress                     | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, Pincode and country. For the country category, acceptable values are “IN”, ”IND” and ”INDIA”. |
| result.natureOfBusiness                 | The nature of the business conducted by the company. For ex: Supplier of Services.                                                                                                                                              |
| result.activeCompliance                 |                                                                                                                                                                                                                                 |
| result.status                           | Whether a company is in operation or not                                                                                                                                                                                        |
| result.statusForEfiling                 | Whether company is filing its return on regular basis or not with ROC. If yes than Active else Inactive                                                                                                                         |
|                                         |                                                                                                                                                                                                                                 |
{% endtab %}

{% tab title="API Response" %}
```
{
    "target": "Organization",
    "itemId": "616a4da218d6ad764a315911",
    "accessToken": "tv68tvs6ah0es6fb82808ra4vfkeu6h9q",
    "task": "quickSearchByDin",
    "id": "616a53ee18d6ad764a315924",
    "essentials": {
        "din": "00031051"
    },
    "result": {
        "din": "00031051",
        "designation": "DIRECTOR",
        "dateOfAppointment": "01/03/2004",
        "address": "1901, FLOOR-19, STERLING TOWER, HARISHCHANDRA GOREGAONKAR MARG, GAMDEVI LANE, GRANT RO AD MUMBAI 400007 MH IN",
        "name": "ANANT JAIVANT TALAULICAR",
        "whetherDscRegistered": "YES",
        "dscExpiryDate": "18/10/2018",
        "fatherName": "JAIVANT TALAULICAR",
        "dob": "11/07/1961",
        "noOfCompanies": "11",
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
            "pincode": "400007",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "1901,FLOOR-19,STERLING TOWER,HARISHCHANDRA GOREGAONKAR MARG,GAMDEVI LANE,GRANT RO AD"
        }
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/237e97585fba5da6bf15)
