# Search Court Case List by Company Name

### Introduction

The Case List API is similar to the Case Count API with one key difference. While the Case Count API only shows the number of cases filed against an individual name, it does not specify whether all the cases are against one individual or multiple individuals. The Case List API lists all the cases with case reference ID and case details, thereby providing much more clarity.&#x20;

### API Usecase

This unique service by Signzy helps identify the case records of an individual and prevents any misuse of financial system software by malicious users with existing criminal records.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Court Cases (Case List) request along with other parameters.

### API Input Guidelines

We should pass the individual details like name address, etc.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name     | Required/ optional | Description                                                                         |
| ------------------ | ------------------ | ----------------------------------------------------------------------------------- |
| task               | Required           | Type of task - case count                                                           |
| essentials         | Required           | Contains request data as JSON object                                                |
| essentials.name    | Required           | Name of a person                                                                    |
| essentials.stateId | optional           | State of where case registered                                                      |
| essentials.cityId  | optional           | <p>City name of the individual/organization<br>whose records are being searched</p> |
| type               | Required           | entity or organization                                                              |
{% endtab %}

{% tab title="Sample CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/courtcases' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{
    "task": "caseList",
    "essentials": {
        "name": "Signzy",
        "address": "",
        "type": "entity",
        "fatherName": "",
        "state": "UP",
        "caseFilter": "",
        "caseCategory": "",
        "caseType": "",
        "caseYear": ""
    }
}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                                   | DESCRIPTION                                                                                                            |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| task                                             | The type of task performed - caseCount                                                                                 |
| essentials                                       | Contains the essential output data.                                                                                    |
| essentials.name                                  | The name of the individual/organization is displayed by this parameter.                                                |
| essentials.stateId                               | This parameter displays the state name of the  individual/organization whose records are being searched.               |
| essentials.cityId                                | This parameter displays the city name of the individual/organization whose records are being searched.                 |
| id                                               | This parameter returns the access token (returned as id field of login request).                                       |
| patronId                                         | This parameter is returned as userId parameter of login request.                                                       |
| result                                           | The final response parameters are contained here.                                                                      |
| result.totalCaseCount                            | This parameter shows the total number of cases registered against the name being searched.                             |
| result.caseCountDistribution                     | The details of the various cases registered against the searched name and the details of the court are displayed here. |
| caseCountDistribution.supremeCourt               | The cases registered in the Supreme Court of India are shown here.                                                     |
| caseCountDistribution.highCourt                  | The cases registered in the High Court are displayed here.                                                             |
| caseCountDistribution.districtCourt              | The cases registered in the district Court are displayed here.                                                         |
| caseCountDistribution.consumerCourt              | The cases registered with the Consumer court are displayed by this parameter.                                          |
| caseCountDistribution.incomeTaxAppellateTribunal | The cases registered with the Income Tax Appellate Tribunal are shown here.                                            |
| caseCountDistribution.nationalCompanyLawTribunal | The cases that are registered with the national Company Law Tribunal are displayed here.                               |
| caseCountDistribution.debtRecoveryTribunal       | The cases registered with the debt recovery Tribunal are shown here.                                                   |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "essentials": {
        "name": "signzy",
        "address": "",
        "type": "entity",
        "fatherName": "",
        "state": "",
        "caseFilter": "",
        "caseCategory": "",
        "caseType": "",
        "caseYear": "",
        "task": "caseList"
    },
    "id": "614499f2f6d4030eae0547d6",
    "patronId": "614097a1f6d4030eae049781",
    "task": "caseList",
    "result": {
        "cases": []
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
&#x20;You can pass either of **cityId** or **stateId.** Both **** in the same request is not allowed.

Please [Click here](https://signzy.xyz/cdn/files/states.xlsx) to the sheet containing the valid values for state list

Please [Click here](https://signzy.xyz/cdn/files/cities.xlsx) to the sheet containing the valid values for city list
{% endhint %}

### HTTP Response Codes

| Status Code | Error Message               | Possible Fix                   |
| ----------- | --------------------------- | ------------------------------ |
| 200         | Successful                  | Nothing to fix                 |
| 400         | Missing or Invalid data     | Check all the input parameters |
| 401         | Authorization Required      | Check Authorization Header     |
| 404         | No method to handle request | Check URL endpoint of API      |
| 422         | Unprocessable Entity        | Notify our support team        |
