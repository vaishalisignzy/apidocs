# EPFO Employee Name Search



### Introduction

EPFO or **Employees Provident Fund Organisation** assists the Central Board in administering a _compulsory contributory Provident Fund Scheme_, _Pension Scheme_ and an _Insurance Scheme_ for the workforce engaged in the organized sector in India.

### API Usecase

This API takes the **Establishment ID** and **Employee name** that were retrieved in the _Establishment Number_ _Based Search API_ request along with the month for which the employee record is to be searched.&#x20;

Upon a successful match, it receives the employee record and displays the organisation details to which the employee is registered as well as the list of other employees currently employed at the organisation.

**The following information is generated:**

* Establishment ID
* Establishment Name
* Validity Status
* Establishment Status
* Establishment Details
* PAN Status
* Primary Business Activity
* ESIC Code
* Ownership Type
* Date of the setup of establishment
* Detailed Address
* EPFO Office Name
* EPF Office address&#x20;
* EPFO Zone
* EPFO Region
* Employee name search response



### How to call the API

You will need to login before sending a firm number request. You are required to pass the access token received from the login call, as authorization header in the EPFO Employee Name Based Search request along with **establishmentId**, **employeeName** and **employmentMonth.**



### API Input Guidelines

Provide correct **Establishment Name**, that's provided by the **Ministry of corporate affairs** (MCA)



### Sample CURL Request

Use the following exchange parameters for EPFO Employee Name Based Search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization              | Required | String | Access Token                     |
| -------------------------- | -------- | ------ | -------------------------------- |
| Content-Type               | Required | String | Application/JSON                 |
| task                       | Required | String | Employee name search             |
| essentials.establishmentID | Required | String | ID of th establishment           |
| essentials.employeeName    | Required | String | Employee name to be searched for |
| essentials.employeeMonth   | Required | String |                                  |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/epfos' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "employeeNameSearch",
    "essentials": {
        "establishmentId": "PUPUN1753022000",
        "employeeName": "ankit ratan",
        "employmentMonth": "09/2021"
    }
}'
```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters" %}
| **PARAMETER NAME**                                  | **DESCRIPTION**                                                                                                                                                                                                                     |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **result**                                          | **The final response parameters are contained here.**                                                                                                                                                                               |
| **result.establishmentId**                          | **The establishment ID for which EPFO details are being searched.**                                                                                                                                                                 |
| **result.establishmentName**                        | **The name of the establishment.**                                                                                                                                                                                                  |
| **result.validityStatus**                           | **This parameter displays the details of the validity status like establishment status, portal registration status and post coverage status.**                                                                                      |
| **result.establishmentStatus**                      | **The details about the establishment coverage are displayed here like exemption, working, coverage section, actionable status and date of coverage.**                                                                              |
| **result.establishmentDetails**                     | **This parameter displays the details of the establishment registered under EPFO.**                                                                                                                                                 |
| **establishmentDetails.panstatus**                  | **The pan status of the establishment.**                                                                                                                                                                                            |
| **establishmentDetails.sectionApplicable**          | **The section of EPFo that is applicable to the establishment being searched.**                                                                                                                                                     |
| **establishmentDetails.primaryBusinessActivity**    | **The primary business activity of the establishment.**                                                                                                                                                                             |
| **establishmentDetails.esicCode**                   | **The ESIC code assigned to the establishment.**                                                                                                                                                                                    |
| **establishmentDetails.ownershipType**              | **The ownership type of the establishment is displayed by this parameter.**                                                                                                                                                         |
| **establishmentDetails.dateOfSetupOfEstablishment** | **The date of setup of the establishment as registered with EPFO.**                                                                                                                                                                 |
| **establishmentDetails.address**                    | **The address of the establishment registered under EPFO.**                                                                                                                                                                         |
| **establishmentDetails.pincode**                    | **The pincode of the establishment address.**                                                                                                                                                                                       |
| **establishmentDetails.city**                       | **The city of the establishment address.**                                                                                                                                                                                          |
| **establishmentDetails.district**                   | **The district of the establishment address.**                                                                                                                                                                                      |
| **establishmentDetails.state**                      | **The state of the establishment address.**                                                                                                                                                                                         |
| **establishmentDetails.country**                    | **The country of the establishment address.**                                                                                                                                                                                       |
| **establishmentDetails.epfoOfficeName**             | **The EPFO office name under which establishment is registered.**                                                                                                                                                                   |
| **establishmentDetails.epfoOfficeAddress**          | **The EPFO office address under which establishment is registered.**                                                                                                                                                                |
| **establishmentDetails.zone**                       | **The EPFO zone under which establishment is registered.**                                                                                                                                                                          |
| **establishmentDetails.region**                     | **The EPFO region under which establishment is registered.**                                                                                                                                                                        |
| **establishmentDetails.splitAddress**               | **This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.**  |
| employeeNameSearchResponse                          | This parameter matches the employee name against EPFO records and returns a match along with the employee list in the organization, and provides result as Match or No match                                                        |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "establishmentId": "PUPUN1753022000",
        "employeeName": "ankit ratan",
        "employmentMonth": "09/2021"
    },
    "id": "617cfbeb7157fd10dd4ec173",
    "patronId": "<Patron ID>",
    "task": "employeeNameSearch",
    "result": {
        "establishmentId": "PUPUN1753022000",
        "establishmentName": "SIGNZY TECHNOLOGIES PRIVATE LIMITED",
        "validityStatus": {
            "establishmentStatus": "CODE NO ALLOTTED WAS AFTER ONLINE REGISTRATION STARTED",
            "registrationStatusOnEcrPortal": "PERMANENT LOGIN CREATED BY OWNER ON ECR PORTAL",
            "postCoverageStatus": ""
        },
        "establishmentStatus": {
            "exemptionStatus": "PF: UNEXEMPTED, PENSION: UNEXEMPTED, EDLI: UNEXEMPTED",
            "workingStatus": "LIVE ESTABLISHMENT",
            "coverageSection": "0001(3)(B",
            "actionableStatus": "ACTIONABLE ESTABLISHMENT",
            "dateOfCoverage": "01/05/2018"
        },
        "establishmentDetails": {
            "panStatus": "VERIFIED",
            "sectionApplicable": "OTHER ESTABLISHMENTS IN WHICH EMPLOYING 20 OR MORE PERSONS AND NOTIFIED BY THE CENTRAL GOVT",
            "primaryBusinessActivity": "ESTABLISHMENT ENGAGED IN MANUFACTURE, MARKETING SERVICING, USAGE OF COMPUTERS",
            "esicCode": "",
            "ownershipType": "15",
            "dateOfSetupOfEstablishment": "03/11/2015",
            "pincode": "411021",
            "city": "PUNE",
            "district": "PUNE",
            "state": "MAHARASHTRA",
            "country": "INDIA",
            "epfoOfficeName": "PUNE",
            "epfoOfficeAddress": "2-3RD FLR,PUNE CANT. BOARD BLDING, NEAR GOLIBAR MAIDAN, CAMP",
            "zone": "MAHARASHTRA AND CHHATTISGARH",
            "region": "MH - PUNE",
            "address": "18 B, KUBERA BAHAR BUNGLOWS, SOC 131 2 BANER PASHAN LINK ROAD",
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
                    "PUNE"
                ],
                "pincode": "411021",
                "country": [
                    "IN",
                    "IND",
                    "INDIA"
                ],
                "addressLine": "18 B, KUBERA BAHAR BUNGLOWS, SOC 131 2 BANER PASHAN LINK ROAD"
            }
        },
        "employeeNameSearchResponse": {
            "match": "MATCH",
            "upstreamName": "ANKIT RATAN",
            "employeeList": [
                "SOURAV PAI K",
                "PRABHAT SHARMA",
                "SARVANI ADIL ALI KHAN",
                "SWETAPADMA DASH",
                "RACHNA SINHA",
                "ELIYAZ AHMED",
                "A N CHANDRA MOHAN",
                "ARSALAN AHMAD IMTIYAZ KHAN",
                "MANISHA GANAPATI SHETTIGAR",
                "KOMAL TUKARAM SALUNKHE",
                "ANKUR ARORA",
                "PURUSHOTTAM KADAM",
                "ROHIT NAGESH PATIL",
                "SIDDHANT SEHGAL",
                "DEEPAK KUMAR BEHERA",
                "RAGHUPATURNI KOMAL",
                "PARAG NUWAL",
                "RAJAT VASHISHT",
                "SUNIL VYAS",
                "UDIT SINGH",
                "MAYANK",
                "ARGHYA BHATTACHARYA",
                "SURESH",
                "SHEETAL JAIN",
                "SHRISTY",
                "B. KARTHICK",
                "MUNIGELA VARUN",
                "TANGELLAPALLI SHALINI",
                "ADITYA SHARMA",
                "DEBANJAN BAKSHI",
                "GOWTHAMI M",
                "HIMANI PATHAK",
                "KARAN THAKUR",
                "UMA LAXMAN POTE",
                "SEENA SHEKHAWAT",
                "KASUKURTI RAMAKRISHNA",
                "MANAN SHETH",
                "MURALI KANNAN",
                "TAPABRATA BHADURI",
                "KOPAL AWASTHI",
                "ANOOP SRIVASTAVA",
                "ARPIT RATAN",
                "KUSHAL S PATIL",
                "ANKIT RATAN",
                "VIJAY SHANKAR THAKUR",
                "PARDEEP SINGH",
                "PRANEET MEHTA",
                "HINA RANGLANI",
                "MOHIT GUPTA",
                "SRIKANTH PARTHASARATHY",
                "AMAN HARISHKUMAR BHARANI",
                "CHIRAG V",
                "RAVI HEMAN MEHTA",
                "SHRUTHI SURENDRAN",
                "DEEPAK KUMAR MODI",
                "S VARSHITHA BHAVNI",
                "NILU DILIP SHINDE",
                "YUVRAJ SHARMA",
                "AADESH P",
                "HARSHIT LALIT KARIA",
                "SERJIL ALAM",
                "KUNAL ANAND AKLEKAR",
                "BIJAYA KUMAR BARIK",
                "GANDU VAMSHI KRISHNA",
                "PRATEEK GERA",
                "SAQLAIN AHMED",
                "AKHILESH KUMAR GOSWAMI",
                "PARTH DINESH RAMANI",
                "HARSHEET KAKAR",
                "VIKAS GOSWAMI",
                "KESHAV BANSAL",
                "TUSHAR SHARMA",
                "MOUMITA GIRI",
                "ANUBHAV SHRIVASTAVA",
                "GIRISH D",
                "SWETANK BHARDWAJ",
                "AMAN SRIVASTAVA",
                "HARSHAL NIRANJAN SARDA",
                "KARAN ARYAN",
                "ADYA TRIPATHI",
                "SANDHIYA B",
                "VINEET TIWARI",
                "OMKAR GIRISH FADNIS",
                "ALISHA SRIVASTAVA",
                "PANDEY ABHISHEK RAMASHANKAR",
                "ADITYA SAHU",
                "ANTONY M SEBASTIAN",
                "ARSHITA BATRA",
                "DEEPAK M",
                "TANGUDU MANITEJA",
                "CHIRAG SAINI",
                "ADITYA UPADHYAY",
                "CHITRANSH RAJESH",
                "RONAK KANTILAL BHANUSHALI",
                "AJINKYA ARVIND DESHMUKH",
                "MEERA NARAYANAN",
                "NADEEM MOHAMMAD SALIM NAKKASHI",
                "ANVEET MEHTA",
                "VIBHU RAMESH SHIVAGUNDE",
                "HIMANSHU RAO",
                "KEVAL JAIN",
                "MAITREYI KULKARNI",
                "AKSHAT ANUJ",
                "ANIRUDH BHASKARAN",
                "SMARAN SOMAIAH N",
                "VEDANT BASSI",
                "MAHESH MOHAN",
                "ADITI AGARWAL",
                "RAJDEEP SHARMA",
                "PRAVIN SHRIDHAR POPHALE",
                "SUCHETA PATRO",
                "RAKESH M R",
                "A DINESH KUMAR",
                "SHEEBA NADAR",
                "ASHISH GUPTA",
                "DIGVIJAY SANJEEV CHAVAN",
                "VIDYA RAM SONAWANE",
                "ARUN KUMAR S",
                "SHIVAM MITTAL",
                "ANSHU KUMARI",
                "KESHAV RAGHU",
                "AKASH DASMONDAL",
                "PRIYABRATA PRADHAN",
                "ARPIT MALAIYA",
                "SACHIN SHIVPRAKASH VISHWAKARMA",
                "ABHISHEK KUMAR YADAV",
                "TONMOY JYOTI BORAH",
                "JITENDRA SINGH SANKHLA",
                "SANAD DANIYAL",
                "UDIT PRAKASH JESWANI",
                "ANKUR PANDEY",
                "PRASANNA PRASHANT MANGOLI",
                "JEET SHANKER SRIVASTAVA",
                "PARITOSH VATSAL TRIPATHI",
                "IPSIT CHAKRABORTY",
                "SUSHMITHA",
                "NAVANEETHAN RAJASEKARAN",
                "ARBAZ AHMED AFZAL ANSARI",
                "MANISH KUMAR",
                "KANCHERLA YESHWANTH",
                "HARIHARAN",
                "CHITRANGADA PATRA",
                "HARSH TYAGI",
                "NISHANT JAIN",
                "NAMAN RAJPUT",
                "SAURABH SHANKAR VASNIK",
                "ABHISHEK KANAUJIA",
                "SHREYAS HARESH JANI",
                "SANCHIT AGNIHOTRI",
                "SONIE RAI",
                "RUTIKA MAHAGAOKAR",
                "APURBA KUIRY",
                "PRATISH KALIDAS WAGHMARE"
            ]
        }
    }
}
```
{% endtab %}
{% endtabs %}

### ****

### **HTTP Response Codes**

| Status Code | Description                            |
| ----------- | -------------------------------------- |
| **200**     | All response details are valid and ... |
| **404**     | not found                              |
| **400**     | bad request                            |
| **401**     | unauthorised                           |
| **422**     | processable entity                     |
|             |                                        |







&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/787e784264ae2687754d)
