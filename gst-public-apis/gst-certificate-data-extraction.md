# GST Certificate Data Extraction

### Introduction

Every taxpayer who has successfully registered under GST is issued a GST registration certificate in form GST REG-06. The registration certificate is available for downloading only on the [GST Portal,](https://cleartax.in/s/cleartax-guide-on-gst-portal) and the government does not issue any physical certificate.&#x20;

### API Usecase

The GST certificate extraction API by Signzy is designed to extract the details from the uploaded pdf for further use. Please note that the pdf file size must be less than 2 MB. In case you have an image/image URL, you can use the Converters API by Signzy to convert file to .pdf for extraction.

**The following information will be extracted :**

* Registration Status
* CST Status&#x20;
* PAN
* Dealer's Name
* Dealer's Address
* Registration Date&#x20;
* Cancellation Date



### How to call the API

You will need to [login](https://docs-staging.signzy.tech/) before sending an Extraction request for a GSTN certificate. You are required to pass the access token received from the login call, as an authorization header in the Extraction request apart from the JSON body parameters.

### API Input Guidelines

Provide correct **15 Digit GSTN number** issued by **Goods and Services Tax department**

### <mark style="color:blue;">Sample CURL Request</mark>

Use the following exchange parameters for VAT based search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization    | Required | String | Access Token     |
| ---------------- | -------- | ------ | ---------------- |
| Content-Type     | Required | String | Application/JSON |
| essentials.files | Required | PDF    | Certificate URL  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/gstextractions' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "essentials": {
        "files": [
            "<URL of PDF>"
        ]
    }
}'
```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">**Response**</mark>

{% tabs %}
{% tab title="Response Parameters " %}
| PARAMETER NAME                                   | DESCRIPTION                                                                                                                                                                                                                                         |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials                                       | This parameter contains the essential data for generating output.                                                                                                                                                                                   |
| essentials.files                                 | This parameter contains the URL of the uploaded image for GST Certificate.                                                                                                                                                                          |
| id                                               | The access token generated during login request is held here.                                                                                                                                                                                       |
| patronId                                         | This parameter is returned as userId parameter of login request.                                                                                                                                                                                    |
| result                                           | The final response parameters to be displayed are contained here.                                                                                                                                                                                   |
| result.gstDetails                                | The GST Certificate details are contained in this parameter.                                                                                                                                                                                        |
| gstDetails.addressOfPrincipalPlaceOfBusiness     | The primary address of the principal place of business is displayed by this parameter.                                                                                                                                                              |
| gstDetails.address                               | All the addresses of the primary establishment of business are shown by this parameter in detail.                                                                                                                                                   |
| gstDetails.splitAddress                          | This parameter distinguishes the various parts of the address of the primary business establishment into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine                         | The first line of the registered address is displayed by this parameter.                                                                                                                                                                            |
| result.businessPlaces                            | This parameter shows the addresses of the other business places (like branch offices).                                                                                                                                                              |
| businessPlaces.address                           | The addresses of the business places (multiple if more than one address) are shown in this parameter.                                                                                                                                               |
| businessPlaces.splitAddress                      | This parameter distinguishes the various parts of the address of the business places into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.                |
| splitAddress.addressLine                         | The first line of the address of business place is displayed by this parameter.                                                                                                                                                                     |
| result.constitutionOfBusiness                    | This parameter determines whether the GST Certificate has been issued to a public or private limited company.                                                                                                                                       |
| result.dateOfIssue                               | The date of issue of the GST Certificate.                                                                                                                                                                                                           |
| result.dateOfLiability                           | The date of liability that is recorded for the uploaded GST Certificate.                                                                                                                                                                            |
| result.directorInfo                              | The director information of the organization to which the GST Certificate has been issued.                                                                                                                                                          |
| directorInfo.photo                               | The image URL of the director photo.                                                                                                                                                                                                                |
| directorInfo.resident                            | The residential address of the director.                                                                                                                                                                                                            |
| directorInfo.name                                | The name of the director as registered with the GST Certificate.                                                                                                                                                                                    |
| directorInfo.designation                         | The specific designation that is assigned to the director is displayed by this parameter.                                                                                                                                                           |
| result.gstNumber                                 | The GST Number as available on the GST Certificate.                                                                                                                                                                                                 |
| result.jurisdictionalOffice                      | This parameter contains the details, if any, about the jurisdictional office of the company/organization.                                                                                                                                           |
| result.legalName                                 | The legal/official name of the company as registered with the GSTIN.                                                                                                                                                                                |
| result.name                                      | The common name of the company, especially if it is different from the legal name, is displayed here.                                                                                                                                               |
| result.registrationType                          | The type of registration done for the company under GST.                                                                                                                                                                                            |
| result.tradeName                                 | The name of the trade company is displayed here.(If different from name or legal name.)                                                                                                                                                             |
| result.validFrom                                 | The date from which the GST Certificate is valid.                                                                                                                                                                                                   |
| result.validTo                                   | The date upto which the GST Certificate is valid.                                                                                                                                                                                                   |
| result.dscDetails                                | This parameter contains the details about the digital GST certificate for authenticity.                                                                                                                                                             |
| dscDetails.isSigned                              | This parameter checks whether the certificate is signed or not.                                                                                                                                                                                     |
| dscDetails.hashCode                              | The hash code that is attached to the digital certificate is displayed by this parameter.                                                                                                                                                           |
| dscDetails.name                                  | The name on the GST Certificate.                                                                                                                                                                                                                    |
| dscDetails.signDate                              | The date of signature as available on the GST Certificate is verified and displayed by this parameter.                                                                                                                                              |
| dscDetails.signTime                              | The time of signature as available on the GST Certificate is verified and displayed by this parameter.                                                                                                                                              |
| dscDetails.signatureDetails                      | The parameter verifies and displays the details of the available signature on the GST Certificate.                                                                                                                                                  |
| signatureDetails.documentRevision                | This parameter displays the number of times the signature on the document has been revised or changed.                                                                                                                                              |
| signatureDetails.doesSignatureCoversFullDocument | This parameter verifies whether the signature covers the full length of the GST Certificate.                                                                                                                                                        |
| signatureDetails.totalDocumentRevisions          | This shows the total count of document revisions made.                                                                                                                                                                                              |
| signatureDetails.certificateInfo                 | This parameter shows even more details about the GST Certificate regarding validity of the document.                                                                                                                                                |
| certificateInfo.certificateNumber                | The certificate number as available on the uploaded GST Certificate is shown here.                                                                                                                                                                  |
| certificateInfo.subject                          | The subject of the certificate is displayed by this parameter.                                                                                                                                                                                      |
| certificateInfo.certificateValidity              | The validity of the certificate is verified and displayed by this parameter.                                                                                                                                                                        |
| certificateInfo.certificateTimeValidity          | The time validity of the GST Certificate is verified and displayed by this parameter.                                                                                                                                                               |
| certificateInfo.validFrom                        | The date from which the digital certificate is valid.                                                                                                                                                                                               |
| certificateInfo.issuer                           | The issuing authority of the certificate is displayed here.                                                                                                                                                                                         |
| certificateInfo.validTo                          | The date up to which the digital certificate is valid.                                                                                                                                                                                              |
| result.integrityCheck                            | The integrity check status of the certificate is displayed by this parameter.                                                                                                                                                                       |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "files": [
            "<URL of GST certificate>"
        ]
    },
    "id": "<Access Token from Login request>",
    "patronId": "<Patron ID>",
    "result": {
        "gstDetails": {
            "addressOfPrincipalPlaceOfBusiness": {
                "address": "",
                "splitAddress": {
                    "error": {
                        "name": "error",
                        "message": "This is not a valid address",
                        "status": 400,
                        "reason": "INVALID_PARAM",
                        "type": "Bad Request",
                        "statusCode": 400
                    }
                }
            },
            "buisnessPlaces": [],
            "constitutionOfBusiness": "Proprietorship",
            "dateOfIssue": "",
            "dateOfLiability": "27/09/2017",
            "designation": "Superintendent",
            "directorInfo": [],
            "gstNumber": "07APOPS5860B1ZM",
            "jurisdictionalOffice": "Ward",
            "legalName": "AMIT SHARMA",
            "name": "SURENDER KUMAR BAHOT",
            "registrationType": "Regular",
            "tradeName": "ARIA INTERNATIONAL",
            "validFrom": "",
            "validTo": "NA"
        },
        "signatureDetails": "",
        "dscDetails": ""
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |





Use the following exchange parameters for Extracting data from a PDF GST certificate.

{% swagger baseUrl="https://production.signzy.tech" path="/api/v2/patrons/...patronID.../gstextractions" method="post" summary="GST Certificate Data Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../gstextractions`

\




\


This method is used to extract the details from GST Certificate.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.files" type="string" %}
URL of the file from which data has to be extracted
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "essentials": {
        "files": [
            "...file url..."
        ]
    },
    "id": "...id...",
    "patronId": "...patron id...",
    "result": {
        "gstDetails": {
            "addressOfPrincipalPlaceOfBusiness": {
                "address": "...address...",
                "splitAddress": {
                    "address": "...address...",                    
                    "result": {
                        "splitAddress": {
                            "district": [
                                "...district name..."
                            ],
                            "state": [
                                [
                                    "...state name...",
                                    "...state code..."
                                ]
                            ],
                            "city": [
                                "...city name..."
                            ],
                            "pincode": "...pincode...",
                            "country": [
                                "IN",
                                "IND",
                                "INDIA"
                            ],
                            "addressLine": "...address line...."
                        }
                    }
                }
            },
            "buisnessPlaces": [
                {
                    "address": "...address of business places...",
                    "splitAddress": {
                        "address": "...address of business places...",                        
                        "result": {
                            "splitAddress": {
                                "district": [
                                    "...city name.."
                                ],
                                "state": [
                                    [
                                        "...state name...",
                                        "..state code..."
                                    ]
                                ],
                                "city": [
                                    "...city name..."
                                ],
                                "pincode": "...pincode...",
                                "country": [
                                    "IN",
                                    "IND",
                                    "INDIA"
                                ],
                                "addressLine": "...address line..."
                            }
                        }
                    }
                }
                
            ],
            "constitutionOfBusiness": "...public/private limited company...",
            "dateOfIssue": "..date of issue...",
            "dateOfLiability": "...date of liability...",
            "designation": "...designation...",
            "directorInfo": [
                {
                    "photo": "...url of the image...",
                    "resident": "...resident of director...",
                    "name": "...name...",
                    "designation": "...designation..."
                }
            ],
            "gstNumber": "...gst number...",
            "jurisdictionalOffice": "",
            "legalName": "...legal name of the company...",
            "name": "",
            "registrationType": "...type of registration...",
            "tradeName": "...name of the trade company...",
            "validFrom": "...valid from what date...",
            "validTo": "..date.."
        },
        "dscDetails": {
            "isSigned": "...is signed status...",
            "hashcode": ...hash code...,
            "name": "...name...",
            "signDate": "...sign date...",
            "signTime": "...sign time...",
            "signatureDetails": {
                "documentRevision": 1,
                "doesSignatureCoversFullDocument": true,
                "totalDocumentRevisions": 1,
                "certificateInfo": [
                    {
                        "certificateNumber": 0,
                        "subject": "...subject of certificate...",
                        "certificateValidity": "...validity status of certificate...",
                        "certificateTimeValidity": "...time validity of certificate...",
                        "validFrom": "...valid from what date...",
                        "issuer": "...issuer of the certificate...",
                        "validTo": "...valid to what date..."
                    }
                ],
                "IntegrityCheck": ...integrity check status...
            }
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "essentials": {
      "files": ["..url to a PDF file from which you need to extract data.."]
    }
  }

```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                                   | DESCRIPTION                                                                                                                                                                                                                                         |
| ------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials                                       | This parameter contains the essential data for generating output.                                                                                                                                                                                   |
| essentials.files                                 | This parameter contains the URL of the uploaded image for GST Certificate.                                                                                                                                                                          |
| id                                               | The access token generated during login request is held here.                                                                                                                                                                                       |
| patronId                                         | This parameter is returned as userId parameter of login request.                                                                                                                                                                                    |
| result                                           | The final response parameters to be displayed are contained here.                                                                                                                                                                                   |
| result.gstDetails                                | The GST Certificate details are contained in this parameter.                                                                                                                                                                                        |
| gstDetails.addressOfPrincipalPlaceOfBusiness     | The primary address of the principal place of business is displayed by this parameter.                                                                                                                                                              |
| gstDetails.address                               | All the addresses of the primary establishment of business are shown by this parameter in detail.                                                                                                                                                   |
| gstDetails.splitAddress                          | This parameter distinguishes the various parts of the address of the primary business establishment into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine                         | The first line of the registered address is displayed by this parameter.                                                                                                                                                                            |
| result.businessPlaces                            | This parameter shows the addresses of the other business places (like branch offices).                                                                                                                                                              |
| businessPlaces.address                           | The addresses of the business places (multiple if more than one address) are shown in this parameter.                                                                                                                                               |
| businessPlaces.splitAddress                      | This parameter distinguishes the various parts of the address of the business places into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.                |
| splitAddress.addressLine                         | The first line of the address of business place is displayed by this parameter.                                                                                                                                                                     |
| result.constitutionOfBusiness                    | This parameter determines whether the GST Certificate has been issued to a public or private limited company.                                                                                                                                       |
| result.dateOfIssue                               | The date of issue of the GST Certificate.                                                                                                                                                                                                           |
| result.dateOfLiability                           | The date of liability that is recorded for the uploaded GST Certificate.                                                                                                                                                                            |
| result.directorInfo                              | The director information of the organization to which the GST Certificate has been issued.                                                                                                                                                          |
| directorInfo.photo                               | The image URL of the director photo.                                                                                                                                                                                                                |
| directorInfo.resident                            | The residential address of the director.                                                                                                                                                                                                            |
| directorInfo.name                                | The name of the director as registered with the GST Certificate.                                                                                                                                                                                    |
| directorInfo.designation                         | The specific designation that is assigned to the director is displayed by this parameter.                                                                                                                                                           |
| result.gstNumber                                 | The GST Number as available on the GST Certificate.                                                                                                                                                                                                 |
| result.jurisdictionalOffice                      | This parameter contains the details, if any, about the jurisdictional office of the company/organization.                                                                                                                                           |
| result.legalName                                 | The legal/official name of the company as registered with the GSTIN.                                                                                                                                                                                |
| result.name                                      | The common name of the company, especially if it is different from the legal name, is displayed here.                                                                                                                                               |
| result.registrationType                          | The type of registration done for the company under GST.                                                                                                                                                                                            |
| result.tradeName                                 | The name of the trade company is displayed here.(If different from name or legal name.)                                                                                                                                                             |
| result.validFrom                                 | The date from which the GST Certificate is valid.                                                                                                                                                                                                   |
| result.validTo                                   | The date upto which the GST Certificate is valid.                                                                                                                                                                                                   |
| result.dscDetails                                | This parameter contains the details about the digital GST certificate for authenticity.                                                                                                                                                             |
| dscDetails.isSigned                              | This parameter checks whether the certificate is signed or not.                                                                                                                                                                                     |
| dscDetails.hashCode                              | The hash code that is attached to the digital certificate is displayed by this parameter.                                                                                                                                                           |
| dscDetails.name                                  | The name on the GST Certificate.                                                                                                                                                                                                                    |
| dscDetails.signDate                              | The date of signature as available on the GST Certificate is verified and displayed by this parameter.                                                                                                                                              |
| dscDetails.signTime                              | The time of signature as available on the GST Certificate is verified and displayed by this parameter.                                                                                                                                              |
| dscDetails.signatureDetails                      | The parameter verifies and displays the details of the available signature on the GST Certificate.                                                                                                                                                  |
| signatureDetails.documentRevision                | This parameter displays the number of times the signature on the document has been revised or changed.                                                                                                                                              |
| signatureDetails.doesSignatureCoversFullDocument | This parameter verifies whether the signature covers the full length of the GST Certificate.                                                                                                                                                        |
| signatureDetails.totalDocumentRevisions          | This shows the total count of document revisions made.                                                                                                                                                                                              |
| signatureDetails.certificateInfo                 | This parameter shows even more details about the GST Certificate regarding validity of the document.                                                                                                                                                |
| certificateInfo.certificateNumber                | The certificate number as available on the uploaded GST Certificate is shown here.                                                                                                                                                                  |
| certificateInfo.subject                          | The subject of the certificate is displayed by this parameter.                                                                                                                                                                                      |
| certificateInfo.certificateValidity              | The validity of the certificate is verified and displayed by this parameter.                                                                                                                                                                        |
| certificateInfo.certificateTimeValidity          | The time validity of the GST Certificate is verified and displayed by this parameter.                                                                                                                                                               |
| certificateInfo.validFrom                        | The date from which the digital certificate is valid.                                                                                                                                                                                               |
| certificateInfo.issuer                           | The issuing authority of the certificate is displayed here.                                                                                                                                                                                         |
| certificateInfo.validTo                          | The date up to which the digital certificate is valid.                                                                                                                                                                                              |
| result.integrityCheck                            | The integrity check status of the certificate is displayed by this parameter.                                                                                                                                                                       |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/90a9a4f3a8c99cb0ea6b)
