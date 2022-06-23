# Creating an URL

### **Introduction**

Firstly an URL will be created where the user will provide their Digilocker credentials on Digilocker iframe, and give consent that Signzy can download the file on the client's behalf.

### API Usecase

If you have a web-based application (be it mobile web or desktop web) you can access this through an **iframe**. In your mobile application, you can use web view. If you have integrated iframe-based payment gateways, you would find this to be very similar.

### How to call the API

Signzy provides a Digilocker iframe where the user enters the Digilocker credentials and once it is verified by a valid OTP sent to the registered mobile number user gets an access token from the login API call,  now user can send further calls to different endpoints by passing the access token in Authorization header or in the access token query (GET) parameter.

{% hint style="info" %}
User mobile number must be registered to his/her Aadhaar, to extract data using this API.&#x20;
{% endhint %}



### Steps to get URL

1. Open Digilocker iFrame
2. Enter Aadhaar number
3. Verify with the OTP sent on the registered mobile number
4.  **Load Digilocker Url**

    Once you receive the Digilocker Url.

    * Open the URL in a web browser.
    * In the case of a web app product, load the URL in the iframe
    * In the case of mobile APP, load the URL in the web view and you need to enable local storage in our APP. For Android, you can use this [link](https://stackoverflow.com/questions/5899087/android-webview-localstorage) to enable it.
    * Once URL is open, you have to enter your Digilocker credentials and give consent that Signzy can download the file on the client behalf
    * Once Signzy is authorized, a thank you page will be shown

![On Successful validation user will receive this message](<../../.gitbook/assets/thank u.jpg>)

> Once access is granted, Request ID will be generated which would be used further to call API's like, Get Aadhaar details, Get details of issued docs etc.

### Sample CURL request

```javascript
curl --location --request POST 'https://preproduction.signzy.tech/api/v2/patrons/<Your Patron ID>/digilockers' \
--header 'Authorization: AUTH' \
--header 'Content-Type: application/json' \
--header 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' \
--data-raw '{
    "task": "url"
}'
```

### Sample API Response

```javascript
{
    "id": "614aa215f0e8db4b7318XXXX",
    "patronId": "6140962af6d4030eae04XXXX",
    "task": "url",
    "result": {
        "url": "https://api.digitallocker.gov.in/public/oauth2/1/authorize?client_id=7E5773CXXXX_flow&redirect_uri=https%3A%2F%2Fdigilocker-preproduction.signzy.tech%2Fdigilocker-auth-complete&response_type=code&state=614aa21583e52667a11cXXXX",
        "requestId": "614aa1d183e52667a11cXXXX"
    }
}
```

### Input Parameters

| Parameter Name | Description                                                                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------------------- |
| Task           | Type of Tasks to be performed in Signzy System, eg: URL , GetData                                                     |
| Patron ID      | Unique ID for each patron. Which will be a alphanumeric value of 24 characters in length eg: 5a12eaf09fa3e67936b43c52 |
|                |                                                                                                                       |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
| URL            |             |
| Request ID     |             |

### Error Codes

| CODE | TITLE           | DESCRIPTION                                    |
| ---- | --------------- | ---------------------------------------------- |
| 304  | No Content      | Successfully Logged Out.                       |
| 400  | Token is Used   | URL is expired.                                |
| 400  | Token not found | Invalid Token or token is found in our system. |
