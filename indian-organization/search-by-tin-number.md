# Search by TIN Number

TIN is an acronym for Taxpayer Identification Number, which is a unique number allotted by Commercial tax department of the respective State in which the business is registered.. It's an eleven digit number to be mentioned in all VAT/CST transactions and correspondence.&#x20;

The Search By TIN API by Signzy to retrieve the unique details like name and address of the business/dealer to which the TIN is registered. The TIN acts as the unique identifier and is the only input for the API service.

You will need to login before sending TIN Number request. You are required to pass the access token received from the login call, as authorization header in the TIN request along with tinNumber.

Use the following exchange parameters for TIN based search\


{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../tins" method="post" summary="Search by TIN Number" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/...patronID.../tins`



\




\


This method is used to search for business details using TIN Number.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
Contains the access token (returned as id field of login request)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.tinNumber" type="string" %}
The TIN number to be searched
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "essentials": {
    "tinNumber": "..tinNumber.."
  },
  "id": "...accessToken...",
  "patronId": "...patronId...",
  "result":  [{
           "cstStatus": "...cstStatus...",
           "pan": "...pan...",
           "status": "...status...",
           "ownerName": "...ownerName...",
           "dealer": "...dealer...",
           "address": "...address...",
           "regDate": "...regDate...",
           "cancelDate": "...cancelDate...",
           "splitAddress": {
               "district": [
                   "...district..."
               ],
               "state": [
                   [
                       "...state..."
                   ]
               ],
               "city": [
                   "...city..."
               ],
               "pincode": "...pincode...",
               "country": [
                   "IN",
                   "IND",
                   "INDIA"
               ],
               "addressLine": "...addressLine...",
           }
       }]
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
    "essentials": {
    	"tinNumber": ".....company's-tinNumber-to-search-for...."
    }
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME           | DESCRIPTION                                                                                                                                                                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| essentials               | This parameter contains the essential output data.                                                                                                                                                                                        |
| essentials.tinNumber     | The TIN number that is being searched.                                                                                                                                                                                                    |
| id                       | This parameter contains the access token received during login request.                                                                                                                                                                   |
| patronId                 | This parameter is returned as userId parameter of login request.                                                                                                                                                                          |
| result                   | This contains the final response parameters to be displayed.                                                                                                                                                                              |
| result.cstStatus         | The central sales tax status for the TIN number.                                                                                                                                                                                          |
| result.pan               | The PAN number of the TIN holder.                                                                                                                                                                                                         |
| result.status            | The status of the TIN is displayed here.                                                                                                                                                                                                  |
| result.ownerName         | The TIN holder name is displayed here.                                                                                                                                                                                                    |
| result.dealer            | The dealer name associated with the TIN.                                                                                                                                                                                                  |
| result.address           | The address of the business associated with the TIN is displayed here.                                                                                                                                                                    |
| result.regDate           | The registration date of the business associated with the TIN is displayed by this parameter.                                                                                                                                             |
| result.cancelDate        | The cancellation date for the TIN is mentioned here.                                                                                                                                                                                      |
| result.splitAddress      | This parameter distinguishes the various parts of the address of the TIN holder's business into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA” |
| splitAddress.addressLine | This parameter contains the first line of the address.                                                                                                                                                                                    |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/0369e7ba7056969a7ad1)
