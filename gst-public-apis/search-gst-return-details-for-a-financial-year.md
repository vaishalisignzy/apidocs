# Search GST Return details for a Financial Year

### &#xD;Introduction

This Signzy API is used to track the financial returns of a particular business for a given financial year by taking GSTIN and the particular financial year as an input. This might be useful for retrieving details about a client when not much is known other than the GSTIN and the year for which the records are required.

**The following information will be extracted :**

* Constitution of business
* Legal name of business
* Trade name of business
* Centre Jurisdiction
* State Jurisdiction
* Registration Date
* Date of tax payment
* Tax payer type
* Cancellation date
* Nature of business activities
* Principal place of address

### How to call the API

You will need to login before sending PAN Number request. You are required to pass the access token received from the login call, as authorization header in the GSTIN request along with GSTIN Number

### API Input Guidelines

* Provide unique **15-digit** alphanumeric GSTIN issued by **Goods and Services Tax department**
* Financial year for which information is required

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for View and Track GST Returns

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization            | Required | String | Access Token                      |
| ------------------------ | -------- | ------ | --------------------------------- |
| Content-Type             | Required | String | Application/JSON                  |
| task                     | Required | String | Type of task - VIEW RETURNS       |
| essentials.gstin         | Required | String | GSTIN number to be searched       |
| essentials.financialYear | Required | Sring  | Financial year to be searched for |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<PATRON ID>/gstns' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "viewReturns",
    "essentials": {
        "gstin": "<GSTIN NUMBER>",
        "financialYear": "2017-18"
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME                          | DESCRIPTION                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------- |
| result                                  | The final response parameters to be displayed are stored here.                  |
| result.filedReturns                     | This parameter contains the details of the filed returns for a particular year. |
| filedReturns.valid                      | The validity of the transaction is denoted by this parameter.                   |
| filedReturns.methodOfFilling            | The method of filing GST returns is determined here.                            |
| filedReturns.dateofFiling               | The date of filing GST returns is displayed here.                               |
| filedReturns.returnPeriod               | The duration/length for which GST returns are being retrieved.                  |
| filedReturns.returnType                 | The type of GST returns is determined here.                                     |
| filedReturns.applicationReferenceNumber | The application reference number associated with GST Return is displayed here.  |
| filedReturns.status                     | The current status of the GST Return is displayed here.                         |
{% endtab %}

{% tab title="Response" %}
```
{
    "task": "viewReturns",
    "essentials": {
        "gstin": "27AOKPP9482P1ZQ",
        "financialYear": "2017-18"
    },
    "id": "618b35222c349a6ff72a0ced",
    "patronId": "6140962af6d4030eae0496e0",
    "result": {
        "filedReturns": [
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "20/03/2018",
                "returnPeriod": "02/2018",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA2702186814521",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "22/02/2018",
                "returnPeriod": "01/2018",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA270118945021H",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "02/02/2018",
                "returnPeriod": "12/2017",
                "returnType": "GSTR1",
                "applicationReferenceNumber": "AB271217216082I",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "17/01/2018",
                "returnPeriod": "12/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA271217420393D",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "25/12/2017",
                "returnPeriod": "09/2017",
                "returnType": "GSTR1",
                "applicationReferenceNumber": "AB270917149635K",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "19/12/2017",
                "returnPeriod": "11/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA271117553595X",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "15/11/2017",
                "returnPeriod": "10/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA271017217072O",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "16/10/2017",
                "returnPeriod": "09/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA270917336509M",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "23/09/2017",
                "returnPeriod": "07/2017",
                "returnType": "GSTR1",
                "applicationReferenceNumber": "AC270717244584P",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "19/09/2017",
                "returnPeriod": "08/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA270817513768L",
                "status": "Filed"
            },
            {
                "valid": "Yes",
                "methodOfFilling": "ONLINE",
                "dateOfFilling": "22/08/2017",
                "returnPeriod": "07/2017",
                "returnType": "GSTR3B",
                "applicationReferenceNumber": "AA2707177085701",
                "status": "Filed"
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |



Use the following exchange parameters for View and Track GST Returns

{% swagger baseUrl="https://production.signzy.tech" path="/api/v2/patrons/...patronID.../gstns" method="post" summary=" GST Returns For A Financial Year" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../gstns`

\




\


This method is used to extract the details of GSTIN for a particular financial year.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task - View Returns
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.gstin" type="string" %}
GSTIN for which return details are searched.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.financialYear" type="string" %}
Financial Year for which the records are being searched.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  	"result": {
  		"filedReturns": [{
  				"valid": "..valid..",
  				"methodOfFilling": "..methodOfFilling..",
  				"dateOfFilling": "..dateOfFilling..",
  				"returnPeriod": "..returnPeriod..",
  				"returnType": "..returnType..",
  				"applicationReferenceNumber": "..applicationReferenceNumber..",
  				"status": "..status.."
  			}

  		]
  	}

  }
```
{% endswagger-response %}
{% endswagger %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/6eb3b56ff09c1994960b)
