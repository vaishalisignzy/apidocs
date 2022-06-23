# GSTR Initiation Flow - Get OTP Request

### Introduction

GSTR or GST return is a document that will contain all the details of your sales, purchases, tax collected on sales (output tax), and tax paid on purchases (input tax). Once you file GST returns, you will need to pay the resulting tax liability (money that you owe the government).&#x20;

### API Usecase

The GSTR OTP Request service is used to take the GSTIN of the business and the username of the business owner as input and generate a unique One Time Password (OTP) for the particular GSTIN (which will later serve as the App Key when requesting Auth Token, we will discuss that later)

### How to call the API

You will need to login before sending a GSTR OTP Request. You are required to pass the access token received from the login call, as an authorization header in the GSTR OTP Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
*   Username registered on **GST Portal**

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTR OTP Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization       | Required | String  | Access Token                                      |
| ------------------- | -------- | ------- | ------------------------------------------------- |
| Content-Type        | Required | String  | Application/JSON                                  |
| task                | Required | String  | Type of task - Get OTP                            |
| essentials          | Required | Object  | This parameter contains the essential input data. |
| essentials.gstn     | Required | String  | Contains GST number of the organisation           |
| essentials.username | Required | String  | Username from GST portal credentials              |
{% endtab %}

{% tab title="CURL Request" %}
```
 {
    "task" : "getOtp",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username.."
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
| task                | The type of task to be performed by the API - "getOTP".                     |
| essentials          | This parameter contains the essential input data.                           |
| essentials.gstin    | The unique GST identification number is displayed here.                     |
| essentials.username | This parameter displays the username.                                       |
| id                  | Contains the access token that was received during login request.           |
| patronId            | The unique userId that was assigned during login request is displayed here. |
| result              | The final response parameters are contained here.                           |
| result.message      | This parameter displays the status message.                                 |
| result.appKey       | This parameter contains the unique app key.                                 |
{% endtab %}

{% tab title="Response" %}
```
{
    "task" : "getOtp",
    "essentials": {
        "gstin": "..gstin..",
        "username": "..username.."
    },
    "id": "...accessToken...",
    "patronId": "...patronId...",
    "result":{
        "message": "..message..",
        "appKey": "..appKey.."
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
