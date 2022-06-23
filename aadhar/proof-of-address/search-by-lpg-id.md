# Search by LPG ID (D)



You will need to [login](https://docs-staging.signzy.tech/) before sending request. You are required to pass the access token received from the login call, as authorization header in the LPG request along with lpgId.

Use the following exchange parameters for LPG based search by LPG ID



### Introduction

For Indian residents, this API can be used to retrieve the address proof of the registered LPG consumer with the help of the unique LPG consumer number provided. The API uses the consumer number to extract the details of the user.

### API Usecase

This API uses LPG ID of the user and provide the details of that particular user. It helps in auto-generating the details for the user without having to manually provide the information. Following information is generated:&#x20;

* Name
* Address
* District
* Pincode
* State
* Country

### How to call the API



### API Input Guidelines

* LPG ID



### Input Parameters

| Parameter Name | Description                                                                                |
| -------------- | ------------------------------------------------------------------------------------------ |
| accessToken    | (required, string) this is provided by the identities api                                  |
| task           | this value always remains fixed for Aadhaar extraction API, it is always `AutoRecognition` |
|                | ``                                                                                         |

### Output Parameters

| Parameter Name | Description |
| -------------- | ----------- |
|                |             |

****

### Sample CURL Request

**Step 1**: Hit Identities API

```
```

**Step 2:** Hit Snoops API and receives response

```
```

###

### Sample API Response

```
```



### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../lpgs" method="post" summary="Search LPG ID" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../lpgs`

\




\


This method is used to search consumer details using LPG ID
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token (returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="task" type="string" %}
Type of task to be performed - lpgidsearch
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.lpgId" type="string" %}
LPG ID of the individual
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
      "task" : "lpgidsearch",
      "essentials": {
        "lpgId" : "...lpgID..."
      },
      "id": "...accessToken...",
      "patronId": "...patronId...",
      "result": {
        "bankIfscCode": ".....IFSC Code of Bank Account linked with LPG.....",
        "consumerNo": ".....Consumer Number.....",
        "distributorName": ".....Distributor Name of the Consumer.....",
        "address": ".....Address of the Consumer.....",
        "aadhaarNumber": ".....Aadhaar Number of the Consumer.....",
        "consumerName": ".....Name of the Consumer.....",
        "optedOutOfSubsidy": ".....Subsidy Opted For.....",
        "distributorCode": ".....Code of the Distributor.....",
        "bankAccountLinkedToLpg": ".....Is bank Account Linked with LPG.....",
        "distributorDeliveryPerformanceRating": ".....Distributor Peformance Rating.....",
        "lastRefillBookingDate": ".....Date of Last Refill Booking.....",
        "aadhaarLinkedToBankAccount": ".....Whether Aadhaar is linked to Bank Account.....",
        "distributorAddress": ".....Address of the Distributor.....",
        "subsidizedRefillConsumed": ".....Number of subsidized Refill Consumed.....",
        "bankName": ".....Name of the bank.....",
        "mobileNo": ".....Registered mobile Number of the consumer.....",
        "aadhaarLinkedToLpgAccount": ".....Is Aaadhaar Linked with LPG.....",
        "emailId": ".....Registered Email-ID of the consumer.....",
        "approximateSubsidyAvailed": ".....Subsidy received by the consumer in rupees.....",
        "lpgId": "....lpgId of the Consumer.....",
        "consumerStatus": "....Status of the Consumer.....",
        "closingStockWithDistributor": "....Date on which Stock Closed on Distributor side.....",
        "bankAccountNo": "....Account Number of Bank Account linked with LPG.....",
        "totalRefillConsumed": "Total refill consumed",
        "consumerBase": ".... Base of the Consumer.............",
        "refillBookingStatus": "..........Status of Refill Booking...............",
        "splitAddress": {
          "state": [
            []
          ],
          "district": [],
          "city": [],
          "pincode": "...pincode...",
          "country": [
            "IN",
            "IND",
            "INDIA"
          ],
          "addressLine": "...addressLine..."
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

       "task" : "lpgidsearch",
       "essentials": {
         "lpgId" : "...lpgID..."
       }
     }

```


{% endtab %}

{% tab title="Response Parameters" %}
| PARAMETER NAME                              | DESCRIPTION                                                                                                                                                                                                                                                  |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| result                                      | This holds the final result parameters of the response.&#xD;                                                                                                                                                                                                 |
| result.bankIfscCode                         | IFSC code of the bank account that is linked with LPG is shown here.                                                                                                                                                                                         |
| result.consumerNo                           | The LPG consumer number is displayed here.                                                                                                                                                                                                                   |
| result.distributorName                      | This parameter displays the distributor name for the consumer.                                                                                                                                                                                               |
| result.address                              | The address information of the consumer is displayed here.                                                                                                                                                                                                   |
| result.aadhaarNumber                        | The Aadhaar Number of the consumer for the searched LPG ID.                                                                                                                                                                                                  |
| result.consumerName                         | The consumer name for whom the LPG ID is being searched.                                                                                                                                                                                                     |
| result.optedOutOfSubsidy                    | This parameter displays the LPG subsidy opted for by the consumer.                                                                                                                                                                                           |
| result.distributorCode                      | The code of the distributor for the particular consumer ID being searched.                                                                                                                                                                                   |
| result.bankAccountLinkedToLpg               | This parameter shows the bank account number which is linked to LPG.                                                                                                                                                                                         |
| result.distributorDeliveryPerformanceRating | The distributor delivery performance rating for the consumer ID being searched is displayed here                                                                                                                                                             |
| result.lastRefillBookingDate                | The last refill booking date for the LPG consumer is shown here.                                                                                                                                                                                             |
| result.aadhaarLinkedToBankAccount           | This parameter shows whether the bank account for the LPG ID has been linked to Aadhaar.                                                                                                                                                                     |
| result.distributorAddress                   | The distributor address for the registered LPG ID.                                                                                                                                                                                                           |
| result.subsidizedRefillConsumed             | This parameter displays the number of subsidized refills that have been consumed by the LPG consumer.                                                                                                                                                        |
| result.bankName                             | The bank name of the consumer is displayed here.                                                                                                                                                                                                             |
| result.mobileNo                             | The registered mobile number of the consumer.                                                                                                                                                                                                                |
| result.aadhaarLinkedToLpgAccount            | This parameter shows whether the LPG account has been linked to Aadhaar.                                                                                                                                                                                     |
| result.emailId                              | The email id of the LPG consumer.                                                                                                                                                                                                                            |
| result.approximateSubsidyAvailed            | This parameter is used to determine the subsidy received by the consumer in rupees.                                                                                                                                                                          |
| result.lpgId                                | The LPG ID of the consumer.                                                                                                                                                                                                                                  |
| result.consumerStatus                       | The current status of the LPG consumer is shown here.                                                                                                                                                                                                        |
| result.closingStockWithDistributor          | This parameter shows the date on which the stock was closed on the distributor side.                                                                                                                                                                         |
| result.bankAccountNo                        | The bank account number which is linked to LPG.                                                                                                                                                                                                              |
| result.totalRefillConsumed                  | The total refill that is consumed by the LPG consumer is displayed here.                                                                                                                                                                                     |
| result.consumerBase                         | This parameter gives the base of the consumer as output.                                                                                                                                                                                                     |
| result.refillBookingStatus                  | The current status of the refill Booking is shown as output here.                                                                                                                                                                                            |
| result.splitAddress                         | <p>This parameter displays the various parts of the address of the LPG ID holder by splitting them into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”</p><p></p> |
| result.addressLine                          | The first line of the registered consumer address is displayed here.                                                                                                                                                                                         |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/1ac4bb81cb71bf87c58d)

