# Search Entity Discrepancy details

### &#xD;Introduction

There might be times when there is a discrepancy in any details pertaining to the net sales and purchases of GSTR-1 or 2A with GSTR-3B. In such cases, the Entity Discrepancy Request API does a comparative analysis of the required documents to check whether there is any dispute between the reported amount and the government calculated amount.

### API Usecase



### How to call the API

You will need to login before sending Entity Discrepancy Request. You are required to pass the access token received from the login call, as authorization header in the Entity Discrepancy Request along with other parameters.



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
| PARAMETERS            | DESCRIPTION                                                                      |
| --------------------- | -------------------------------------------------------------------------------- |
| essentials            | This parameter contains the essential data for output.                           |
| essentials.gstin      | GST Number of the organization                                                   |
| essentials.sername    | Username of your GST Portal Credentials                                          |
| essentials.authToken  | AuthToken received in the authToken request                                      |
| essentials.appKey     | APP Key received in the OTP request                                              |
| essentials.sek        | Secret Key                                                                       |
| essentials.retPeriod  | Return Period for which Discrepancy has to be fetched. (Eg 03/2018)              |
| id                    | This contains the auth token returned during login request.                      |
| patronId              | This parameter is returned as userId parameter of login request.                 |
| result                | This parameter contains the final response parameters to be displayed as output. |
| result.sale           | This parameter contains the sale details for the dealer/business owner.          |
| sale.status           | The current status of the discrepancy,if any, for sales.                         |
| sale.gstr1Amount      | The amount for GSTR1 to be verified for discrepancy is displayed here.           |
| sale.gstr3bAmount     | The amount for GSTR3B to be verified for discrepancy is displayed here.          |
| result.purchase       | This parameter contains the purchase details for the dealer/business owner.      |
| purchase.status       | The current status of the discrepancy, if any, for purchases.                    |
| purchase.gstr2aAmount | The amount for GSTR2A to be verified for discrepancy is displayed here.          |
| purchase.gstr3bAmount | The amount for GSTR3B to be verified for discrepancy is displayed here.          |
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
        "sale" : {
            "status" : "..status..",
            "gstr1Amount" : "..gstr1Amount..",
            "gstr3bAmount" : "..gstr3bAmount.."
        },
        "purchase" : {
            "status" : "..status..",
            "gstr2aAmount" : "..gstr2aAmount..",
            "gstr3bAmount" : "..gstr3bAmount.."
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/6bc30af9561565009905)
