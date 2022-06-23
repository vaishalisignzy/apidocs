# EZMatch

### Introduction

The EZMATCH Payment Facilitator service is an external API that assists the Payment Facilitator's ability to consider the merchants terminated and merchants inquired.

### API Usecase

EZMATCH can provide the Payment Facilitator with all relevant data, such as, if a Merchant or individual has been terminated by another acquirer already, the reason for termination, the history of fraudulent or risky business practices that led to that termination and the inquiry that was made already on the Merchant or individual by own or another acquiring bank.

Signzy makes use of the EZMATCH API for forgery detection and ensures that none of the Merchants or individuals is fraudulent as an initiative to make authenticity more convenient.

### How to call the API

You are required to pass the access token received from the login call, an authorization header in the request for Risk API along with other parameters.

### API Input Guidelines

Acquirer Id is required along with name & address to check the risk score.

### Input Parameters & CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| PARAMETERS             | Required/ Optional | DESCRIPTION                                                                                                                      |
| ---------------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| acquirerId             | Required           | Acquirer Id of the bank                                                                                                          |
| merchant               | Required           | Merchant Information                                                                                                             |
| address                | Required           | The address of the business(merchant)                                                                                            |
| line1                  | Required           | addressline of the business(merchant)                                                                                            |
| line2                  | Optional           | additional addressline of the business(merchant)                                                                                 |
| city                   | Required           | city of the business(merchant)                                                                                                   |
| countrySubdivision     | Optional           | <p>countrySubdivision of the business(merchant)</p><p><strong>Note:</strong>  Compulsory only when countrycode is USA or CAN</p> |
| country                | Required           | country of the business(merchant)                                                                                                |
| postalCode             | Required           | postalCode of the business(merchant)                                                                                             |
| name                   | Required           | Name of the business(merchant).                                                                                                  |
| doingBusinessAsName    | Optional           | Doing Business As Name of the business(merchant).                                                                                |
| principal              | Required           | Principal Information of the business                                                                                            |
| firstName              | Required           | First Name of the the principal owner of the business(principal)                                                                 |
| lastName               | Required           | Last Name of the the principal owner of the business(principal)                                                                  |
| phoneNumber            | Optional           | Phone Number of the the principal owner of the business(principal)                                                               |
| driversLicense         | Optional           | Drivers License of the the principal owner of the business(principal)                                                            |
| driversLicenseNumber   | Optional           | Drivers License Number of the the principal owner of the business(principal)                                                     |
| driversLicenseCountry  | Optional           | Drivers License Country of the the principal owner of the business(principal)                                                    |
| driversLicenseProvince | Optional           | Drivers License Province of the the principal owner of the business(principal)                                                   |
| address                | Required           | The address of the principal owner of the business(principal)                                                                    |
| line1                  | Required           | addressline of the principal owner of the business(principal)                                                                    |
| line2                  | Optional           | additional addressline of the principal owner of the business(principal)                                                         |
| city                   | Required           | city of the principal owner of the business(principal)                                                                           |
| countrySubdivision     | Required           | countrySubdivision of the principal owner of the business(principal)                                                             |
| country                | Required           | country of the principal owner of the business(principal)                                                                        |
| postalCode             | Required           | postalCode of the principal owner of the business(principal)                                                                     |
| serviceProvLegal       | Optional           | Service Provider Legal Name of the business                                                                                      |
| searchCriteria         | Required           | Search Criteria                                                                                                                  |
| searchAll              | Required           | Search All Flag for Search Criteria                                                                                              |
| minPossibleMatchCount  | Required           | Minimum Possible Merchant Count for Search Criteria                                                                              |
{% endtab %}

{% tab title="Sample CURL Request" %}
```
```
{% endtab %}
{% endtabs %}

### Output Parameters & API Response

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETERS                  | DESCRIPTION                                                                                                                                                                                                                                                           |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| numberOfTerminatedMerchants | Determines how many minimum matches are needed for a merchant or inquiry to appear in the results.                                                                                                                                                                    |
| addedByAquirerID            | The Member ICA that has added the merchant to the MATCH system                                                                                                                                                                                                        |
| addedOnDate                 | The date on which the merchant was added to the MATCH system. Format: MM/DD/YYY                                                                                                                                                                                       |
| terminationReasonCode       | A two digit numeric code indication why a particular merchant was terminated.                                                                                                                                                                                         |
| terminationReasonMessage    | Description of terminationReasonCode                                                                                                                                                                                                                                  |
| urlGroup                    |                                                                                                                                                                                                                                                                       |
| exactMatchUrls              |                                                                                                                                                                                                                                                                       |
| url                         | The exactly matched URL of Merchant. The results may return 0 or more URLs.                                                                                                                                                                                           |
| urlDetails                  |                                                                                                                                                                                                                                                                       |
| severity                    | The Severity of the match as set by the Acquirer Bank.                                                                                                                                                                                                                |
| status                      | The current status of the match set be the Acquirer Bank. "NotCleared" items require review by the Payment Facilitator or Acquirer depending on Acquirer configuration. Allowed values: "Cleared", "NotCleared", "ConfirmedHit"                                       |
| closeMatchUrls              | The closely matched URL of Merchant. The results may return 0 or more URLs.                                                                                                                                                                                           |
| noMatchUrls                 | The unmatched URL of Merchant.The results may return 0 or more URLs.                                                                                                                                                                                                  |
| name                        | The name of the Business which has been terminated.                                                                                                                                                                                                                   |
| doingBusinessAsName         | The name used by a merchant that could be different from the legal name of the business. Such as Bait R Us instead of the legal name, The Bait Shop.                                                                                                                  |
| address                     |                                                                                                                                                                                                                                                                       |
| line1                       | Line 1 of the street address for the Merchant's location. Usually includes street number and name.                                                                                                                                                                    |
| line2                       | Line 2 of the street address, usually an apartment number or suite number.                                                                                                                                                                                            |
| city                        | The name of the city for a merchant location.                                                                                                                                                                                                                         |
| countrySubdivision          | The abbreviated state or countrySubdivision code for a merchant location (only supported for US and Canada merchants)                                                                                                                                                 |
| postalCode                  | The US Post Office Zip Code for the address of the merchant; if outside the U.S. region, the approved postal code for that country will be used.                                                                                                                      |
| country                     | The country code for a country                                                                                                                                                                                                                                        |
| countrySubdivisionTaxId     | The Merchant's state tax ID; for the U.S region only. Return value will be obfuscated.                                                                                                                                                                                |
| phoneNumber                 | The Business or Merchant's phone number.                                                                                                                                                                                                                              |
| altPhoneNumber              | The Business or Merchant's alternate phone number.                                                                                                                                                                                                                    |
| countrySubdivisionTaxId     | The Merchant's state tax ID; for the U.S region only. Return value will be obfuscated                                                                                                                                                                                 |
| nationalTaxId               | The National tax ID or business registration number. Return value will be obfuscated                                                                                                                                                                                  |
| serviceProvLegal            | The name of the service provider associated with the merchant listed in the MATCH                                                                                                                                                                                     |
| serviceProvDBA              | The name of the service provider associated with the merchant listed in the MATCH                                                                                                                                                                                     |
| principal                   |                                                                                                                                                                                                                                                                       |
| firstName                   | The first name of a principal owner. Return value will be obfuscated when the Termination of the Merchant was due to Identity Theft. The results may return up to 5 principal owners.                                                                                 |
| lastName                    | The last name of a principal owner. Return value will be obfuscated when the Termination of the Merchant was due to Identity Theft. The results may return information for up to 5 principal owners.                                                                  |
| nationalId                  | Social Security of a principal owner; if outside the U.S. Region, the national ID card number; may return up to 5 principal owners Social Security or National Ids. The results may return information for up to 5 principal owners. Return value will be obfuscated. |
| phoneNumber                 | The phone number of a principal owner. The results may return information for up to 5 principal owners.                                                                                                                                                               |
| altPhoneNumber              | The alternate phone number of a principal owner. The results may return information for up to 5 principal owners.                                                                                                                                                     |
| address                     |                                                                                                                                                                                                                                                                       |
| line1                       | Line 1 of the street address for the principal owner location. Usually includes street number and name.                                                                                                                                                               |
| line2                       | Line 2 of the street address, usually an apartment number or suite number.                                                                                                                                                                                            |
| city                        | The name of the city for a principal owner.                                                                                                                                                                                                                           |
| countrySubdivision          | The abbreviated state or countrySubdivision code for a principal owner location (only supported for US and Canada merchants).                                                                                                                                         |
| postalCode                  | The US Post Office Zip code for the address of the principal owner; If outside the U.S. region, the approved postal code.                                                                                                                                             |
| country                     | The country code for a country.                                                                                                                                                                                                                                       |
| driversLicense              |                                                                                                                                                                                                                                                                       |
| number                      | The driver's license number of a principal owner. The results may return up to 5 principal owner drivers' licenses.                                                                                                                                                   |
| countrySubdivision          | The state or countrySubdivision the principal owners driver's license was issued in; U.S. Region and Canada only                                                                                                                                                      |
| country                     | The country code of the country the principal owners driver's license was issue in.                                                                                                                                                                                   |
| merchantMatch               | Describes if the data input matches any data within the MATCH service                                                                                                                                                                                                 |
| merchantInquiryMatch        | Describes if the data input matches any inquiry data within the MATCH service                                                                                                                                                                                         |
{% endtab %}

{% tab title="Sample API Response" %}
```
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
