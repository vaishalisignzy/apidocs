# Search Company's Assets Under Charge by CIN

### Introduction

In simple terms, Charge is a **right created by** a company i.e. "Borrower" in favour of a financial institution or a bank or any other lender, i.e. "creditor" who has agreed to extend financial assistance to the company on its assets or properties or any of its undertakings present and future. So this API helps to retrieve any charge created against any company's asset.



### API Usecase

This API is used to retrieve basic details about the company and any Charge which is created on the assets of the company just by entering the company's CIN as input. It helps in auto-generating the information of charges on assets, which is useful for various stakeholders of the company.&#x20;

**The following information is generated about the company:**

* Company name
* ROC office
* Registration number
* Category
* Sub category&#x20;
* Class
* Authorised capital
* PaidUp capital
* Number of members
* Date of Incorporation
* Registered address
* Email-Id
* Whether listed
* Last AGM date
* Balance sheet date
* Status for E-filing
* Address other than Registered office
* Suspended at Stock exchange
* CIN
* Number of directors
* Charges registered

**The following information is generated about Charge against Assets of the company:**&#x20;

* Asset under charge
* Charge amount
* Date of creation
* Date of modification
* Charged ID
* Charge holder name
* Date of satisfaction
* Address
* Status



### How to call the API

Before going for ROC Asset charges for organizations, you first need to create an '_Organization'_ **object** and you need to pass the _CIN_ as an **identifier** in the request body.



### API Input Guidelines

Provide correct CIN, it is **a unique 21 digit alpha-numeric number** provided to every registered company by the **ROC (Registrar of Companies).**

{% hint style="info" %}
You can get CIN from our API [Search by Company Name](search-by-company-name.md)&#x20;
{% endhint %}

###

### Sample CURL Request

### **Step 1**: Creating Organisation Object

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                            |
| -------------- | ----------------- | --------- | -------------------------------------- |
| Authorization  | Required          | Object    | Access Token                           |
| Content-Type   | Required          | String    | Application/JSON                       |
| identifier     | Required          | String    | Contains the unique identifier ID      |
| service        | Required          | String    | Type of service - ROC                  |
| callbackUrl    | Required          | String    | URL where the response will be posted  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/organizations' \
--header 'Authorization: exjbyOxoHTxq9YpagNDXeAMmQ2n0a8pjY41EZKi02H6BumuuCMQimfutTPIMFgzO' \
--header 'Content-Type: application/json' \
--data-raw '{
    "identifier": "U74900MH2011PTC216800",
    "service": "roc",
    "callbackUrl": "https://www.w3schools.com"
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters " %}
| **Parameter Name** | Description                                         |
| ------------------ | --------------------------------------------------- |
| callbackUrl        | URL where response will be posted                   |
| accessToken        | Access token from the organization creation request |
| id                 |                                                     |
| patronId           | Unique user id                                      |
| identifier         | Contains the unique identifier ID                   |
| service            | Type of service - ROC                               |
{% endtab %}

{% tab title="Response" %}
```
{
    "callbackUrl": "https://www.w3schools.com",
    "accessToken": "4ax19juwo4cr8c7ns9h359c1604mcf34u",
    "id": "61655bb3bd40d75f83620d4e",
    "patronId": "6140962af6d4030eae0496e0",
    "identifier": "U74900MH2011PTC216800",
    "service": "roc"
}
```
{% endtab %}
{% endtabs %}

### ****

### **Step 2**: Hunt for Organisation

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Required/Optional | Data Type | Description                                         |
| -------------- | ----------------- | --------- | --------------------------------------------------- |
| Content-Type   | Required          | String    | Application/JSON                                    |
| target         | Required          | String    | Organization                                        |
| itemId         | Required          | String    | ID of the Organization object created               |
| accessToken    | Required          | String    | Access token from the organization creation request |
| task           | Required          | String    | Task to be performed - Company search by CIN        |
| essentials     | Required          | Object    | Contains essential input data                       |
| cin            | Required          | String    | Company's CIN to search                             |


{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/hunts' \
--header 'Accept: application/json, text/plain, */*' \
--header 'Content-Type: application/json' \
--data-raw '{
    "target": "Organization",
    "itemId": "616558e3bd40d75f83620cb5",
    "accessToken": "7arbnktbduttffcvbq68knyjgvt9w4m",
    "task": "assetChargesByCin",
    "essentials": {
        "cin": "L74999PN2018PLC174192"
    }
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name                          | Description                                                                                                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result.numberofMembers                  | Number of members in the company                                                                                                                                                                                                |
| result.subCategory                      | Whether the company is a Government or Non-Govt company                                                                                                                                                                         |
| result.class                            | The class to which the company belongs.                                                                                                                                                                                         |
| result.companyType                      | The type of company - Public or Private limited.                                                                                                                                                                                |
| result.companyName                      | Registered name of the company                                                                                                                                                                                                  |
| result.paidUpCapital                    | Amount of money a company receives in exchange for a share of the company                                                                                                                                                       |
| result.authorisedCapital                | The maximum amount of share capital that the company is authorized                                                                                                                                                              |
| result.whetherListed                    | Whether listed on Exchange ( NSE, BSE) or not                                                                                                                                                                                   |
| result.dateofIncorporation              | Date on which company got incorporated                                                                                                                                                                                          |
| result.registrationNumber               | Registration number of the company got from ROC                                                                                                                                                                                 |
| result.registeredAddress                | The Registered address of the company                                                                                                                                                                                           |
| result.category                         | Which type of limited company it is whether Limited by shares or Limited by Guarantee                                                                                                                                           |
| result.cin                              | CIN (Corporate Identification Number) of the company                                                                                                                                                                            |
| result.rocOffice                        | Registrar to which company comes under                                                                                                                                                                                          |
| result.noOfDirectors                    | Number of directors the company has                                                                                                                                                                                             |
| result.addressOtherThanRegisteredOffice | Any other registered address of the company                                                                                                                                                                                     |
| result.emailId                          | Registered email Id of the company with the ROC                                                                                                                                                                                 |
| result.splitAddress                     | This parameter distinguishes the various parts of the address of the company into separate categories like district, state, city, Pincode and country. For the country category, acceptable values are “IN”, ”IND” and ”INDIA”. |
| result.natureOfBusiness                 | The nature of the business conducted by the company. For ex: Supplier of Services.                                                                                                                                              |
| result.activeCompliance                 |                                                                                                                                                                                                                                 |
| result.status                           | Whether a company is in operation or not                                                                                                                                                                                        |
| result.statusForEfiling                 | Whether company is filing its return on regular basis or not with ROC. If yes than Active else Inactive                                                                                                                         |
| chargesRegistered                       | This parameter displays the details of the charges registered against the assets.                                                                                                                                               |
| chargesRegistered.assetsUnderCharge     | The asset name under charge is shown by this parameter.                                                                                                                                                                         |
| chargesRegistered.chargeAmount          | The amount charged against the asset is shown here.                                                                                                                                                                             |
| chargesRegistered.dateOfCreation        | The date of creation of the asset charge.                                                                                                                                                                                       |
| chargesRegistered.dateOfModification    | The date of modification, if any, on the asset charge.                                                                                                                                                                          |
| chargesRegistered.Status                | The status of the asset under charge.                                                                                                                                                                                           |


{% endtab %}

{% tab title=" Response" %}
```
{
    "target": "Organization",
    "itemId": "616558e3bd40d75f83620cb5",
    "accessToken": "7arbnktbduttffcvbq68knyjgvt9w4m",
    "task": "assetChargesByCin",
    "id": "61655bf1bd40d75f83620d5f",
    "essentials": {
        "cin": "L74999PN2018PLC174192"
    },
    "result": {
        "numberOfMembers": "0",
        "subCategory": "NON-GOVT COMPANY",
        "class": "PUBLIC",
        "companyType": "INDIAN COMPANY",
        "companyName": "KPIT TECHNOLOGIES LIMITED",
        "paidUpCapital": "2741438080",
        "authorisedCapital": "4500000000",
        "whetherListed": "LISTED",
        "dateOfIncorporation": "08/01/2018",
        "balanceSheetDate": "31/03/2021",
        "registrationNumber": "174192",
        "registeredAddress": "PLOT NO.17,RAJIV GANDHI INFOTECH PARK,MIDC-SEZ, PHASE-III,MAAN,TALUKA - MULSHI, HINJAWADI,PUNE. PUNE PUNE MH 411057 IN",
        "category": "COMPANY LIMITED BY SHARES",
        "cin": "L74999PN2018PLC174192",
        "rocOffice": "ROC-PUNE",
        "noOfDirectors": "10",
        "addressOtherThanRegisteredOffice": "",
        "lastAgmDate": "25/08/2021",
        "suspendedAtStockExchange": "",
        "emailId": "Nida.Deshpande@kpit.com",
        "activeCompliance": "",
        "status": "ACTIVE",
        "statusForEfiling": "ACTIVE",
        "chargesRegistered": [
            {
                "assetsUnderCharge": "",
                "chargeAmount": "960000000.0",
                "dateOfCreation": "14/03/2021",
                "dateOfModification": "-",
                "chargeId": "100433343",
                "chargeHolderName": "THE HONGKONG AND SHANGHAI BANKING CORPORATION LIMITED",
                "dateOfSatisfaction": "-",
                "address": "PLOT NO D2,5TH FLOOR,AMAR AVINASH CORPORATE PLAZA,BUND GARDEN,PUNEMH411001IN",
                "status": ""
            },
            {
                "assetsUnderCharge": "",
                "chargeAmount": "9043880.0",
                "dateOfCreation": "01/01/2020",
                "dateOfModification": "-",
                "chargeId": "100323023",
                "chargeHolderName": "HDFC BANK LIMITED",
                "dateOfSatisfaction": "-",
                "address": "SENAPATI BAPAT ROAD,LOWER PANEL (WEST)MUMBAIMH400013IN",
                "status": ""
            },
            {
                "assetsUnderCharge": "",
                "chargeAmount": "750000000.0",
                "dateOfCreation": "27/06/2019",
                "dateOfModification": "-",
                "chargeId": "100276115",
                "chargeHolderName": "AXIS BANK LIMITED",
                "dateOfSatisfaction": "-",
                "address": "214-215,SECOND FLOOR,\"CITI MALL\",UNIVERSITY(GANESH KHIND) ROADPUNEMH411007IN",
                "status": ""
            },
            {
                "assetsUnderCharge": "",
                "chargeAmount": "250000000.0",
                "dateOfCreation": "22/04/2019",
                "dateOfModification": "-",
                "chargeId": "100261866",
                "chargeHolderName": "CITI BANK N.A.",
                "dateOfSatisfaction": "-",
                "address": "GROUND FLOOR, ONYX TOWER, 37/3 GHORPADINR. WESTT N HOTEL, NORTH KOREGAON PARK, MAIN RD,PUNEMH411001IN",
                "status": ""
            },
            {
                "assetsUnderCharge": "",
                "chargeAmount": "750000000.0",
                "dateOfCreation": "16/04/2019",
                "dateOfModification": "-",
                "chargeId": "100259463",
                "chargeHolderName": "HDFC BANK LIMITED",
                "dateOfSatisfaction": "-",
                "address": "HDFC BANK HOUSESENAPATI BAPAT MARGLOWER PAREL WMUMBAIMH400013IN",
                "status": ""
            },
            {
                "assetsUnderCharge": "",
                "chargeAmount": "500000000.0",
                "dateOfCreation": "07/03/2019",
                "dateOfModification": "-",
                "chargeId": "100247580",
                "chargeHolderName": "KOTAK MAHINDRA BANK LIMITED",
                "dateOfSatisfaction": "-",
                "address": "27BKC, C 27, G BLOCKBANDRA KURLA COMPLEX, BANDRA (E),MUMBAIMA400051IN",
                "status": ""
            }
        ],
        "splitAddress": {
            "district": [
                "PUNE"
            ],
            "state": [
                [
                    "MAHARASHTRA",
                    "MH"
                ]
            ],
            "city": [
                "MARUNJI"
            ],
            "pincode": "411057",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "PLOT NO.17,RAJIV GANDHI INFOTECH PARK,MIDC-SEZ,PHASE-III,MAAN,TALUKA MULSHI,HINJAWADI"
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



&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/run-collection/2ee7c3a566d899966273)
