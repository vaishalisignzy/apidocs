# Get Files

### **Introduction**

Signzy provides a Digilocker iframe where the user enters the Digilocker credentials and gives access to documents in Digilocker to the client.&#x20;

### API Usecase

If you have a web-based application (be it mobile web or desktop web) you can access this through an **iframe**. In your mobile application, you can use web view. If you have ever integrated iframe based payment gateways, you would find this to be very similar.

### How to call the API

Once you are logged in, you need to initiate Aadhaar Auth session by creating a web URL in the following manner.

### API Input Guidelines

* Request ID will be auto filled

### <mark style="color:blue;">Sample CURL Request</mark>

```
curl --location --request POST 'https:/signzy.tech/api/v2/patrons/<Patron ID>/digilockers' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "getDetails",
    "essentials": {
        "requestId": "<Unique File ID>"
    }
}'
```

****

### <mark style="color:green;">Sample API Response</mark>

```
{
    "essentials": {
        "requestId": "<Unique File ID>"
    },
    "id": "<Unique User ID>",
    "patronId": "<patron ID>",
    "task": "getDetails",
    "result": {
        "userDetails": {
            "digilockerid": "<Digilocker ID>",
            "name": "<Name of the holder>",
            "dob": "<D.O.B>",
            "gender": "M",
            "eaadhaar": "Y"
        },
        "files": [
            {
                "name": "Aadhaar Card",
                "type": "file",
                "size": "",
                "date": "03/11/2021",
                "parent": "",
                "mime": [
                    "application/pdf",
                    "application/xml"
                ],
                "doctype": "ADHAR",
                "description": "Aadhaar Card",
                "issuerid": "in.gov.uidai",
                "issuer": "Aadhaar, Unique Identification Authority of India",
                "id": "in.gov.uidai-ADHAR-6b931b93940cbc7a25a185229dfb6538"
            },
            {
                "name": "Class X Marksheet",
                "type": "file",
                "size": "",
                "date": "11/05/2020",
                "parent": "",
                "mime": [
                    "application/json",
                    "application/xml",
                    "application/pdf"
                ],
                "doctype": "SSCER",
                "description": "Class X Marksheet",
                "issuerid": "in.gov.cbse",
                "issuer": "Central Board of Secondary Education",
                "id": "in.gov.cbse-SSCER-51471032009"
            },
            {
                "name": "Class XII Marksheet",
                "type": "file",
                "size": "",
                "date": "11/05/2020",
                "parent": "",
                "mime": [
                    "application/json",
                    "application/xml",
                    "application/pdf"
                ],
                "doctype": "HSCER",
                "description": "Class XII Marksheet",
                "issuerid": "in.gov.cbse",
                "issuer": "Central Board of Secondary Education",
                "id": "in.gov.cbse-HSCER-76427922011"
            },
            {
                "name": "Class XII Migration Certificate",
                "type": "file",
                "size": "",
                "date": "11/05/2020",
                "parent": "",
                "mime": [
                    "application/pdf"
                ],
                "doctype": "HSMGR",
                "description": "Class XII Migration Certificate",
                "issuerid": "in.gov.cbse",
                "issuer": "Central Board of Secondary Education",
                "id": "in.gov.cbse-HSMGR-76417922011"
            },
            {
                "name": "Class XII Passing Certificate",
                "type": "file",
                "size": "",
                "date": "11/05/2020",
                "parent": "",
                "mime": [
                    "application/pdf"
                ],
                "doctype": "HPCER",
                "description": "Class XII Passing Certificate",
                "issuerid": "in.gov.cbse",
                "issuer": "Central Board of Secondary Education",
                "id": "in.gov.cbse-HPCER-76417922011"
            },
            {
                "name": "Driving License",
                "type": "file",
                "size": "",
                "date": "22/03/2020",
                "parent": "",
                "mime": [
                    "application/json",
                    "application/xml",
                    "application/pdf"
                ],
                "doctype": "DRVLC",
                "description": "Driving License",
                "issuerid": "in.gov.transport",
                "issuer": "Ministry of Road Transport and Highways",
                "id": "in.gov.transport-DRVLC-JH0920200008145"
            },
            {
                "name": "PAN Verification Record",
                "type": "file",
                "size": "",
                "date": "02/11/2019",
                "parent": "",
                "mime": [
                    "application/json",
                    "application/xml",
                    "application/pdf"
                ],
                "doctype": "PANCR",
                "description": "PAN Verification Record",
                "issuerid": "in.gov.pan",
                "issuer": "Income Tax Department",
                "id": "in.gov.pan-PANCR-GBHPS6194D"
            }
        ]
    }
}
```



### **HTTP Response Codes**

| Status Code | Description     |                                                |
| ----------- | --------------- | ---------------------------------------------- |
| 304         | No Content      | Sucessfully Logged Out.                        |
| 400         | Token is Used   | URL is expired.                                |
| 400         | Token not found | Invalid Token or token is found in our system. |
