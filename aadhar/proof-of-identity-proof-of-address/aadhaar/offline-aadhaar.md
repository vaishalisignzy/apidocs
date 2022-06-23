---
description: Offline Aadhaar data extraction from ZIP orXML file
---

# Offline Aadhaar

### An Overview

This API service reads the data directly from the URL of the ZIP or XML file of an Offline Aadhaar to collect all the details.&#x20;

> In the case of a zip file, you have to pass the password in the request body.&#x20;
>
> In the case of XML, a file password is not required.

### How to call the API

Before going for Auto reading, you first need to create an Identity object. The API responds with a JSON object upon creating a request.



### API Input Guidelines

* A Zip file, or
* An XML file
* Size ?

### Sample CURL Request

### **Step 1**: Hit Identities API

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                       |
| -------------- | ----------------- | --------- | --------------------------------- |
| Authorization  | Required          | String    | Access Token                      |
| Content-Type   | Required          | String    | Application/JSON                  |
| Type           | Required          | String    | Aadhaar                           |
| e-mail         | Required          | String    | e-mail ID                         |
| Callback URL   | Required          | String    | URL where response will be posted |


{% endtab %}

{% tab title="Curl Request" %}
```
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/identities' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--data-raw '{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": []
}'
```
{% endtab %}
{% endtabs %}

Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameters Name | Data Type | Description |
| --------------- | --------- | ----------- |
| type            | String    |             |
| email           | String    |             |
| Callbackurl     | String    |             |
| images          |           |             |
| accessToken     | String    |             |
| autoRecognition | String    |             |
| verification    | String    |             |
| forgeryCheck    | String    |             |
| id              | String    |             |
| patronid        | String    |             |


{% endtab %}

{% tab title="Response" %}
```
{
    "type": "aadhaar",
    "email": "ankur.rand@signzy.com",
    "callbackUrl": "https://www.w3schools.com",
    "images": [],
    "accessToken": "ks4oo3fbbaegl04ckm3yv8cewxlaoh",
    "autoRecognition": [],
    "verification": [],
    "forgeryCheck": [],
    "id": "6177cc01c9d0c71ff1c5a32f",
    "patronId": "6140962af6d4030eae0496e0"
}
```
{% endtab %}
{% endtabs %}

###

### **Step 2:** Hit Snoops API and receives a response

{% tabs %}
{% tab title="Input Parameters" %}
| Parameters Name | Description                                |
| --------------- | ------------------------------------------ |
| content-Type    | Application/ JSON                          |
| service         | type-identity                              |
| itemId          | Contains the Identity object id            |
| accessToken     | Access token for the identity object       |
| task            | offline Aadhaar                            |
| essentials      | contains the URL and password of the file. |
|                 |                                            |
{% endtab %}

{% tab title="Snoops Response" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/snoops' \
--header 'Content-Type: application/json;charset=UTF-8' \
--data-raw '{
    "service": "Identity",
    "itemId": "6178a991c9d0c71ff1c5c018",
    "accessToken": "323q6sn330q0va5xpkljc0iyamwi1463v9",
    "task": "offlineAadhaar",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/29451333/download/25c86d76e8e146e38ecdc957b22eecdd2664e84e44f24ca0af5cedf46f6e4ce3.zip",
        "password": "<Password of the zip file>",
        "email": "<e-mail address of the Aadhaar holder>",
        "mobile": "<Mobile Number of the Aadhaar holder>"
    }
}'
```
{% endtab %}
{% endtabs %}

### Sample API Response

{% tabs %}
{% tab title="Response Parameter" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name                     | The name of the Aadhaar card holder.                                                                                                                                                                                                |
| dob                      | The date of birth of the Aadhaar Card holder.                                                                                                                                                                                       |
| gender                   | The gender of the Aadhaar card holder.                                                                                                                                                                                              |
| emailHash                | This parameter contains the hashed value of the email ID of Aadhaar holder.                                                                                                                                                         |
| mobileNoHash             | This parameter contains the hashed value of the mobile number of the Aadhaar holder.                                                                                                                                                |
| x509Data                 | This parameter contains the digital certificate information of the Aadhaar Card.                                                                                                                                                    |
| x509Data.subjectName     | This parameter shows the subject name and version used for displaying the Aadhaar digital Certificate.                                                                                                                              |
| x509Data.certificate     | The digital certificate ID for the Aadhaar card.                                                                                                                                                                                    |
| x509Data.details         | This parameter contains the details of the digital certificate including DSC validator of Aadhaar Card.                                                                                                                             |
| address                  | The address details of the Aadhaar Card holder is displayed here.                                                                                                                                                                   |
| photo                    | The URL of the uploaded Aadhaar Card image.                                                                                                                                                                                         |
| splitAddress             | This parameter distinguishes the various parts of the address of the Aadhaar holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”. |
| splitAddress.addressLine | The first line of the address is displayed by this parameter.                                                                                                                                                                       |
{% endtab %}

{% tab title="API Response" %}
```
{
    "service": "Identity",
    "itemId": "6178a991c9d0c71ff1c5c018",
    "task": "offlineAadhaar",
    "essentials": {
        "url": "https://preproduction-persist.signzy.tech/api/files/29451333/download/25c86d76e8e146e38ecdc957b22eecdd2664e84e44f24ca0af5cedf46f6e4ce3.zip",
        "password": "<Password of the zip file>",
        "email": "<email ID of aadhaar card holder>",
        "mobile": "<Mobile Number of user>",
        "instance": {
            "id": "6178a991c9d0c71ff1c5c018",
            "callbackUrl": "https://www.w3schools.com"
        }
    },
    "accessToken": "323q6sn330q0va5xpkljc0iyamwi1463v9",
    "id": "61790481c9d0c71ff1c5c9f9",
    "response": {
        "url": "https://preproduction-persist.signzy.tech/api/files/29451333/download/25c86d76e8e146e38ecdc957b22eecdd2664e84e44f24ca0af5cedf46f6e4ce3.zip",
        "id": "61790481794a524d6b5fac4e",
        "result": {
            "name": "RAM SHARMA",
            "dob": "01/01/1998",
            "yob": "1998",
            "gender": "MALE",
            "emailHash": "0793d82f1d738bbac1de1ae0086df82fce9d128064fb373da3f6a19e76fba782",
            "mobileNoHash": "892b21b53c472c1983b25d61c630b926a7f7d4980730b4838e5293444a5ac424",
            "address": "C/O,PREM SINGH BISTH A-53 06 NEAR BADRINATH MANDIR WEST VINOD NAGAR LAXMI NAGAR (EAST DELHI) LAXMI NAGAR (EAST DELHI) EAST DELHI DELHI INDIA 110092",
            "photo": "https://persist.signzy.tech/api/files/234618989/download/5a9378f90b4446c4a9bc9649c4fd015ed2e2b0220a194ed8ad57624d5de526fb.jpeg",
            "uidLast4Digits": "6603",
            "uid": "XXXXXXXX6603",
            "generationDate": "26/10/2021",
            "generationTime": "15:01:42",
            "unixTimeStamp": 1635240702,
            "dateDifference": 0,
            "expiryTime": "",
            "emailHashVerified": "yes",
            "mobileHashVerified": "yes",
            "splitAddress": {
                "district": [
                    "EAST DELHI"
                ],
                "state": [
                    [
                        "DELHI",
                        "DL"
                    ]
                ],
                "city": [
                    "DELHI"
                ],
                "pincode": "110092",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "<Address of Aadhaar holder>"
            },
            "x509Data": {
                "subjectName": "DS UIDAI 01",
                "certificate": "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",
                "details": {
                    "version": 2,
                    "subject": {
                        "countryName": "IN",
                        "organizationName": "UIDAI",
                        "organizationalUnitName": "Technology Centre",
                        "postalCode": "560092",
                        "stateOrProvinceName": "Karnataka",
                        "streetAddress": "bangalore",
                        "houseIdentifier": "UIDAI Tech Centre, Aadhar Complex, NTI Layout, Tat",
                        "serialNumber": "b19a87fae7ae9ef55ff166b5cc625700e28d82da76bd53f09836eeaeab3fe385",
                        "commonName": "DS UIDAI 01"
                    },
                    "issuer": {
                        "countryName": "IN",
                        "organizationName": "Capricorn Identity Services Pvt Ltd.",
                        "organizationalUnitName": "Certifying Authority",
                        "postalCode": "110092",
                        "stateOrProvinceName": "DELHI",
                        "streetAddress": "18,LAXMI NAGAR DISTRICT CENTER",
                        "houseIdentifier": "G5,VIKAS DEEP BUILDING",
                        "commonName": "Capricorn CA 2014"
                    },
                    "serial": "02FE6F53",
                    "notBefore": "2020-05-27T05:03:05.000Z",
                    "notAfter": "2023-05-27T05:03:05.000Z",
                    "subjectHash": "db8cc5b5",
                    "signatureAlgorithm": "sha256WithRSAEncryption",
                    "fingerPrint": "DF:2A:08:D0:9E:8A:E6:21:04:8C:3C:3F:49:0D:F7:07:CE:1F:9A:39",
                    "publicKey": {
                        "algorithm": "sha256WithRSAEncryption"
                    },
                    "altNames": [],
                    "extensions": {
                        "extendedKeyUsage": "Microsoft Smartcardlogin, E-mail Protection, TLS Web Client Authentication, 1.3.6.1.4.1.311.10.3.12, 1.2.840.113583.1.1.5",
                        "authorityKeyIdentifier": "keyid:43:80:04:A0:07:B5:E0:CF",
                        "authorityInformationAccess": "OCSP - URI:http://ocvs.certificate.digital/\nCA Issuers - URI:https://www.certificate.digital/repository/CapricornCA2014.cer",
                        "certificatePolicies": "Policy: 2.16.356.100.2.3\n  User Notice:\n    Explicit Text: Class 3 Certificate issued by Capricorn Certifying Authority\nPolicy: 2.16.356.100.10.1\n  User Notice:\n    Explicit Text: Organizational Document Signer Certificate\nPolicy: 2.16.356.100.1.10.2\n  CPS: https://www.certificate.digital/repository/cpsv1.pdf",
                        "cRLDistributionPoints": "Full Name:\n  URI:https://www.certificate.digital/crl/CapricornCA.crl",
                        "subjectKeyIdentifier": "4D:F9:2C:CF:41:DA:50:55",
                        "keyUsage": "Digital Signature, Non Repudiation",
                        "subjectAlternativeName": "email:anup.kumar@uidai.net.in",
                        "basicConstraints": "CA:FALSE"
                    }
                },
                "validAadhaarDSC": "yes"
            }
        },
        "instance": {
            "id": "6178a991c9d0c71ff1c5c018",
            "callbackUrl": "https://www.w3schools.com"
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



{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/snoops" method="post" summary="Offline Aadhaar XML Extraction" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/snoops`

\




\


This method is used to read offline XML or ZIP Aadhaar files.
{% endswagger-description %}

{% swagger-parameter in="body" name="essentials" type="string" %}
contains the URL and password of the file.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accessToken" type="string" %}
access token for the identity object 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task " type="string" %}
type of task - offline Aadhaar
{% endswagger-parameter %}

{% swagger-parameter in="body" name="itemID" type="string" %}
Contains the Identity object id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="service" type="string" %}
type-identity
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
      "name": "...name of person...",
      "dob": "..date of birth...",
      "gender": "...gender...",
      "emailHash": "...hash of email...",
      "mobileNoHash": "...hash of mobile number...",
      "x509Data": {
        "subjectName": "",
        "certificate": "",
        "details": {},
        "validAadhaarDSC": "...dsc status..."
      },
      "address": "...address ....",
      "photo": "...url to the image...",
      "splitAddress": {
        "district": [
          "...district.."
        ],
        "state": [
          [
            "..state name...",
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
        "addressLine": "...address line..."
      }
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
        "service":"Identity",
        "itemId":"<Identity-id>",
        "task":"offlineAadhaar",
        "accessToken":"<Identity-access-token>",
        "essentials":{
            "url":"...remote url of the file...",
            "password":"password of the file"
        }
    }
```
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/5fa2cf67da23501971b1)

