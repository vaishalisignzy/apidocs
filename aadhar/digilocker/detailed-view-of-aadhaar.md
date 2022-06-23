# Get e-Aadhaar

### **Introduction**

Signzy provides a Digilocker iframe where the user enters the Digilocker credentials and gives access to documents in Digilocker to the client.&#x20;

### API Usecase

If you have a web-based application (be it mobile web or desktop web) you can access this through an **iframe**. In your mobile application, you can use web view. If you have ever integrated iframe based payment gateways, you would find this to be very similar.

### How to call the API

Once you are logged in, you need to initiate Aadhaar Auth session by creating a web URL in the following manner.

### API Input Guidelines

* Request ID will be auto filled

### <mark style="color:blue;">Sample CURL Request</mark>

{% tabs %}
{% tab title="First Tab" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                      |
| ------------------- | ---------------------------------------------------- |
| task                | <p>The type of task performed - “getEadhaar”<br></p> |
| essentials          | Contains the essential output data                   |
{% endtab %}

{% tab title="Second Tab" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/digilockers' \
--header 'Authorization: <Auth Key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "getEadhaar",
    "essentials": {
        "requestId": "Unique File ID"
    }
}'

```
{% endtab %}
{% endtabs %}

### <mark style="color:green;">Sample API Response</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| Parameters Name      | Description                                                                                             |
| -------------------- | ------------------------------------------------------------------------------------------------------- |
| result.name          | Aadhaar holder name                                                                                     |
| result.uid           | Aadhaar number                                                                                          |
| result.gender        | Gender of aadhaar holder                                                                                |
| result.x509Data      | This parameter contains the digital certificate information of the Aadhaar Card.                        |
| x509Data.subjectName | This parameter shows the subject name and version used for displaying the Aadhaar digital Certificate.  |
| x509Data.certificate | The digital certificate ID for the Aadhaar card.                                                        |
| x509Data.details     | This parameter contains the details of the digital certificate including DSC validator of Aadhaar Card. |
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "essentials": {
        "requestId": "Unique File ID"
    },
    "id": "<Request id>",
    "patronId": "<Patron ID>",
    "task": "getEadhaar",
    "result": {
        "name": "Ravi Singh",
        "uid": "xxxxxxxx7758",
        "dob": "03/05/1997",
        "gender": "MALE",
        "x509Data": {
            "subjectName": "DS MINISTRY OF ELECTRONICS AND INFORMATION TECHNOLOGY 01",
            "certificate": "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",
            "details": {
                "version": 2,
                "subject": {
                    "countryName": "IN",
                    "organizationName": "MINISTRY OF ELECTRONICS AND INFORMATION TECHNOLOGY",
                    "organizationalUnitName": "NeGD",
                    "commonName": "DS MINISTRY OF ELECTRONICS AND INFORMATION TECHNOLOGY 01",
                    "serialNumber": "0f30cb67333f634db11fdb41868b343a6f0469581bdb9fd2a2e4cb59e7797a43",
                    "postalCode": "110003",
                    "telephoneNumber": "b176790cc3a74b862e6b6b50814a8887a5f372ac5a0689eb5219c0b4a978583c",
                    "stateOrProvinceName": "Delhi"
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
                "serial": "02A905",
                "notBefore": "2017-12-13T09:14:46.000Z",
                "notAfter": "2019-12-13T09:14:46.000Z",
                "subjectHash": "d8b970c7",
                "signatureAlgorithm": "sha256WithRSAEncryption",
                "fingerPrint": "D3:B7:FE:62:58:09:B9:97:82:B5:AA:8C:F5:46:80:FE:32:67:EA:9E",
                "publicKey": {
                    "algorithm": "sha256WithRSAEncryption"
                },
                "altNames": [],
                "extensions": {
                    "extendedKeyUsage": "Microsoft Smartcardlogin, E-mail Protection, TLS Web Client Authentication, 1.3.6.1.4.1.311.10.3.12",
                    "authorityKeyIdentifier": "keyid:43:80:04:A0:07:B5:E0:CF",
                    "authorityInformationAccess": "OCSP - URI:http://ocvs.certificate.digital/\nCA Issuers - URI:https://www.certificate.digital/repository/CapricornCA2014.cer",
                    "certificatePolicies": "Policy: 2.16.356.100.2.2\n  CPS: https://www.certificate.digital/repository/cpsv1.pdf\n  User Notice:\n    Explicit Text: Class 2 Certificate issued by Capricorn Certifying Authority\nPolicy: 2.16.356.100.10.1\n  User Notice:\n    Explicit Text: Organizational Document Signer Certificate",
                    "cRLDistributionPoints": "Full Name:\n  URI:https://www.certificate.digital/crl/CapricornCA.crl",
                    "subjectKeyIdentifier": "42:20:58:03:49:7D:83:F9",
                    "keyUsage": "Digital Signature, Non Repudiation",
                    "subjectAlternativeName": "email:d.nayak@nic.in"
                }
            },
            "validAadhaarDSC": "yes"
        },
        "address": "Address Of the aadhaar holder",
        "photo": "https://preproduction-persist.signzy.tech/api/files/28523817/download/.jpeg",
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
            "addressLine": "Address of the aadhaar holder"
        }
    }
}
```
{% endtab %}
{% endtabs %}



### **HTTP Response Codes**

| Status Code | Description     |                                                |
| ----------- | --------------- | ---------------------------------------------- |
| 304         | No Content      | Successfully Logged Out.                       |
| 400         | Token is Used   | URL is expired.                                |
| 400         | Token not found | Invalid Token or token is found in our system. |
