# Search GSTR2A B2B details

### &#xD;Introduction

Form GSTR 2A is an auto-populated statement in which the visibility of all the inward supplies reported by one’s supplier in GSTR 1, is made available to the recipient. The details of this form are made available on the GST portal after submission.

### API Usecase

We can use this service to view the details directly rather than extract the same from the GST portal. The request made by the API returns the details of all B2B transactions (Business to Business) for the particular GSTIN.

### How to call the API

You will need to login before sending GSTR2A B2B Request. You are required to pass the access token received from the login call, as authorization header in the GSTR2A B2B Request along with other parameters.

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Username registered on **GST Portal**
* **Auth Token** received from **** [GSTR Initiation Flow - Get Auth Token](gstr-initiation-flow-get-auth-token.md)
* **Secret Key**
* **App key r**eceived from **** [GSTR Initiation Flow - Get OTP Request](gstr-initiation-flow-get-otp-request.md)
*   Return Period

    <mark style="color:blue;"></mark>

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for GSTR2a B2B Request

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String  | Access Token                                      |
| -------------------- | -------- | ------- | ------------------------------------------------- |
| Content-Type         | Required | String  | Application/JSON                                  |
| task                 | Required | String  | Type of task performed - B2B                      |
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
    "task" : "b2b",
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
| PARAMETER NAME                       | DESCRIPTION                                                                  |
| ------------------------------------ | ---------------------------------------------------------------------------- |
| result                               | The final response parameters to be displayed are contained here.            |
| result.message                       | The status message which indicates if the returns were fetched successfully. |
| result.data                          | The details of the GSTR2A returns are stored in this parameter.              |
| data.invoiceDetails                  | The invoice details for GSTR2A is displayed by this parameter.               |
| invoiceDetails.invoiceChecksumValue  |                                                                              |
| invoiceDetails.supplierInvoiceNumber | The identifying number for the supplier invoice.                             |
| invoiceDetails.supplierInvoiceDate   | The date of the supplier invoice is shown here.                              |
| invoiceDetails.supplierInvoiceValue  | The total value estimated on the supplier invoice.                           |
| invoiceDetails.placeOfSupply         | The place of supply registered to the supplier as per GSTR2A.                |
| invoiceDetails.reverseCharge         | This displays the total amount of charges that were reversed.                |
| invoiceDetails.invoiceType           | The type of invoice associated with the GSTR2A.                              |
| invoiceDetails.items                 | The list of items on the invoice are displayed in detail by this parameter.  |
| items.number                         | The item number on the list of items.                                        |
| item.details                         | The details of the items on the invoice are displayed here.                  |
| details.taxableValue                 | The net taxable value on the inward sales of the supplier.                   |
| details.igstAmount                   | The IGST amount on the taxable value.                                        |
| details.cgstAmount                   | The CGST amount on the taxable value.                                        |
| details.sgstAmount                   | The SGST amount on the taxable value.                                        |
| details.cessAmount                   | The net cess amount on the taxable value.                                    |
| details.taxRate                      | The tax rate                                                                 |
| details.ctin                         | The CTIN number on the invoice is displayed here.                            |
{% endtab %}

{% tab title="Response" %}
```
{
  	"result": {
  		"message": "Returns fetched successfully",
  		"data": [{
  			"invoiceDetails": [{
  				"invoiceChecksumValue": "..invoiceChecksumValue..",
  				"supplierInvoiceNumber": "..supplierInvoiceNumber..",
  				"supplierInvoiceDate": "..supplierInvoiceDate..",
  				"supplierInvoiceValue": "..supplierInvoiceValue..",
  				"placeOfSupply": "..placeOfSupply..",
  				"reverseCharge": "..reverseCharge..",
  				"invoiceType": "..invoiceType..",
  				"items": [{
  					"number": "..number..",
  					"details": {
  						"taxableValue": "..taxableValue..",
  						"igstAmount": "..igstAmount..",
  						"cgstAmount": "..cgstAmount..",
  						"sgstAmount": "..sgstAmount..",
  						"cessAmount": "..cessAmount..",
  						"taxRate": "..taxRate.."
  					}
  				}]
  			}],
  			"counterPartyFillingStatus": "..counterPartyFillingStatus..",
  			"ctin": "..ctin.."
  		}]
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/85e7aaa90f6a1505a87a)

