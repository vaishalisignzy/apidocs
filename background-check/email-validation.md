# Email Validation

### Introduction

This API is used to validate an email ID  of an individual. This will check the name of the email id user, which domain it belongs to, what is the SMTP server address, etc.

### API Usecase

Email Validation API is very useful for getting the details of an email id. This helps to eliminate spams. We can get the IP address  of an email server where it has been sent. So incase of spam mail sent, we can contact the mail server admin & notify them.

### How to call the API

You are required to pass the access token received from the login call, as authorization header in the Email-ID Validation request along with Email-ID.

### API Input Guidelines

Full email id is required to complete the request.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/ optional | Description                          |
| -------------- | ------------------ | ------------------------------------ |
| emailId        | Required           | Valid email id                       |
| essentials     | Required           | Contains request data as JSON object |
{% endtab %}

{% tab title="Sample CURL Request" %}
```aspnet
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/emailverificationsv2' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{"essentials":{"emailId":"nikita.wasnik@signzy.com"}}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response parameters" %}
| PARAMETERS        | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| email             | emailID passed by the user                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| status            | whether the EmailID is valid or not.(returns string value i.e."valid \|invalid \|catch-all \|unknown \|spamtrap \|abuse \|do\_not\_mail")                                                                                                                                                                                                                                                                                                                                                                                           |
| sub-status        | Possible Values (\[antispam\_system \|greylisted \|mail\_server\_temporary\_error \|forcible\_disconnect \|mail\_server\_did\_not\_respond \|timeout\_exceeded \|failed\_smtp\_connection \|mailbox\_quota\_exceeded \|exception\_occurred \|possible\_traps \|role\_based \|global\_suppression \|mailbox\_not\_found \|no\_dns\_entries \|failed\_syntax\_check \|possible\_typo \|unroutable\_ip\_address \|leading\_period\_removed \|does\_not\_accept\_mail \|alias\_address \|role\_based\_catch\_all \|disposable \|toxic]) |
| account           | The portion of the email address before the "@" symbol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| domain            | The portion of the email address after the "@" symbol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| did\_you\_mean    | Suggestive Fix for an email typo                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| domain\_age\_days | Age of the email domain in days.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| free\_email       | If the email comes from a free provider (returns string value i.e."true/false").                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| mx\_found         | Does the domain have an MX record. (returns string value i.e."true/false").                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| mx\_record        | The preferred MX record of the domain.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| smtp\_provider    | The SMTP Provider of the email.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| firstname         | The first name of the owner of the email when available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| lastname          | The last name of the owner of the email when available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| gender            | The gender of the owner of the email when available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| city              | The city of the IP passed in.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| region            | The region/state of the IP passed in.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| zipcode           | The zipcode of the IP passed in.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| country           | The country of the IP passed in.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
{% endtab %}

{% tab title="Sample API Response" %}
```markup
{
    "essentials": {
        "emailId": "nikita.wasnik@signzy.com"
    },
    "id": "61432b30f6d4030eae05072b",
    "patronId": "614097a1f6d4030eae049781",
    "result": {
        "emailId": "nikita.wasnik@signzy.com",
        "validEmail": "true",
        "status": "deliverable",
        "subStatus": "",
        "freeEmail": "false",
        "didYouMean": "",
        "account": "nikita.wasnik",
        "domain": "signzy.com",
        "domainAgeDays": "2269",
        "smtpProvider": "g-suite",
        "mxFound": "true",
        "mxRecord": "aspmx.l.google.com",
        "personalDetails": {
            "name": "Nikita Wasnik",
            "email": "nikita.wasnik@signzy.com",
            "location": "Pune, MH, IN",
            "timeZone": "Asia/Kolkata",
            "bio": "",
            "avatar": "",
            "employment": "signzy.com",
            "socialMediaHandles": {
                "facebook": "",
                "github": "",
                "twitter": "",
                "linkedin": "in/nikita-wasnik-48a4a4184",
                "googleplus": "",
                "aboutme": "",
                "gravatar": ""
            }
        },
        "companyDetails": {
            "name": "Signzy",
            "legalName": "",
            "domain": "signzy.com",
            "domainAliases": [],
            "phoneNumbers": [],
            "emailAddresses": [
                "Dhwaneet@signzy.com",
                "compliance@signzy.com"
            ],
            "category": {
                "sector": "Information Technology",
                "industryGroup": "Software & Services",
                "industry": "Internet Software & Services",
                "subIndustry": "Internet Software & Services",
                "sicCode": "48",
                "naicsCode": "51"
            },
            "tags": [
                "Information Technology & Services",
                "Consulting & Professional Services",
                "Technology",
                "Financial Services",
                "Enterprise",
                "SAAS",
                "B2B"
            ],
            "description": "Accelerate Digital transformation using artificial intelligence. Make your digital onboarding hassle free using Video KYC and realtime negative data checks",
            "foundedYear": 2015,
            "location": "Arakere Bannerghatta Rd, Arekere, Bengaluru, Karnataka 560076, India",
            "linkedinHandle": "company/teamsignzy",
            "usEIN": "",
            "metrics": {
                "alexaUsRank": "",
                "alexaGlobalRank": 321846,
                "employeesRange": "51-250",
                "marketCap": "",
                "raised": 12600000,
                "annualRevenue": "",
                "estimatedAnnualRevenue": "$10M-$50M"
            }
        },
        "domainDetails": {
            "ip": "13.234.218.151",
            "continentCode": "NA",
            "countryCode": "US",
            "latitude": 38,
            "longitude": -97,
            "timezone": "",
            "domain": "",
            "status": "",
            "available": "",
            "registered": "",
            "domainId": "",
            "createdOn": "",
            "updatedOn": "",
            "expiresOn": "",
            "registrar": {
                "id": "",
                "name": "",
                "organization": "",
                "url": ""
            },
            "nameservers": []
        }
    }
}
```
{% endtab %}
{% endtabs %}

### HTTP Response Codes

| Status Code | Error Message               | Possible Fix                   |
| ----------- | --------------------------- | ------------------------------ |
| 200         | Successful                  | Nothing to fix                 |
| 400         | Missing or Invalid data     | Check all the input parameters |
| 401         | Authorization Required      | Check Authorization Header     |
| 404         | No method to handle request | Check URL endpoint of API      |
| 422         | Unprocessable Entity        | Notify our support team        |
