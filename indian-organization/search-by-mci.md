# Search by MCI

### &#xD;Introduction

The MCI is an acronym for the <mark style="color:orange;">Medical Council of India</mark> and this Council grants recognition of medical qualifications, gives accreditation to medical schools, grants registration to medical practitioners, and monitors medical practice in India. Each member is issued with a unique MCI registration number.

### API Usecase

The Search companies by MCI service uses the registration number along with the state and qualification year of the member to identify and retrieve the unique details and particulars of the member.

**The following information is generated:**

* Name
* Permanent Address
* Date of Registration

### How to call the API

You will need to login before sending the registration number request. You are required to pass the access token received from the login call, as an authorization header in the MCI request along with Registration Number, State Medical Council and Qualification Year.

### API Input Guidelines

Provide the following details:

* Registration Number
* Qualification Year
* State Medical Council
* Year of Registration

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for MCI based search

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
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/mcis' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "registration_no": "<Registration Number>",
        "qualification_year": "<Year of Qualification>",
        "state_medical_council": "<State of Medical Council>",
        "year_of_registration": "<Year of Registration>",
        "name": "<Name>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}


| PARAMETER NAME                     | DESCRIPTION                                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------------------------- |
| essentials                         | This parameter contains the essential data for output.                                            |
| essentials.registration\_no        | The registration number of the MCI member is displayed here.                                      |
| essentials.state\_medical\_council | This parameter displays the name of the state medical council to which the MCI member belongs to. |
| essentials.qualification\_year     | The qualification year of the member is displayed here.                                           |
| id                                 | This contains the access token received during login request.                                     |
| patronId                           | This parameter is returned as userId parameter of login request.                                  |
| result                             | The final response parameters to be displayed are contained here.                                 |
| result.name                        | The name of the MCI member doctor.                                                                |
| result.date\_of\_reg               | The date of registration with the MCI is displayed here.                                          |
| result.permanent\_address          | The permanent address of the doctor is shown here.                                                |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "registration_no": "<Registration Number>",
        "qualification_year": "<Year of Qualification>",
        "state_medical_council": "<State of Medical Council>",
        "year_of_registration": "<Year of Registration>",
        "name": "<Doctor's Name>"
    },
    "id": "<Request ID>",
    "patronId": "<Patron ID>",
    "result": {
        "name": "<Doctor's Name>",
        "permanent_address": "<Address of Doctor>",
        "date_of_reg": "<Date of Registration>"
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



<mark style="color:orange;">**Valid Medical Council List**</mark>

1 ) Gujarat Medical Council\
2 ) Goa Medical Council\
3 ) Maharashtra Medical Council\
4 ) Karnataka Medical Council\
5 ) West Bengal Medical Council\
6 ) Bombay Medical Council\
7 ) Bihar Medical Council\
8 ) Haryana Dental & Medical Councils\
9 ) Uttar Pradesh Medical Council\
10 ) Assam Medical Council\
11 ) Medical Council of India\
12 ) Madhya Pradesh Medical Council\
13 ) Delhi Medical Council\
14 ) Tamil Nadu Medical Council\
15 ) Travancore - Cochin Medical Council, Trivandrum\
16 ) Orissa Council of Medical Registration\
17 ) Travancore Cochin Medical Council\
18 ) Rajasthan Medical Council\
19 ) Jharkhand Medical Council\
20 ) Hyderabad Medical Council\
21 ) Uttarakhand Medical Council\
22 ) Jammu & Kashmir Medical Council\
23 ) Andhra Pradesh Medical Council\
24 ) Himanchal Pradesh Medical Council\
25 ) Punjab Medical Council\
26 ) Chattisgarh Medical Council\
27 ) Madras Medical Council\
28 ) Sikkim Medical Council\
29 ) Mysore Medical Council\
30 ) Arunachal Pradesh Medical Council\
31 ) Vidharba Medical Council\
32 ) Bhopal Medical Council\
33 ) Mahakoshal Medical Council\
34 ) Tripura State Medical Council\
35 ) Dental Council of India\


&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/20970a7db1434197a3dc)
