# Search by Electricity Consumer No.(404)

### Introduction

For Indian residents, this API can be used to retrieve the registered Electricity consumer information with the help of the unique Electricity consumer number provided by the department. This API uses the consumer number paired with the appropriate electricity supplying organization to extract the address proof details of the user.

### API Usecase

This API uses the **Consumer number** and name of the **Electricity board** of the user and provides the details of that particular user. It helps in auto-generating the details for the user without having to manually provide the information. The following information is generated:&#x20;

* Name:&#x20;
* Address:
* Amount Payable:
* BillAmount:
* BillDate:
* BillDueDate:
* BillIssueDate:
* Bill No:
* Consumer No:&#x20;
* Email:
* Mobile Number:
* AccountId:
* BillingUnit:
* ConsumptionUnits:
* ElectricityProvider:

### How to call the API

You will need to log in before sending the request. You are required to pass the access token received from the login call, as an authorization header.



### API Input Guidelines

* Consumer number
* Electricity board



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

{% swagger baseUrl="https://preproduction.signzy.tech" path="/api/v2/patrons/..your-patron-id../electricitybills" method="post" summary="Search Electricity Consumer ID" %}
{% swagger-description %}
**Production URL:**

\




`https://signzy.tech/api/v2/patrons/..your-patron-id../electricitybills`

\




\


This method is used to search consumer details using Electricity Consumer Number
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="object" %}
access token (returned as id field of login request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" type="object" %}
Application/JSON
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials" type="object" %}
Contains essential Input data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.consumerNO" type="object" %}
Consumer Number of the individual
{% endswagger-parameter %}

{% swagger-parameter in="body" name="essentials.electricityprovider" type="string" %}
Electricity Provider of the individual
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
 {
      "essentials": {
        "consumerNo": "....consumerNo...",
        "electricityProvider": ".....electricityProvider....."
      },
      "id": "....randomId.....",
      "patronId": "....patronid.....",
      "result": {
       "name": "...name...",
       "address": "...address...",
       "amountPayable": "...amountPayable...",
       "billAmount": "...billAmount...",
       "billDate": "...billDate...",
       "billDueDate": "...billDueDate...",
       "billIssueDate": "...billIssueDate...",
       "billNo": "...billNo...",
       "consumerNo": "...consumerNo...",
       "electricityProvider": "...electricityProvider...",
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
      "essentials": {
      "consumerNo": "...consumer Number...",
      "electricityProvider": ".....Electricity provider....."
      }
    }

```
{% endtab %}

{% tab title="Response Parameter" %}
| PARAMETER NAME             | DESCRIPTION                                                                                                                                                                                                                                                 |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                     | This holds the final response parameters.                                                                                                                                                                                                                   |
| result.name                | The name of the consumer is displayed here.                                                                                                                                                                                                                 |
| result.address             | The address registered with the consumer is displayed as output here.                                                                                                                                                                                       |
| result.amountPayable       | The net bill amount payable by the consumer is the output of this parameter.                                                                                                                                                                                |
| result.billAmount          | The bill amount for the consumer is shown here.                                                                                                                                                                                                             |
| result.billDate            | The bill date of for the consumer id being searched.                                                                                                                                                                                                        |
| result.billDueDate         | The due date of the bill for the consumer.                                                                                                                                                                                                                  |
| result.billIssueDate       | The date of issue for the bill to the customer.                                                                                                                                                                                                             |
| result.billNo              | The bill number for the consumer ID is displayed here.                                                                                                                                                                                                      |
| result.consumerNo          | The consumer number is displayed by this parameter.                                                                                                                                                                                                         |
| result.electricityProvider | The electricity provider information for the consumer ID being searched.                                                                                                                                                                                    |
| result.splitAddress        | This parameter displays the various parts of the address of the consumer number holder by splitting them into separate categories like district, state, city, pincode and country. For the country category, acceptable values is “IN”,”IND”and”INDIA”&#xD; |
| result.addressLine         | The first line of the address registered to the consumer number.                                                                                                                                                                                            |
{% endtab %}
{% endtabs %}

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/01e25f017cc7a5679abf)

| STATE            | ELECTRICITY BOARD NAME                                                      | ELECTRICITY PROVIDER CODE |
| ---------------- | --------------------------------------------------------------------------- | ------------------------- |
| ANDHRA PRADESH   | SOUTHERN POWER DISTRIBUTION COMPANY OF ANDHRA PRADESH LIMITED               | APSPDCL                   |
| ANDHRA PRADESH   | EASTERN POWER DISTRIBUTION COMPANY OF ANDHRA PRADESH LIMITED                | APEPDCL                   |
| CHANDIGARH       | CHANDIGARH ELECTRICITY DEPARTMENT                                           | CH\_ELEC                  |
| CHHATTISGARH     | CHHATTISGARH STATE POWER DISTRIBUTION COMPANY LIMITED                       | CSPDCL                    |
| DAMAN & DIU      | DAMAN AND DIU ELECTRICITY DEPARTMENT                                        | DAMAN\_DIU                |
| DELHI            | TATA POWER DELHI DISTRIBUTION                                               | TATA\_DL                  |
| DELHI            | BSES YAMUNA POWER LTD / BSES RAJDHANI POWER LTD                             | BSES\_DL                  |
| GOA              | GOA ELECTRICITY- FOR TISVADI, PONDA & VERNA                                 | GOA\_ELEC                 |
| GOA              | GOA ELECTRICITY- FOR OTHERS                                                 | UPAY\_GOA                 |
| GUJARAT          | UTTAR GUJARAT VIJ COMPANY LTD.                                              | UGVCL                     |
| GUJARAT          | PASHCHIM GUJARAT VIJ COMPANY LTD.                                           | PGVCL                     |
| GUJARAT          | MADHYA GUJARAT VIJ COMPANY LIMITED                                          | MGVCL                     |
| GUJARAT          | DAKSHIN GUJARAT VIJ COMPANY LIMITED                                         | DGVCL                     |
| HARYANA          | DAKSHIN HARYANA BIJLI VITRAN NIGAM                                          | DHBVN                     |
| HARYANA          | UTTAR HARYANA BIJLI VITRAN NIGAM                                            | UHBVN                     |
| HIMACHAL PRADESH | HIMACHAL PRADESH STATE ELECTRICITY BOARD LTD                                | HPSEB                     |
| KARNATAKA        | MANGALORE ELECTRICITY SUPPLY COMPANY LIMITED                                | MESCOM                    |
| KARNATAKA        | BANGALORE ELECTRICITY SUPPLY COMPANY LTD                                    | BESCOM                    |
| KARNATAKA        | CHAMUNDESHWARI ELECTRICITY SUPPLY COMPANY LIMITED MYSORE                    | CESCOM                    |
| KARNATAKA        | GULBARGA ELECTRICITY SUPPLY COMPANY LIMITED                                 | GESCOM                    |
| KARNATAKA        | HUBLI ELECTRICITY SUPPLY COMPANY LIMITED                                    | HESCOM                    |
| MADHYA PRADESH   | MADHYA PRADESH PASCHIM KSHETRA VIDYUT VITRAN COMPANY LIMITED                | MPWZ                      |
| MADHYA PRADESH   | MADHYA PRADESH MADHYA KSHETRA VIDYUT VITRAN COMPANY LIMITED                 | MPCZ                      |
| MADHYA PRADESH   | MADHYA PRADESH POORV KSHETRA VIDYUT VITRAN COMPANY LIMITED                  | MPEZ                      |
| MAHARASHTRA      | TATA-POWER - MUMBAI                                                         | TATA\_MUMBAI              |
| MAHARASHTRA      | BEST UNDERTAKING                                                            | BEST                      |
| MAHARASHTRA      | MAHAVITARAN-MAHARASHTRA STATE ELECTRICITY DISTRIBUTION CO. LTD (MSEDCL)     | MAHAVITRAN                |
| MAHARASHTRA      | RELIANCE ENERGY - MUMBAI                                                    | RELIANCE\_MH              |
| ORISSA           | SUPPLY COMPANY OF ORISSA LIMITED (NORTH, SOUTH & WEST)                      | ORISSA                    |
| PUNJAB           | PUNJAB STATE POWER CORPORATION LIMITED                                      | PSPCL                     |
| RAJASTHAN        | JAIPUR VIDHYUT VITRAN NIGAM LTD                                             | JAIPUR                    |
| RAJASTHAN        | AJMER VIDHYUT VITRAN NIGAM LTD                                              | AJMER                     |
| RAJASTHAN        | JODHPUR VIDHYUT VITRAN NIGAM LTD                                            | JODHPUR                   |
| UTTAR PRADESH    | KANPUR ELECTRICITY SUPPLY COMPANY                                           | KESCO                     |
| UTTAR PRADESH    | UP VIDYUT VITRAN NIGAM LIMITED (ALL ZONES)                                  | UPPCL                     |
| GUJARAT          | TORRENT POWER LIMITED - AHMEDABAD                                           | TORRENT\_AHD              |
| GUJARAT          | TORRENT POWER LIMITED - SURAT                                               | TORRENT\_SURAT            |
| GUJARAT          | TORRENT POWER LIMITED - AGRA                                                | TORRENT\_AGRA             |
| GUJARAT          | TORRENT POWER LIMITED - BHIWANDI                                            | TORRENT\_BHIWANDI         |
| GUJARAT          | TORRENT POWER LIMITED - DAHEJ                                               | TORRENT\_DAHEJ            |
| BIHAR            | NORTH BIHAR POWER DISTRIBUTION COMPANY LIMITED                              | NBPDCL                    |
| BIHAR            | SOUTH BIHAR POWER DISTRIBUTION COMPANY LIMITED                              | SBPDCL                    |
| TELANGANA        | THE SOUTHERN POWER DISTRIBUTION COMPANY OF TELANGANA LIMITED                | TSSPCL                    |
| ASSAM            | ASSAM POWER DISTRIBUTION COMPANY LIMITED                                    | APDCL                     |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - CHENNAI\_NORTH | CHENNAI\_NORTH            |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - VILLUPURAM     | VILLUPURAM                |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - COIMBATORE     | COIMBATORE                |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - ERODE          | ERODE                     |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - MADURAI        | MADURAI                   |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - TRICHY         | TRICHY                    |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - TIRUNELVEL     | TIRUNELVEL                |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - VELLORE        | VELLORE                   |
| TAMIL NADU       | TAMIL NADU GENERATION AND DISTRIBUTION CORPORATION LIMITED - CHENNAI\_SOUTH | CHENNAI\_SOUTH            |
