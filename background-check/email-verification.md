# Email Verification

### Introduction

An email id is often given to a person to verify his employment. This API will verify a given email address & show information from the email address like organization, domain, full name, etc.

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

Need to pass the full email id & access token for sending API requests.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Description                          |
| -------------- | ----------------- | ------------------------------------ |
| essentials     | Required          | Contains request data as JSON object |
| emailId        | Required          | Any email id                         |


{% endtab %}

{% tab title="Sample CURL Request" %}
```aspnet
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<patron id>/emailvalidations' \
--header 'Content-Type: application/json' \
--header 'Authorization: <Authorization token>' \
--data-raw '{"essentials":{"emailId":"nikita.wasnik@signzy.com"}}'
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
#### **E**mail Verification block

| PARAMETERS             | DESCRIPTION                                                                                                                                                |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| validEmail             | whether the EmailID is valid or not.(returns string value i.e."true/false")                                                                                |
| emailValidationDetails | Gives the details of validation for email address                                                                                                          |
| result                 | Whether the Email address is deliverable or not.                                                                                                           |
| score                  | It is the deliverability score we give to the email address                                                                                                |
| email                  | It is the entered email address or the email address to look up                                                                                            |
| regexp                 | It is true if the email addresses pass our regular expression (returns string value i.e."true/false").                                                     |
| gibberish              | It is true if we find this is an automatically generated email address (for example "e65rc109q@company.com") (returns string value i.e."true/false").      |
| disposable             | It is true if we find this is an email address from a disposable email service (returns string value i.e."true/false").                                    |
| webmail                | It is true if we find this is an email from a webmail (for example Gmail) (returns string value i.e."true/false").                                         |
| mx\_records            | It is true if we find MX records exists on the domain of the given email address (returns string value i.e."true/false").                                  |
| smtp\_server           | It is true if we connect to the SMTP server successfully (returns string value i.e."true/false").                                                          |
| smtp\_check            | It is true if the email address doesn't bounce (returns string value i.e."true/false").                                                                    |
| accept\_all            | It is true if the server accept all the email addresses. It mean you can have have false positives on SMTP checks (returns string value i.e."true/false"). |

#### personalInfo block

| PARAMETERS           | DESCRIPTION                                                                                                        |
| -------------------- | ------------------------------------------------------------------------------------------------------------------ |
| name.fullName        | Full formatted name of person. Sometimes this will be present even if the givenName or familyName aren’t available |
| name.givenName       | First name of person (if found)                                                                                    |
| name.familyName      | Last name of person (if found).                                                                                    |
| email                | It is the entered email address                                                                                    |
| gender               | Gives gender of the person (returns string value i.e."male or female").                                            |
| location             | The most accurate location we have                                                                                 |
| timeZone             | The timezone for the person’s location                                                                             |
| utcOffset            | The offset from UTC in hours in the person’s location.                                                             |
| geo.city             | Normalized city based on location                                                                                  |
| geo.state            | Normalized state based on location.                                                                                |
| geo.country          | Normalized country based on location                                                                               |
| geo.stateCode        | two character state code based on location.                                                                        |
| geo.countryCode      | Normalized two letter country code based on location                                                               |
| geo.lat              | General latitude based on location.                                                                                |
| geo.lng              | General longitude based on location                                                                                |
| bio                  | The most accurate bio we have                                                                                      |
| site                 | The person’s website                                                                                               |
| avatar               | The best avatar url we have                                                                                        |
| employment.name      | Company name                                                                                                       |
| employment.title     | Title at Company                                                                                                   |
| employment.role      | Role at Company                                                                                                    |
| employment.seniority | Seniority at Company                                                                                               |
| employment.domain    | Company domain                                                                                                     |
| facebook.handle      | Facebook ID or screen name                                                                                         |
| github.handle        | GitHub handle                                                                                                      |
| github.id            | GitHub ID                                                                                                          |
| github.avatar        | GitHub avatar                                                                                                      |
| github.company       | GitHub company                                                                                                     |
| github.blog          | GitHub blog url                                                                                                    |
| github.followers     | Count of GitHub followers                                                                                          |
| github.following     | Count of GitHub following                                                                                          |
| twitter.handle       | Twitter screen name                                                                                                |
| twitter.id           | Twitter ID                                                                                                         |
| twitter.followers    | Count of Twitter followers                                                                                         |
| twitter.following    | Count of Twitter friends                                                                                           |
| twitter.location     | Twitter location                                                                                                   |
| twitter.site         | Twitter site                                                                                                       |
| twitter.statuses     | Tweet count                                                                                                        |
| twitter.favorites    | Favorite count                                                                                                     |
| twitter.avatar       | HTTP Twitter avatar                                                                                                |
| linkedin.handle      | LinkedIn url (i.e. /pub/alex-maccaw/78/929/ab5)                                                                    |
| googleplus.handle    | Google Plus handle                                                                                                 |
| aboutme.handle       | about.me handle                                                                                                    |
| aboutme.bio          | about.me bio                                                                                                       |
| aboutme.avatar       | about.me avatar URL                                                                                                |
| gravatar.handle      | Gravatar handle                                                                                                    |
| gravatar.urls        | Array of URLs from Gravatar                                                                                        |
| gravatar.avatar      | Gravatar main avatar url.                                                                                          |
| gravatar.avatars     | Array of objects containing a avatar url, and a type (i.e. thumbnail)                                              |
| fuzzy                | Indicating whether or not the lookup is a fuzzy or exact search                                                    |
| emailProvider        | is the email domain associated with a free email provider (i.e. Gmail)?                                            |
| indexedAt            | The time at which we indexed this data                                                                             |

#### company block

| PARAMETERS                     | DESCRIPTION                                                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------ |
| name                           | Name of company                                                                            |
| legalName                      | Legal name of company                                                                      |
| domain                         | Domain of company’s website                                                                |
| domainAliases                  | List of domains also used by the company                                                   |
| site.phoneNumbers              | List of phone numbers mentioned on the company’s website                                   |
| site.emailAddresses            | List of email addresses mentioned on the company’s website                                 |
| category.sector                | Broad sector (see a complete list)                                                         |
| category.industryGroup         | Industry group (see a complete list)                                                       |
| category.industry              | Industry (see a complete list)                                                             |
| category.subIndustry           | Sub industry (see a complete list)                                                         |
| category.sicCode               | Two digit category SIC code                                                                |
| category.naicsCode             | Two digit category NAICS code                                                              |
| tags                           | List of market categories (see a complete list)                                            |
| description                    | Description of the company                                                                 |
| foundedYear                    | Year company was founded                                                                   |
| location                       | Address of company                                                                         |
| timeZone                       | The timezone for the company’s location                                                    |
| utcOffset                      | The offset from UTC in hours in the company’s location                                     |
| geo.streetNumber               | Headquarters street number                                                                 |
| geo.streetName                 | Headquarters street name                                                                   |
| geo.subPremise                 | Headquarters suite number                                                                  |
| geo.city                       | Headquarters city name                                                                     |
| geo.state                      | Headquarters state name                                                                    |
| geo.stateCode                  | Headquarters two character state code                                                      |
| geo.postalCode                 | Headquarters postal/zip code                                                               |
| geo.country                    | Headquarters country name                                                                  |
| geo.countryCode                | Headquarters two character country code                                                    |
| geo.lat                        | Headquarters latitude                                                                      |
| geo.lng                        | Headquarters longitude                                                                     |
| logo                           | SRC of company logo                                                                        |
| facebook.handle                | Company’s Facebook ID                                                                      |
| facebook.likes                 | Count of likes on Facebook                                                                 |
| linkedin.handle                | Company’s Linkedin URL                                                                     |
| twitter.handle                 | Twitter screen name                                                                        |
| twitter.id                     | Twitter ID                                                                                 |
| twitter.bio                    | Twitter Bio                                                                                |
| twitter.followers              | Count of Twitter followers                                                                 |
| twitter.following              | Count of Twitter friends                                                                   |
| twitter.location               | Twitter location                                                                           |
| twitter.site                   | Twitter site                                                                               |
| twitter.avatar                 | HTTP Twitter avatar                                                                        |
| crunchbase.handle              | Crunchbase handle                                                                          |
| emailProvider                  | It is the domain associated with a free email provider (i.e. Gmail)?                       |
| type                           | The company’s type, either education, government, nonprofit, private, public, or personal. |
| ticker                         | Stock ticker symbol                                                                        |
| identifiers.usEIN              | US Employer Identification Number                                                          |
| phone                          | International headquarters phone number                                                    |
| metrics.raised                 | Total amount raised                                                                        |
| metrics.alexaUsRank            | Alexa’s US site rank                                                                       |
| metrics.alexaGlobalRank        | Alexa’s global site rank                                                                   |
| metrics.employees              | Amount of employees                                                                        |
| metrics.employeesRange         | Employees range (see a complete list)                                                      |
| metrics.marketCap              | Market Cap                                                                                 |
| metrics.annualRevenue          | Annual Revenue (public companies only)                                                     |
| metrics.estimatedAnnualRevenue | Estimated annual revenue range (see a complete list)                                       |
| metrics.fiscalYearEnd          | Month that the fiscal year ends (1-indexed)                                                |
| indexedAt                      | The time at which we indexed this data                                                     |
| tech                           | Array of technology tags                                                                   |
| parent.domain                  | The domain of the parent company (if any)                                                  |

#### domainResult block

| PARAMETERS      | DESCRIPTION                                                     |
| --------------- | --------------------------------------------------------------- |
| continent\_code | Continent code for the continent                                |
| continent       | List of continents with continent code.                         |
| country\_code   | The country code is defined in the ISO 3166-1 alpha-2 standard. |
| country         | List of country with country code.                              |
| emailId         | It is the entered email address.                                |
| domain          | domain name of the email address.                               |
{% endtab %}

{% tab title="Sample API Response" %}
```markup
{
    "essentials": {
        "emailId": "nikita.wasnik@signzy.com"
    },
    "id": "61432799f6d4030eae050638",
    "patronId": "614097a1f6d4030eae049781",
    "result": {
        "emailverifyData": {
            "email": "nikita.wasnik@signzy.com",
            "status": "valid",
            "sub_status": "",
            "free_email": "false",
            "did_you_mean": "",
            "account": "nikita.wasnik",
            "domain": "signzy.com",
            "domain_age_days": "2269",
            "smtp_provider": "g-suite",
            "mx_found": "true",
            "mx_record": "aspmx.l.google.com",
            "gender": "female",
            "country": "",
            "region": "",
            "city": "",
            "zipcode": "",
            "firstname": "NIKITA",
            "lastname": "WASNIK",
            "name": "NIKITA WASNIK"
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
