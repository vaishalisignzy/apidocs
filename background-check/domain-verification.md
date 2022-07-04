# Domain Verification

### Introduction

With the Domain Verification API, we can detect any fake domains & the authenticity of a domain, how old the domain, from which country it was registered, etc.

### API Usecase

The purpose of this service is to detect the existence of any fake/forged domain that may be used for malpractice or might not be created with the intended purpose. This service checks whether the website is authentic and is being used for conducting the business that it was intended for. This API will consider the following parameters to give the output:-

1. Whois records
2. Overall website and the main business
3. About Us - gives an idea of business
4. Terms of Service -gives an idea of business
5. SEO or page ranks - as tell about the business is being real or not.

### How to call the API

You are required have an authorization in the header & domain name in the request body.

### API Input Guidelines

Fully qualified domain name have to be given in the request body of the API.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name       | Required/ optional | Description                          |
| -------------------- | ------------------ | ------------------------------------ |
| webDomain            | Required           | String                               |
| essentials.negativew | optional           | List of negative words               |
| essentials           | Required           | Contains request data as JSON object |
{% endtab %}

{% tab title="Sample CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/domainverifications' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{"essentials":{"webDomain":"signzy.xyz"}}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
#### Output Parameters

| PARAMETERS                     | DESCRIPTION                                                          |
| ------------------------------ | -------------------------------------------------------------------- |
| name                           | Name of company of the entered domain                                |
| legalName                      | Legal name of company                                                |
| domain                         | Domain of company’s website                                          |
| domainAliases                  | List of domains also used by the company                             |
| site.title                     | Name                                                                 |
| site.h1                        | Header tag of the website                                            |
| site.metaDescription           | Description for the site                                             |
| site.metaAuthor                | Name of the Auther of the site                                       |
| site.phoneNumbers              | List of phone numbers mentioned on the company’s website             |
| site.emailAddresses            | List of email addresses mentioned on the company’s website           |
| category.sector                | Broad sector (see a complete list)                                   |
| category.industryGroup         | Industry group (see a complete list)                                 |
| category.industry              | Industry (see a complete list)                                       |
| category.subIndustry           | Sub industry (see a complete list)                                   |
| category.sicCode               | Two digit category SIC code                                          |
| category.naicsCode             | Two digit category NAICS code                                        |
| tags                           | List of market categories (see a complete list)                      |
| description                    | Description of the company                                           |
| foundedYear                    | Year company was founded                                             |
| location                       | Address of company                                                   |
| timeZone                       | The timezone for the company’s location                              |
| utcOffset                      | The offset from UTC in hours in the company’s location               |
| geo.streetNumber               | Headquarters street number                                           |
| geo.streetName                 | Headquarters street name                                             |
| geo.subPremise                 | Headquarters suite number                                            |
| geo.city                       | Headquarters city name                                               |
| geo.state                      | Headquarters state name                                              |
| geo.stateCode                  | Headquarters two character state code                                |
| geo.postalCode                 | Headquarters postal/zip code                                         |
| geo.country                    | Headquarters country name                                            |
| geo.countryCode                | Headquarters two character country code                              |
| geo.lat                        | Headquarters latitude                                                |
| geo.lng                        | Headquarters longitude                                               |
| logo                           | SRC of company logo                                                  |
| facebook.handle                | Company’s Facebook ID                                                |
| facebook.likes                 | Count of likes on Facebook                                           |
| linkedin.handle                | Company’s Linkedin URL                                               |
| twitter.handle                 | Twitter screen name                                                  |
| twitter.id                     | Twitter ID                                                           |
| twitter.bio                    | Twitter Bio                                                          |
| twitter.followers              | Count of Twitter followers                                           |
| twitter.following              | Count of Twitter friends                                             |
| twitter.location               | Twitter location                                                     |
| twitter.site                   | Twitter site                                                         |
| twitter.avatar                 | HTTP Twitter avatar                                                  |
| crunchbase.handle              | Crunchbase handle                                                    |
| emailProvider                  | It is the domain associated with a free email provider (i.e. Gmail)? |
| phone                          | International headquarters phone number                              |
| metrics.raised                 | Total amount raised                                                  |
| metrics.alexaUsRank            | Alexa’s US site rank                                                 |
| metrics.alexaGlobalRank        | Alexa’s global site rank                                             |
| metrics.employees              | Amount of employees                                                  |
| metrics.employeesRange         | Employees range (see a complete list)                                |
| metrics.marketCap              | Market Cap                                                           |
| metrics.annualRevenue          | Annual Revenue (public companies only)                               |
| metrics.estimatedAnnualRevenue | Estimated annual revenue range (see a complete list)                 |
| metrics.fiscalYearEnd          | Month that the fiscal year ends (1-indexed)                          |
| tech                           | Array of technology tags                                             |
| similarDomains                 | Similar domains list                                                 |
| parent.domain                  | The domain of the parent company (if any)                            |
{% endtab %}

{% tab title="Sample API Response" %}
```
{
    "essentials": {
        "webDomain": "signzy.xyz"
    },
    "id": "61433165f6d4030eae0508f0",
    "patronId": "614097a1f6d4030eae049781",
    "result": {
        "name": "",
        "legalName": "",
        "domain": "signzy.xyz",
        "domainAliases": [],
        "websiteBackgroundCheck": {},
        "wordAnalysis": {
            "totalCount": "",
            "wordFrequency": {}
        },
        "wordcloudImage": "",
        "site": {
            "title": "",
            "h1": "",
            "metaDescription": "",
            "metaAuthor": "",
            "phoneNumbers": [],
            "emailAddresses": []
        },
        "category": {
            "sector": "",
            "industry": "",
            "industryGroup": "",
            "subIndustry": "",
            "sicCode": "",
            "naicsCode": ""
        },
        "tags": [],
        "description": "",
        "foundedYear": "",
        "location": "",
        "timeZone": "",
        "utcOffset": "",
        "geo": {
            "streetNumber": "",
            "streetName": "",
            "subPremise": "",
            "city": "",
            "postalCode": "",
            "state": "",
            "stateCode": "",
            "country": "",
            "countryCode": "",
            "lat": "",
            "lng": ""
        },
        "logo": "",
        "facebook": {
            "handle": "",
            "likes": ""
        },
        "linkedin": {
            "handle": ""
        },
        "similarDomains": [],
        "twitter": {
            "handle": "",
            "id": "",
            "followers": "",
            "following": "",
            "location": "",
            "site": "",
            "avatar": "",
            "bio": ""
        },
        "crunchbase": {
            "handle": ""
        },
        "emailProvider": "false",
        "metrics": {
            "alexaGlobalRank": "6648858",
            "alexaUsRank": "",
            "googleRank": "",
            "employees": "",
            "employeesRange": "",
            "marketCap": "",
            "raised": "",
            "annualRevenue": "",
            "estimatedAnnualRevenue": "",
            "fiscalYearEnd": ""
        },
        "tech": [],
        "phone": "",
        "negativeWordResult": [],
        "parent": {
            "domain": ""
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
