# Search GSTR1 Summary details

### &#xD;Introduction

GSTR-1 is a monthly or quarterly return that should be filed by every registered dealer/business owner who is registered under GST. It contains details of all outward supplies i.e sales.

### API Usecase

This Signzy API collects the username, GSTIN and AuthToken details along with APP Key and secret key to generate the GSTR details for the particular business like Section Number, Total Tax, Total Cess etc.

### How to call the API

You will need to login before sending GSTR1 Summary Request. You are required to pass the access token received from the login call, as authorization header in the GSTR1 Summary Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTR1 Summary Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String  | Access Token                                      |
| -------------------- | -------- | ------- | ------------------------------------------------- |
| Content-Type         | Required | String  | Application/JSON                                  |
| task                 | Required | String  | Type of task - Summary                            |
| essentials           | Required | Object  | This parameter contains the essential input data. |
| essentials.gstin     | Required | String  | GST Number of the organization                    |
| essentials.username  | Required | String  | Username from GST portal credentials              |
| essentials.authToken | Required | String  | AuthToken received in the authToken request       |
| essentials.appKey    | Required | String  | APP Key received in the OTP request               |
| essentials.sek       | Required | String  | Secret Key                                        |
| essentials.retPer    | Required | String  | Return period for which details to be searched    |
{% endtab %}

{% tab title="CURL Request" %}
```
{
    "task" : "summary",
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
| PARAMETER NAME                  | DESCRIPTION                                                                      |
| ------------------------------- | -------------------------------------------------------------------------------- |
| result                          | The final response parameters to be displayed are stored here.                   |
| result.gstin                    | The GST identification number is stored here.                                    |
| result.retPeriod                | The return period for GSTR1 is displayed here.                                   |
| result.checksum                 | This parameter is used to validate the data received from the GST Portal.        |
| result.totalRecords             | The total number of records being searched for GSTR1.                            |
| result.totalTax                 | The total tax amount to be filed is shown here.                                  |
| result.totalIgst                | The total integrated GST to be filed by the dealer/business owner.               |
| result.totalSgst                | The total state GST to be filed by the dealer/business owner.                    |
| result.totalCgst                | The total central GST to be filed by the dealer/business owner.                  |
| result.totalVal                 | The total value of taxable goods.                                                |
| result.cess                     | The total cess amount to be filed by the dealer/business owner.                  |
| result.totalDocIssued           | The total number of document types issued.                                       |
| result.totalDocCancelled        | The total number of document types cancelled.                                    |
| result.NetDocIssued             | The net amount of documents that have been issued.                               |
| result.counterPartSummary       | This parameter conveys the details located on the counterpart of the GSTR1 form. |
| counterPartSummary.ctin         | The CTIN number associated with GSTR1 form is displayed here.                    |
| counterPartSummary.checksum     | This parameter is used to validate the data received from the GST Portal.        |
| counterPartSummary.totalRecords | The total number of records being searched for GSTR1 counterpart.                |
| counterPartSummary.totalTax     | The total tax amount to be filed is shown here.                                  |
| counterPartSummary.totalIgst    | The total integrated GST to be filed by the dealer/business owner.               |
| counterPartSummary.totalSgst    | The total state GST to be filed by the dealer/business owner.                    |
| counterPartSummary.totalCgst    | The total central GST to be filed by the dealer/business owner.                  |
| counterPartSummary.totalVal     | The total value of taxable goods as available on the counterpart.                |
| counterPartSummary.totalCess    | The total cess amount to be filed by the dealer/business owner.                  |
{% endtab %}

{% tab title="Response" %}
```
{
    "result":{
        "gstin": "..gstin..",
        "retPeriod": "..retPeriod.."
        "checksum": "..checksum..",
        "sectionSummary": {
            "sectionNo": "..sectionNo..",
            "checksum": "..checksum..",
            "totalRecords": "..totalRecords..",
            "totalTax": "..totalTax..",
            "totalIgst": "..totalIgst..",
            "totalSgst": "..totalSgst..",
            "totalCgst": "..totalCgst..",
            "totalVal": "..totalVal..",
            "totalCess": "..totalCess..",
            "totalDocIssued": "..totalDocIssued..",
            "totalDocCancelled": "..totalDocCancelled..",
            "NetDocIssued": "..NetDocIssued..",
            "counterPartSummary": [{
                "ctin": "..ctin..",
                "checksum": "..checksum..",
                "totalRecords": "..totalRecords..",
                "totalTax": "..totalTax..",
                "totalIgst": "..totalIgst..",
                "totalSgst": "..totalSgst..",
                "totalCgst": "..totalCgst..",
                "totalVal": "..totalVal..",
                "totalCess": "..totalCess.."
            }]

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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/c102782da7f2a87c92cc)
