# Search Entity Gross Profit details



### Introduction

As the name suggests, the Entity Gross Profit Request API is used to retrieve the details associated with the business after the deduction of taxes for the returned period entered by the user.&#x20;

### API Usecase



### How to call the API

You will need to login before sending Entity Gross Profit Request. You are required to pass the access token received from the login call, as authorization header in the Entity Gross Profit Request along with other parameters.



### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](../gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](../gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for Entity Gross Profit Request

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
| PARAMETER NAME     | DESCRIPTION                                                               |
| ------------------ | ------------------------------------------------------------------------- |
| result             | This contains the final response parameters.                              |
| result.grossProfit | This parameter displays the gross profit for the searched period of time. |
{% endtab %}

{% tab title="Response" %}
```
 {
    "result":{
        "grossProfit" : "..grossProfit.."
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





&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c1cd42843aec43c0f1be)

\
