# Search Entity Turn Over details

### Introduction

The Entity Turn Over Request API is used to generate the turnover amount for a particular business for a given period of time based on the GSTIN for the particular reported business. There are 4 categories for which turnover period can be selected in the API based on the time period and type of turnover required by the user:

1. Monthly Turnover
2. Composition Quarterly Turnover
3. E Commerce Monthly Turnover
4. Regular Yearly Turnover

### API Usecase



### How to call the API

You will need to login before sending Entity Turn Over Request. You are required to pass the access token received from the login call, as authorization header in the Entity Turn Over Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](../gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](../gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for Entity Turn Over Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String  | Access Token                                                                                                                         |
| -------------------- | -------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Content-Type         | Required | String  | Application/JSON                                                                                                                     |
| task                 | Required | String  | <p>What type of turnover is required (monthlyTurnover/compositionQuarterlyTurnover/<br>ecomMonthlyTurnover/regularYearlyTurnover</p> |
| essentials           | Required | Object  | This parameter contains the essential input data.                                                                                    |
| essentials.gstin     | Required | String  | GST Number of the organization                                                                                                       |
| essentials.username  | Required | String  | Username from GST portal credentials                                                                                                 |
| essentials.authToken | Required | String  | AuthToken received in the authToken request                                                                                          |
| essentials.appKey    | Required | String  | APP Key received in the OTP request                                                                                                  |
| essentials.sek       | Required | String  | Secret Key                                                                                                                           |
| essentials.retPer    | Required | String  | Return period for which details to be searched                                                                                       |
{% endtab %}

{% tab title="CURL Request" %}
```
 {
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "authToken": "..authToken..",
        "appKey": "..appKey..",
        "sek": "..sek..",
        "retPeriod": "..retPeriod..",
         "task": "monthlyTurnover/compositionQuarterlyTurnover/ecomMonthlyTurnover/regularYearlyTurnover"
    }
  }
  
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME        | DESCRIPTION                                                                                                                                                                            |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials            | This parameter contains the essential input data.                                                                                                                                      |
| essentials.gstin      | The unique GST identification number is displayed here.                                                                                                                                |
| essentials.username   | This parameter displays the username.                                                                                                                                                  |
| essentials.authToken  | This parameter contains the auth token that was received during auth token request.                                                                                                    |
| essentials.appKey     | This parameter contains the unique app key received during OTP request.                                                                                                                |
| essentials.sek        | This parameter contains the secret key for the request.                                                                                                                                |
| essentials.retPeriod  | This parameter displays the return period.                                                                                                                                             |
| essentials.task       | This parameter denotes the type of turnover task performed and is usually one of the following -monthlyTurnover/compositionQuarterlyTurnover/ecomMonthlyTurnover/regularYearlyTurnover |
| id                    | Contains the access token that was received during login request.                                                                                                                      |
| patronId              | The unique userId that was assigned during login request is displayed here.                                                                                                            |
| result                | The final response parameters are contained here.                                                                                                                                      |
| result.turnoverAmount | This parameter displays the total turnover amount as per the type of task performed. (Monthly, Yearly etc.)                                                                            |
| result.information    | This parameter contains the additional information about the request, if any.                                                                                                          |
{% endtab %}

{% tab title="Response" %}
```
 {
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "authToken": "..authToken..",
        "appKey": "..appKey..",
        "sek": "..sek..",
        "retPeriod": "..retPeriod..",
        "task": "monthlyTurnover/compositionQuarterlyTurnover/ecomMonthlyTurnover/regularYearlyTurnover"
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result":{
        "turnoverAmount" : "...turnoverAmount...",
        "information" : "...information..."

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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/636a3f8aeffe93cc5889)

\
