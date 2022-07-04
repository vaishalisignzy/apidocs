# Search Company's Regulatory Filings by CIN(D)

The ROC File Download API is a service that is part of the Download File By CIN service. Whenever certain files belonging to regulatory filings of a Company/LLP like Certificate of Incorporation (CoI) or Memorandum of Association (MoA) needs to be retrieved for a company, this API is used to initiate the request for download.

### Introduction

Corporate Identification Number is abbreviated as CIN it's **a unique identification number that is assigned by the ROC** (Registrar of Companies) of various states under the MCA (Ministry of Corporate Affairs) to the registered companies. Using the CIN, this API can retrieve the regulatory filings of the company.

### API Usecase

This API is used to retrieve basic details about the company just by entering the company's CIN as input. It helps in auto-generating the details for the user without having to manually provide the information. The following files will be retrieved :

* Certificate of incorporation
* Memorandum of Association (MOA)
* Article of Association (AOA)

### How to call the API

Before going for ROC file download API for organizations, you first need to create an '_Organization'_ **object** and you need to pass the _CIN_ as an **identifier** in the request body.

### API Input Guidelines

Provide correct CIN, it is **a unique 21 digit alpha-numeric number** provided to every registered company by the **ROC (Registrar of Companies).**

{% hint style="info" %}
You can get CIN from our API [Search by Company Name](search-by-company-name.md)
{% endhint %}

###

### Sample CURL Request

### **Step 1**: Creating Organisation Object

{% tabs %}
{% tab title="Input Parameters" %}

{% endtab %}

{% tab title="CURL Request" %}
```
```


{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters " %}
| Parameter Name |   |
| -------------- | - |
|                |   |
|                |   |
|                |   |
{% endtab %}

{% tab title="Response" %}
```
```
{% endtab %}
{% endtabs %}

### \*\*\*\*

### **Step 2**: Hunt for Organisation

{% tabs %}
{% tab title="Input Parameters" %}

{% endtab %}

{% tab title="CURL Request" %}
```
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description |
| -------------- | ----------- |
|                |             |
|                |             |
|                |             |
{% endtab %}

{% tab title="API Response" %}
```
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

#### Creating Organization Object

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronId.../organizations" method="post" summary="Search Company Regulatory Filings by CIN" %}
{% swagger-description %}
**Production URL:**

\\

`https://signzy.tech/api/v2/patrons/...patronId.../organizations`

\\

\\

This method is used to search for a company's regulatory filings by its Company identification Number (CIN)
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" required="false" %}
Access Token
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" required="false" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="identifier" type="string" required="false" %}
Contains the unique identifier ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="service" type="string" required="false" %}
Type of service - roc
{% endswagger-parameter %}

{% swagger-parameter in="body" name="callbackURL" type="string" required="false" %}
The call back URL
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
        "callbackUrl": "...callback...",
        "accessToken": "...accestoken....",
        "id": "....id...",
        "patronId": "....patronid...",
        "identifier": "...identifier...",
        "service": "roc"
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "identifier": "...identifier...",
      "service": "roc",
      "callbackUrl": "...callback..."
    }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                            |
| -------------- | ---------------------------------------------------------------------- |
| callbackUrl    | This parameter contains the URl where the response is to be posted.    |
| accesstoken    | The access token that is received during login request.                |
| id             | The parameter which contains the userId received during login request. |
| identifier     | The unique identifier ID.                                              |
| service        | The type of Signzy service - "roc search".                             |
{% endtab %}
{% endtabs %}

#### Creating ROC File Download request.

Use the following exchange parameters for ROC search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/hunts" method="post" summary="ROC File Download `hunt` request" %}
{% swagger-description %}
**Production URL:**

\\

`https://signzy.tech/api/v2/hunts`

\\

\\

This method creates a File Download Hunt request
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-Type" type="string" required="false" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="target" type="string" required="false" %}
Organization
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemId" type="string" required="false" %}
id-of-the-organzation-object-created
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="string" required="false" %}
access-token-from-the-organization-creation-request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Task" type="string" required="false" %}
Task to be performed - fileDownloadByCin
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" required="false" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.cin" type="string" required="false" %}
company's-cin-to-search-for
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
     	"cin": ".....company's-cin-to-search-for...."
      "result": {
          "cin": ".....company's-cin-to-search-for....",
          "requestId": "...requestId...",
          "callbackUrl": "...callback...",
      }
  }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "target": "Organization",
    "itemId": "....id-of-the-organzation-object-created.....",
    "accessToken": ".....access-token-from-the-organization-creation-request.....",
    "task": "fileDownloadByCin",
    "essentials": {
    	"cin": ".....company's-cin-to-search-for...."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                        |
| -------------- | ------------------------------------------------------------------ |
| cin            | The company identification number being searched.                  |
| requestId      | The unique request ID.                                             |
| callbackUrl    | This parameter contains the URL where the response will be posted. |
{% endtab %}
{% endtabs %}

[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/2ee7c3a566d899966273)
