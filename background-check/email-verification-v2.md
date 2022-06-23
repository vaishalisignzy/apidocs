# Email Verification V2

### Introduction

An email id is often given to a person to verify his employment. This API will verify a given email address & show information from the email address like organization, domain, etc.

### API Usecase

This API will check if the email address is genuine or not and if it actually belongs to an organization that it claims. It will check the following things;

1. Email is active
2. Email domain is genuine
3. Domain belongs to the company claimed/ Return organization that it belongs to
4. Total employees in the org
5. Web presence

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the Email ID search request along with Email Id.

### API Input Guidelines

Full email id & access token are required for sending API request.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/ optional | Description                          |
| -------------- | ------------------ | ------------------------------------ |
| emailId        | Required           | full email id                        |
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
{% tab title="Response Parameters" %}
| PARAMETERS    | DESCRIPTION                                                                                               |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| emailId       | Email Id to be verified                                                                                   |
| validEmail    | returns true or false                                                                                     |
| status        | Returns the main status of the verification. It can take 2 possible values: Deliverable and Undeliverable |
| subStatus     | Extra information about the emailId                                                                       |
| freeEmail     | \[true/false] If the email comes from a free provider.                                                    |
| didYouMean    | Suggestive Fix for an email typo                                                                          |
| account       | The portion of the email address before the "@" symbol.                                                   |
| domain        | The portion of the email address after the "@" symbol.                                                    |
| domainAgeDays | Age of the email domain in days or null.                                                                  |
| smtpProvider  | The SMTP Provider of the email or null                                                                    |
| mxFound       | \[true/false] Does the domain have an MX record.                                                          |
| mxRecord      | The preferred MX record of the domain                                                                     |

#### personalDetails block

| PARAMETERS         | DESCRIPTION                                                               |
| ------------------ | ------------------------------------------------------------------------- |
| name               | Full formatted name of person.                                            |
| name               | Full name of person.                                                      |
| email              | Accurate work email for person.                                           |
| location           | City, State and/or Country of person.                                     |
| timeZone           | IANA time zone of person (ex: America/New\_York).                         |
| bio                | The most accurate person bio we surface from a variety of social sources. |
| avatar             | The best personal avatar we surface from a variety of social sources.     |
| employment         | Company name of person's employer.                                        |
| socialMediaHandles | Social Media Handles handle of person.                                    |

#### companyDetails block

| PARAMETERS                     | DESCRIPTION                                                                                    |
| ------------------------------ | ---------------------------------------------------------------------------------------------- |
| name                           | Name of company                                                                                |
| legalName                      | Legal name of company.                                                                         |
| domain                         | Domain of company’s website.                                                                   |
| domainAliases                  | List of domains that redirect to company's main domain.                                        |
| phoneNumbers                   | List of phone numbers that appear on company’s website.                                        |
| emailAddresses                 | List of email addresses that appear on the company’s website.                                  |
| category.sector                | Broadest tier of company's industry classification.                                            |
| category.industryGroup         | Second tier of company's industry classification.                                              |
| category.industry              | Third tier of company's industry classification.                                               |
| category.subIndustry           | Most specific tier of company's industry classification.                                       |
| category.sicCode               | Two digit company SIC (Standard Industry Classification) codes.                                |
| category.naicsCode             | Two digit company NAICS (North American Industry Classification System) codes.                 |
| tags                           | List of company vertical descriptors. Typically more granular than industry classification.    |
| description                    | Description of company.                                                                        |
| foundedYear                    | Year company was founded.                                                                      |
| location                       | Address of company headquarters.                                                               |
| linkedinHandle                 | LinkedIn handle of company.                                                                    |
| usEIN                          | US Employer Identification Number of company.                                                  |
| metrics.alexaUsRank            | US rank of company site traffic as calculated by Alexa (1 being the most trafficked site).     |
| metrics.alexaGlobalRank        | Global rank of company site traffic as calculated by Alexa (1 being the most trafficked site). |
| metrics.employeesRange         | Bucketed employee ranges for company (useful for segmentation).                                |
| metrics.marketCap              | Total market capitalization for company (public companies only).                               |
| metrics.raised                 | Total amount of funding raised by company.                                                     |
| metrics.annualRevenue          | Annual revenue for company (public companies only).                                            |
| metrics.estimatedAnnualRevenue | Our proprietary estimated annual revenue range for company.                                    |

#### domainDetails block

| PARAMETERS             | DESCRIPTION                                     |
| ---------------------- | ----------------------------------------------- |
| ip                     | Visitor IP address.                             |
| continentCode          | Two-letter continent code.                      |
| countryCode            | Two-letter ISO 3166-1 alpha-2 country code.     |
| latitude               | Latitude/                                       |
| longitude              | Longitude.                                      |
| timezone               | Timezone.                                       |
| domain                 | Domain Name                                     |
| status                 | Status of the Domain                            |
| available              | Availabilty of the domain                       |
| registered             | Registered or not, true or false                |
| domainId               | Unique Id of the domain                         |
| createdOn              | Created on date of the domain                   |
| updatedOn              | Updated on date of the domain                   |
| expiresOn              | Expiry date of the domain                       |
| registrar.id           | Registrar Id                                    |
| registrar.name         | Registrar Name                                  |
| registrar.organization | Registrar Organization                          |
| registrar.url          | Registrar URL                                   |
| nameservers            | List of NameServers associated with the Domain. |
| nameservers.name       | Name of the NameServers.                        |
| nameservers.ipv4       | IP of the NameServers in ipv4 format.           |
| nameservers.ipv6       | IP of the NameServers in ipv6 format.           |
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

