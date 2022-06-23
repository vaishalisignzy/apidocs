# Contracting Workflow

### Product flow:

#### Contract:

A contract is created at the client end and the PDF for contract is passed into Signzy Contracting system. Signzy system responds with a URL for each of the signatories. These contract URLs are in turn provided to end customers where they can fill their signature and execute contract. The end product of Signzy Contracting System is a signed PDF with all necessary metadata and audit trail.

#### The process flow:

1. Client first hits Create contract API with the contract as PDF File.
   * The PDF can be provided as a URL or base64
   * Other details provided to this endpoint is the signatory details.
2. Contract process starts after the above API call is made.
   * The first signer gets a unique URL for signing the contract where he can apply his signature and execute.
   * Once the first signatory has executed the next signatory receives his direct URL for signing.
   * This process continues till all the signatories have signed.
   * Once all the signatory have signed the contract is said to be executed and signed contract PDF is posted to the callback URL (callback URL is provided in the contract creation request). This step marks end of contracting flow.
3. Client can avail the contract along with its metadata using the pull contract API call by passing contactId and customerId parameters
4. Client can choose to delete the contract from Signzy system once the contract is executed and its availability is not needed in Signzy system. Parameters contractId and customerId are passed mandatorily for the contract to be deleted.
5. Client can choose to delete a particular signer from a particular contract created earlier in the Signzy system. Parameters contractId ,customerId and signerEmail are passed mandatorily to identify the particular signer of the contract that is to be be deleted.

To see the exact details of each API endpoint and exact API request and response parameters, please refer the endpoint docs.\


![flow](https://docs-staging.signzy.tech/assets/images/contracting-flow1.jpg)

![flow](https://docs-staging.signzy.tech/assets/images/contracting-flow2.jpg)

### Customer Login

#### Authentication

**Authorizing your access**

Username and API key also acts like your key to the APIs. You need to have an access token for making any further API calls, which you can receive by logging in manually or programmatically using these credentials.

Signzy APIs adhere to authentication defined by Swagger 2.0 specifications. Each call to the APIs should include an 'Authorization' header or 'access\_token' query parameter for authentication.

You can find working examples at the bottom of this page.

**Logging in**

Logging in into the API services requires a simple HTTP call with authentication password. Following section mentions data to be input, expected output and meaning of fields.

{% swagger baseUrl="https://esign.signzy.tech" path="/api/customers/login" method="post" summary="Log In" %}
{% swagger-description %}
This method allows authentication during login.
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
        "id": "..accessToken..",
        "ttl": 1209600,
        "created": "2017-06-23T11:10:08.534Z",
        "userId": "..customerId.."
    }
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request Schema" %}
```
 {
      "username": "enter your valid username",
      "password": "enter your valid password"
    }
```
{% endtab %}

{% tab title="Response Parameters" %}

{% endtab %}
{% endtabs %}

**Sending authenticated requests**

Once you have an access token from the login API call, you can send further calls to different endpoints by passing the access-token in Authorization header or in access\_token query (GET) parameter.

It is advisable to send Access Token in header since, query parameters are sometimes saved in the log files thereby exposing vulnerabilities until the access\_token is deleted from sessions.

**Security**

Anybody with your API key/password or an Access Token generated using them can access all information you have created and also send requests on behalf of you.. It is strongly recommended to not send API-key/Password to client side and instead use reverse proxy to call Signzy APIs.

In case you think an access token is compromised, you should delete it using logout. Please inform us if your Signzy Password/API-key is compromised as soon as possible, so that we can disable & create new ones and prevent any misuse of your data.

**Logging out**

To logout you simply need to call the logout route with the access token in 'access\_token' query parameter or as 'Authorization' header.

```
// Logout
    For Test Credentials
    // POST :: https://contracting-preproduction.signzy.tech/api/customers/logout?access_token=...accessToken...
    For Production Credentials
    // POST :: https://contracting.signzy.tech/api/customers/logout?access_token=...accessToken...
    // Response is 204 status code with no content, indicating the Access-token has been deleted.
```

\
