# Search Entity Delinquency details

### Introduction

The Entity Delinquency Request API is used whenever there is a need to retrieve the details about the late fees/penalties for a particular business. The API generates the status as well as the amount for late fees and/or penalties.

### API Usecase



### How to call the API

You will need to [login](https://docs-staging.signzy.tech/) before sending Entity Delinquency Request. You are required to pass the access token received from the login call, as authorization header in the Entity Delinquency Request along with other parameters.



### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](../gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](../gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for Entity Delinquency Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String | Access Token                                                         |
| -------------------- | -------- | ------ | -------------------------------------------------------------------- |
| Content-Type         | Required | String | Application/JSON                                                     |
| essentials           | Required | Object | This parameter contains the essential input data.                    |
| essentials.gstin     | Required | String | GST Number of the organization                                       |
| essentials.username  | Required | String | Username from GST portal credentials                                 |
| essentials.authToken | Required | String | AuthToken received in the authToken request                          |
| essentials.appKey    | Required | String | APP Key received in the OTP request                                  |
| essentials.sek       | Required | String | Secret Key                                                           |
| essentials.retPer    | Required | String | Return Period for which Gross Profit has to be fetched. (Eg 03/2018) |
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
        "retPeriod": "..retPeriod.."
    }
  }

```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME       | DESCRIPTION                                                                         |
| -------------------- | ----------------------------------------------------------------------------------- |
| essentials           | This parameter contains the essential input data.                                   |
| essentials.gstin     | The unique GST identification number is displayed here.                             |
| essentials.username  | This parameter displays the username.                                               |
| essentials.authToken | This parameter contains the auth token that was received during auth token request. |
| essentials.appKey    | This parameter contains the unique app key received during OTP request.             |
| essentials.sek       | This parameter contains the secret key for the request.                             |
| essentials.retPeriod | This parameter displays the return period.                                          |
| id                   | Contains the access token that was received during login request.                   |
| patronId             | The unique userId that was assigned during login request is displayed here.         |
| result               | The final response parameters are contained here.                                   |
| result.interest      | This parameter displays the interest incurred as part of delinquency.               |
| result.lateFee       | This parameter displays the late fee incurred on the total amount.                  |
| result.penalty       | This parameter shows the total penaly incurred on the final amount.                 |
| result.status        | The status message for the delinquency request is displayed here.                   |
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
        "retPeriod": "..retPeriod.."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result":{
        "interest" : "..interest..",
        "lateFee" : "..lateFee..",
        "penalty" : "..penalty..",
        "status" : "..status..."


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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/ff4c551bba798d2a4c10)
