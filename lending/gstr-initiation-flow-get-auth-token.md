# GSTR Initiation Flow - Get Auth Token

### Introduction

GSTR or GST return is a document that will contain all the details of your sales, purchases, tax collected on sales (output tax), and tax paid on purchases (input tax). Once you file GST returns, you will need to pay the resulting tax liability (money that you owe the government).&#x20;

### API Usecase

The GSTR AuthToken request API uses the username and GSTIN of the business user as well as the OTP received on Mobile and APP Key received in the OTP request to generate a unique Auth Token which will be utilised later for further processes involving GSTR.

### How to call the API

You will need to login before sending GSTR AuthToken Request. You are required to pass the access token received from the login call, as authorization header in the GSTR AuthToken Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **OTP**&#x20;
*   **App key r**eceived from **** [GSTR Initiation Flow](gstr-initiation-flow-get-otp-request.md)

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTR AuthToken Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization       | Required | String  | Access Token                                      |
| ------------------- | -------- | ------- | ------------------------------------------------- |
| Content-Type        | Required | String  | Application/JSON                                  |
| task                | Required | String  | Type of task - Get Auth Token                     |
| essentials          | Required | Object  | This parameter contains the essential input data. |
| essentials.gstin    | Required | String  | GST Number of the organization                    |
| essentials.username | Required | String  | Username from GST portal credentials              |
| essentials.otp      | Required | String  | OTP Received on your mobile                       |
| essentials.appKey   | Required | String  | APP Key received in the OTP request               |
{% endtab %}

{% tab title="CURL Request" %}
```
 {
    "task" : "getAuthToken",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "otp": "..otp..",
        "appKey": "..appKey.."
    }
  }
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME      | DESCRIPTION                                                                 |
| ------------------- | --------------------------------------------------------------------------- |
| task                | The type of task to be performed by the API - "getAuthToken".               |
| essentials          | This parameter contains the essential input data.                           |
| essentials.gstin    | The unique GST identification number is displayed here.                     |
| essentials.username | This parameter displays the username.                                       |
| essentials.otp      | The otp received during OTP Request is displayed here.                      |
| essentials.appKey   | This parameter contains the unique app key.                                 |
| id                  | Contains the access token that was received during login request.           |
| patronId            | The unique userId that was assigned during login request is displayed here. |
| result              | The final response parameters are contained here.                           |
| result.message      | This parameter displays the status message.                                 |
| result.authToken    | The auth token is displayed by this parameter.                              |
| result.expiry       | The parameter shows the expiry time for the received auth token.            |
| result.sek          | This parameter contains the secret key for the request.                     |
{% endtab %}

{% tab title="Response" %}
```
{
    "task" : "getAuthToken",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username..",
        "otp": "..otp..",
        "appKey": "..appKey.."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result":{
        "message": "...message...",
      "authToken": "...authToken...",
      "expiry": ...expiry...,
      "sek": "...sek..."
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/1fdd2cd43e55b3d87d1e)
