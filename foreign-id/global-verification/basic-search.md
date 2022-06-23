# Basic Search

This is a unique API that conducts a verification of details against residents of foreign countries like USA, Canada, Australia and South Africa. The purpose of this API is to accept the Name, ID number, Phone Number, DOB, Country Name and ZIP code as input and conduct a verification process for the user whose details are being searched.

You will need to login before sending Global Verification Basic Search API request. You are required to pass the access token received from the login call, as authorization header in the request for Global Verification Basic Search API along with other parameters.

Use the following exchange parameters for Mobile Number based search

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/...patronID.../globalverifications" method="post" summary="Basic Global Search" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your patron id../globalverifications`

\




\


This method is used to extract the details of a foreign national using mobile number.
{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" type="string" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorisation" type="object" %}
Contains the access token which is returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Task to be performed - basic Search
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains the input details like name, idnumber, dob, phonenumber postal code and country of the individual being searched.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
	"result": {
          "address": {
            "reliability": "...reliability...",
            "adaptation": "...adaptation...",
            "messages": [
              {
                "code": "...code...",
                "value": "...value..."
              }
            ]
          },
          "identity": {
              "reliability": "...reliability...",
              "adaptation": "...adaptation...",
              "messages": [
                {
                  "code": "...code...",
                  "value": "...value..."
                }
              ]
          },
          "phone": {
              "reliability": "...reliability...",
              "adaptation": "...adaptation...",
              "messages": [
                {
                  "code": "...code...",
                  "value": "...value..."
                }
              ]
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
 	"task" : "basicSearch",
   "essentials": {
       "name": "...name...",
       "idNumber": "...idNumber...",
       "dob": "...dob...",
       "phoneNumber": "...phoneNumber...",
       "postalCode": "...postalCode...",
       "country": "...country..."
   }
 }
```
{% endtab %}
{% endtabs %}



#### Input Parameters

| PARAMETERS  | DESCRIPTION                     | TYPE   | VALUE (COMPULSORY OR OPTIONAL) |
| ----------- | ------------------------------- | ------ | ------------------------------ |
| name        | Name to be Seached              | String | COMPULSORY                     |
| country     | Country of the individual       | String | COMPULSORY                     |
| idNumber    | ID Number of the individual     | String | OPTIONAL                       |
| dob         | Date of Birth of the individual | String | OPTIONAL                       |
| phoneNumber | Phone Number of the individual  | String | OPTIONAL                       |
| postalCode  | Postal Code of the individual   | String | OPTIONAL                       |
