# Search by Vehicle No. (aka RC No.)

### Introduction

This service is used for retrieving the details of vehicle registration and owner details by simply entering the vehicle registration number.

### API Usecase

This API uses the Vehicle number of the user's vehicle and will provide the details of that particular vehicle. It helps in auto-generating the details for the vehicle without having to manually provide the information. This API provides detailed information about the vehicle searched for.

### How to call the API

You will need to log in before sending the request. You are required to pass the access token received from the login call, as the authorization header in the request.

### API Input Guidelines

* Provide correct Vehicle Number

### <mark style="color:blue;">Sample CURL Request</mark>

{% tabs %}
{% tab title="Input parameters" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                        |
| ------------------- | ------------------------------------------------------ |
| task                | <p>The type of task performed - “Basic Search”<br></p> |
| essentials          | Contains the essential output data                     |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/<Patron ID>/vehicleregistrations' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "basicSearch",
    "essentials": {
        "vehicleNumber": "<Vehicle Number to be searched>"
    }
}'
```
{% endtab %}
{% endtabs %}

###

### <mark style="color:green;">API Sample Parameters and Response</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME          | DESCRIPTION                                                                                                |
| ----------------------- | ---------------------------------------------------------------------------------------------------------- |
| result                  | This holds the final result parameters of the response.                                                    |
| result.foundAt          | This parameter returns the information of the location to where the vehicle is registered.                 |
| result.registrationNo   | This parameter returns the vehicle registration number,                                                    |
| result.registrationDate | This parameter displays the date of registration of the vehicle registration number.                       |
| result.chassisNo        | The chassis number of the registered vehicle is displayed.                                                 |
| result.engineNo         | The engine number of the registered vehicle is displayed in this parameter.                                |
| result.ownerName        | The owner name of the vehicle that is being searched.                                                      |
| result.vehicleClass     | The class of vehicle for which the vehicle number is being searched.                                       |
| result.fuel             | The type of fuel consumed by the vehicle being searched is displayed here.                                 |
| result.makerModel       | The maker model details of the vehicle that is being searched.                                             |
| result.fitnessUpto      | This parameter contains the date upto which the vehicle fitness is certified.                              |
| result.insuranceUpto    | This parameter holds the insurance details of the vehicle number being searched.                           |
| result.pollutionNorms   | The pollution norms details are shown here along with the status of the vehicle under the pollution norms. |
| result.status           | The current status of the registered vehicle is displayed here.                                            |
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "essentials": {
        "vehicleNumber": "MH12BG7237"
    },
    "id": "<Request ID>",
    "patronId": "<Patron ID>",
    "task": "basicSearch",
    "result": {
        "foundAt": "PUNE, MAHARASHTRA",
        "registrationNo": "MH12BG7237",
        "registrationDate": "20/06/2002",
        "chassisNo": "MA3EBE41S002XXXXX",
        "engineNo": "G3BBN1XXXXX",
        "ownerName": "VISHAL PIPARAIYA",
        "vehicleClass": "MOTOR CAR (LMV)",
        "fuel": "PETROL",
        "makerModel": "MARUTI SUZUKI INDIA LTD / MARUTI  ESTEEM",
        "fitnessUpto": "20/06/2022",
        "insuranceUpto": "30/11/2017",
        "pollutionNorms": "NOT AVAILABLE",
        "status": "ACTIVE",
        "vehicleNumber": "MH12BG7237",
        "splitPermanentAddress": {
            "district": [],
            "state": [
                []
            ],
            "city": [],
            "pincode": "",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": ""
        },
        "splitPresentAddress": {
            "district": [],
            "state": [
                []
            ],
            "city": [],
            "pincode": "",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": ""
        }
    }
}
```
{% endtab %}
{% endtabs %}



### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |

### &#xD;

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/298c9fc80c0e52b6031d)
