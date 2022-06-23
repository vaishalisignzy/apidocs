# Search AML/CFT data by Individual/Company Name

### Introduction

Anti-Money Laundering/Combating the Financing of Terrorism (AML/CFT) software is used in the finance and legal industries to meet the legal requirements for various financial institutions and other regulated entities to prevent or report money laundering activities. AML/CFT software, when effectively implemented, mitigates the adverse effects of criminal economic activity and maintains integrity and stability in financial markets.

### API Usecase

Signzy has developed its AML/CFT Basic Search API keeping in mind the regulatory and compliance norms of the various banking sectors and financial markets. Using basic details of the culprit/culprits involved, the service can compare against existing government criminal records and blacklists to identify suspicious activity.

### How to call the API

You are required to pass the access token received from the login call, as authorization header in the AML/CFT Basic Search request along with other parameters.

### API Input Guidelines

We should give the DIN number of individual or CIN of company.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                                                      |
| -------------- | ---------------------------------------------------------------- |
| task           | Type of task - basic Search                                      |
| essentials     | Contains request data as JSON object                             |
| name           | Name of the individual/organization                              |
| type           | Whether individual/organization records                          |
| yob            | Year of birth                                                    |
| country        | Country to which the individual/organisation belongs             |
| aliasArray     | Array containing the alias names for the individual/organisation |
| cin            | CIN no of a company                                              |
| din            | Din no of any individual                                         |
{% endtab %}

{% tab title="Sample CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/amlcfts' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{"task":"directorNegativeList","essentials":{"din":"08163212"}}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
| Parameter Name                   | Description                                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| id                               | The access token received during login request.                                                                                |
| patronId                         | This parameter is returned as userId parameter of login request.                                                               |
| result                           | This contains the final response parameters to be displayed for output.                                                        |
| scores                           | This parameter assigns scores on the basis of match against each parameter searched in the database.                           |
| scores.nameMatch                 | This parameter checks whether the name of an individual/organization matches with any entry in the database.                   |
| scores.dobMatch                  | This parameter checks whether the dob of an individual matches with any entry in the database.                                 |
| scores.countryMatch              | This parameter checks whether the country of an individual/organization matches with any entry in the database.                |
| scores.zipcodeMatch              | This parameter checks whether the zipcode in the address of an individual/organization matches with any entry in the database. |
| scores.aliasArrayMatch           | This parameter checks whether the list of aliases of an individual/organization matches with any entry in the database.        |
| scores.identificationNumberMatch | This parameter checks whether the identification number of an individual/organization matches with any entry in the database.  |
| scores.searchTextMatch           | This parameter checks for any text match in the database.                                                                      |
| details                          | This parameter displays any particular details in the database.                                                                |
| relevance                        | This parameter verifies for relevance against the individual/entity being searched in the database.                            |
| overallScore                     | The overall score against an individual/entity match that was being searched in the database.                                  |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "essentials": {
        "din": "08163212"
    },
    "id": "61448692f6d4030eae05438d",
    "patronId": "614097a1f6d4030eae049781",
    "task": "directorNegativeList",
    "result": {
        "defaulterList": {
            "found": "false",
            "data": []
        },
        "dormantList": {
            "found": "false",
            "data": []
        }
    }
}
```
{% endtab %}
{% endtabs %}

### HTTP Response Codes

| Status Code | Error Message               | Possible Fix                   |
| ----------- | --------------------------- | ------------------------------ |
| 200         | Successful                  | Nothing to fix                 |
| 400         | Missing or Invalid data     | Check all the input parameters |
| 401         | Authorization Required      | Check Authorization Header     |
| 404         | No method to handle request | Check URL endpoint of API      |
| 422         | Unprocessable Entity        | Notify our support team        |
