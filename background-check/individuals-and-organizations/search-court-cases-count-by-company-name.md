# Search Court Cases Count by Company Name

### Introduction

The Case Count API is another section that is built in accordance with AML/CFT regulatory guidelines. The purpose of this API is to search and retrieve any records and relevant details of financial/economic court cases/offences found against an individual.

### API Usecase

The search API is based on city or state-based records and can identify any matches with any cases registered in the same. Upon a successful match, the API will display the number of cases filed against the individual as well as the type of case filed.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Court Cases (Case Count) request along with other parameters.

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
        "name": "ankur pandey",
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
        "name": "ankur pandey",
        "address": "",
        "type": "entity",
        "fatherName": "",
        "state": "BR",
        "caseFilter": "",
        "caseCategory": "",
        "caseType": "",
        "caseYear": "",
        "task": "caseList"
    },
    "id": "61449823f6d4030eae054738",
    "patronId": "614097a1f6d4030eae049781",
    "task": "caseList",
    "result": {
        "cases": [
            {
                "name": "ANKUR KUMAR PANDEY",
                "party": "",
                "petitioner": "",
                "matchType": "",
                "score": 14.445649,
                "subject": "",
                "pdfUrl": "",
                "address": "",
                "rawAddress": "",
                "addressStreet": "",
                "addressState": "",
                "addressTaluka": "",
                "addressDistrict": "",
                "addressPincode": "",
                "stateName": "Bihar",
                "districtCode": 23,
                "stateCode": 8,
                "districtName": "Gopalganj",
                "source": "ecourt",
                "uniqueCaseId": "fce1ed7c2180d9e9f1a41ad933a26a27",
                "caseNumber": "202000005292020",
                "filingNo": "897/2020    18-02-2020",
                "caseCode": "202000005292020",
                "registrationNumber": "529/2020     18-02-2020",
                "firNumber": "39",
                "type": 1,
                "caseType": "REG. CRI. CASE",
                "underAct": "Indian Penal Code",
                "underSections": "341,323,324,379,504,506,34,",
                "natureOfDisposal": "",
                "businessCategory": "serious",
                "caseCategory": "criminal",
                "date": "",
                "firYear": "2020",
                "firstHearingDate": "16/04/2020",
                "nextHearingDate": "16/04/2020",
                "decisionDate": "",
                "caseNumberYear": "",
                "caseYear": "2020",
                "caseDecisionDate": "",
                "courtName": "CJM Div. Gopalganj",
                "courtCode": 3,
                "nameCourtNumber": "",
                "judgeCourtNo": "47-Addl. Chief Judicial Magistrate -IX",
                "purposeOfHearing": "Awated for final form / Chargesheet",
                "policeStation": "UCHAKAGAON",
                "caseStatus": "",
                "orderSummary": "The case is filed under act Indian Penal Code, under section 341,323,324,379,504,506,34, and case status is unknown",
                "riskProfile": "high",
                "cnr": "BRGO020009122020"
            }
        ]
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
