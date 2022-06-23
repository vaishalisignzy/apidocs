# Search by Voter ID (EPIC No.)

### &#xD;Introduction

EPIC full form is <mark style="color:yellow;">**Electoral photo identity card**</mark>. Using the Epic number and state to which the voter belongs, the details of the voter can be retrieved.



### API Usecase

This API uses just the Epic number and state of the user and provides the details of that particular user. It helps in auto-generating the details for the user without having to manually provide the information.

The search by Epic number service returns basic details like:&#x20;

* Name&#x20;
* District
* State Name
* Father's Name
* Gender

### How to call the API

You will need to login before sending a search request. You are required to pass the access token received from the login call, as an authorization header in the Voter ID search request along with the Epic number.



### API Input Guidelines

* EPIC number of the voter
* State name of the voter

### <mark style="color:purple;">Sample CURL Request and Reponse</mark>

{% tabs %}
{% tab title="Input Parameters" %}
| Input Parameters      | Description                                                        | Required/ Optional |
| --------------------- | ------------------------------------------------------------------ | ------------------ |
| essentials            | Contains the essential output data                                 | Required           |
| essentials.epicNumber | This parameter returns the voter ID/ Epic number of the individual | Required           |
| essentials.state      | The state to which the voter ID belongs to.                        | Required           |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/voteridsearches' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "essentials": {
        "epicNumber": "<EPIC Number of voter>",
        "state": "<State to be search for>"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**API Response**</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| **PARAMETER NAME**    | **DESCRIPTION**                                                                  |
| --------------------- | -------------------------------------------------------------------------------- |
| essentials            | Contains the essential output data                                               |
| essentials.epicNumber | This parameter returns the voter ID/ Epic number of the individual               |
| essentials.state      | The state to which the voter ID belongs to.                                      |
| essentials.id         | This parameter contains the access token that was received from identity request |
| essentials.patronId   | Contains the patron ID                                                           |
| result                | This holds final result parameters of the response                               |
| result.name           | The name associated with the epic number is held here                            |
| result.dob            | This parameter holds the date of birth of the voter ID holder.                   |
| result.district       | This parameter holds the district information of the registered address.         |
| result.state          | This parameter holds the state information of the registered address.            |
| result.fatherName     | The father's name of the epic number holder                                      |
| result.gender         | The gender information of the voter card holder                                  |
{% endtab %}

{% tab title="API Response" %}
```
{
    "essentials": {
        "epicNumber": "SCG3050XXX",
        "state": "West Bengal"
    },
    "id": "6147a97df0e8db4b731802ca",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "name": "SUMAN SINGH",
        "dob": "",
        "district": "SOUTH 24 PARGANAS",
        "state": "WEST BENGAL",
        "fatherName": "XXXX SINGH",
        "gender": "Female"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/f6dbb0337cdb3ee17f40)

**Valid State and Union Territory List**

1 ) Andaman and Nicobar Islands\
2 ) Andhra Pradesh\
3 ) Arunachal Pradesh\
4 ) Assam\
5 ) Bihar\
6 ) Chandigarh\
7 ) Chhattisgarh\
8 ) Dadra and Nagar\
9 ) Diu-Daman\
10 ) Delhi\
11 ) Goa\
12 ) Gujarat\
13 ) Haryana\
14 ) HimachalPradesh\
15 ) JammuKashmir\
16 ) Jharkhand\
17 ) Karnataka\
18 ) Kerala\
19 ) Lakshadweep\
20 ) Madhya Pradesh\
21 ) Maharashtra\
22 ) Manipur\
23 ) Meghalaya\
24 ) Mizoram\
25 ) Nagaland\
26 ) Odisha\
27 ) Puducherry\
28 ) Punjab\
29 ) Rajasthan\
30 ) Sikkim\
31 ) TamilNadu\
32 ) Telangana\
33 ) Tripura\
34 ) Uttar Pradesh\
35 ) Uttarakhand\
36 ) West Bengal

****

**VoterID Search Result Scenarios**

1. Provided Epic Number not found
   * Provided Epic Number not found.
   * The provided Epic Number is not updated in the government database.
   * The underlying government data source is having some issues at this moment.
