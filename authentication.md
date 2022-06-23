# Authentication

**Authentication is the method which ensures primarily two things:**

* The credentials provided by you are authentic to you alone. i.e it is not misused by any one in any other way
* A secure login and logout from the system so that your account information is not compromised in any way

Signzy always ensures user authenticity with the help of a unique username and an API key that is specifically tailored to individual clients. The key also acts like your password to the APIs. You need to have an access token for making any further API calls, which you can receive by logging in manually or through a program using these credentials. These helps users maintain the authenticity of their credentials and provides hassle-free use without any difficulty.

Signzy APIs adhere to authentication defined by Swagger 2.0 specifications. The Swagger specification defines a set of files required to describe API’s like this (RESTful API’s). As per the guidelines, each call to the APIs should include an 'Authorization' header or 'access\_token' query parameter for authentication.&#x20;



**Logging in**

The first step is to log in to the API service with the credentials that have been provided to you. This requires a simple HTTP call. The code below mentions data to be input, expected output and meaning of fields.

{% swagger baseUrl="https://signzy.tech" path="/api/v2/patrons/login" method="post" summary="Data Exchange" %}
{% swagger-description %}
This method allows authentication during login and logout.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="string" %}
The username for the user
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" type="string" %}
The password for the user
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
    "id": "...accessToken...",
    "ttl": ..ttl..,
    "created": "..created..",
    "userId": "..patronId..."
  }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
{
    "username": "..username..",
    "password": "..password.."
  }
```
{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME | DESCRIPTION                                                             |
| -------------- | ----------------------------------------------------------------------- |
| id             | This is the access token used for accessing Signzy APIs.                |
| ttl            | This denotes the number of seconds for which the access token is valid. |
| created        | The login creation was successful.                                      |
| userId         | This is the userId as assigned to file.                                 |
{% endtab %}
{% endtabs %}

Logging in into the API service requires a simple HTTP call. Following section mentions data to be input, expected output and meaning of fields.

**Sending authenticated requests**

As discussed in the previous section, users can easily send requests to other endpoints of the API service after receiving the access token from the login API call. This can be done in two ways:

* By passing the access-token in the Authorization header&#x20;
* By creating an access\_token query (GET) parameter.

However, the second method is not commonly used as the query parameters are sometimes saved in the log files, thereby exposing vulnerabilities until the access\_token is deleted from sessions.&#x20;

**Security**

An important aspect to remember while using the API key/password is that anybody with your API key/password or an Access Token generated using them can access all the information you have created and also send requests on your behalf. Therefore, it is highly recommended that the API-key/Password is not provided to client side. Instead, we can make use of a reverse proxy to call Signzy APIs.

In case you think an access token is compromised, you should delete it using logout. Let us know if your Signzy Password/API-key is compromised as soon as possible, so that we can disable & create new ones and prevent any misuse of your data.

**Logging out**

To logout you simply need to call the logout route with the access token in 'access\_token' query parameter or as 'Authorization' header.

```
 // Logout
    For Test Credentials
    // POST :: https://preproduction.signzy.tech/api/v2/patrons/logout?access_token=...accessToken...
    For Production Credentials
    // POST :: https://signzy.tech/api/v2/patrons/logout?access_token=...accessToken...
    // Response is 204 status code with no content, indicating the Access-token has been deleted.
```

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/8adcfff50cd73a1f229c)
