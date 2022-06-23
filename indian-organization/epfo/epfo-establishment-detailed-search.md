# EPFO Establishment Detailed Search



### Introduction

EPFO or **Employees Provident Fund Organisation** assists the Central Board in administering a _compulsory contributory Provident Fund Scheme_, _Pension Scheme_ and an _Insurance Scheme_ for the workforce engaged in the organized sector in India.

### API Usecase

Based on the Establishment ID that is generated during the EPFO Basic Search API request, the **EPFO Detailed Establishment Number Based Search** API delivers the **complete EPF details** of the organisation **along with the list of EPF account holders names** i.e the employees of the organisation for the given number of Months.

**The following information is generated about the Establishment**

* Establishment ID
* Establishment Name
* Validity Status
* Establishment Status
* Establishment Details
* PAN Status
* Primary Business Activity
* ESIC Code
* Primary Business Activity
* Date of the setup of establishment
* Detailed Address
* EPFO Office Name
* EPF Office address&#x20;



### How to call the API

You will need to login before sending a firm number request. You are required to pass the access token received from the login call, as an authorization header in the EPFO Basic Establishment Number/Name Based Search request along with establishmentId.



### API Input Guidelines

Provide correct **Establishment Name**, that's provided by the **Ministry of corporate affairs** (MCA)



### Sample CURL Request

Use the following exchange parameters for EPFO Detailed Establishment Number Based Search

{% tabs %}
{% tab title="Input Parameters" %}
| Authorization        | Required | String | Access Token               |
| -------------------- | -------- | ------ | -------------------------- |
| Content-Type         | Required | String | Application/JSON           |
| task                 | Required | String | Basic establishment search |
| essentials.vatNumber | Required | String | VAT number of the delear   |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 'https://signzy.tech/api/v2/patrons/6140962af6d4030eae0496e0/epfos' \
--header 'Authorization: <AUTH>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "detailedEstablishmentSearch",
    "essentials": {
        "establishmentId": "PUPUN1753022000",
        "employeeListMonths": "<Employee List Months>"
    }
}'

```
{% endtab %}
{% endtabs %}

**Response**

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                                  | DESCRIPTION                                                                                                                                                                                                                     |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                                          | The final response parameters are contained here.                                                                                                                                                                               |
| result.establishmentId                          | The establishment ID for which EPFO details are being searched.                                                                                                                                                                 |
| result.establishmentName                        | The name of the establishment.                                                                                                                                                                                                  |
| result.validityStatus                           | This parameter displays the details of the validity status like establishment status, portal registration status and post coverage status.                                                                                      |
| result.establishmentStatus                      | The details about the establishment coverage are displayed here like exemption, working, coverage section, actionable status and date of coverage.                                                                              |
| result.establishmentDetails                     | This parameter displays the details of the establishment registered under EPFO.                                                                                                                                                 |
| establishmentDetails.panstatus                  | The pan status of the establishment.                                                                                                                                                                                            |
| establishmentDetails.sectionApplicable          | The section of EPFo that is applicable to the establishment being searched.                                                                                                                                                     |
| establishmentDetails.primaryBusinessActivity    | The primary business activity of the establishment.                                                                                                                                                                             |
| establishmentDetails.esicCode                   | The ESIC code assigned to the establishment.                                                                                                                                                                                    |
| establishmentDetails.ownershipType              | The ownership type of the establishment is displayed by this parameter.                                                                                                                                                         |
| establishmentDetails.dateOfSetupOfEstablishment | The date of setup of the establishment as registered with EPFO.                                                                                                                                                                 |
| establishmentDetails.address                    | The address of the establishment registered under EPFO.                                                                                                                                                                         |
| establishmentDetails.pincode                    | The pincode of the establishment address.                                                                                                                                                                                       |
| establishmentDetails.city                       | The city of the establishment address.                                                                                                                                                                                          |
| establishmentDetails.district                   | The district of the establishment address.                                                                                                                                                                                      |
| establishmentDetails.state                      | The state of the establishment address.                                                                                                                                                                                         |
| establishmentDetails.country                    | The country of the establishment address.                                                                                                                                                                                       |
| establishmentDetails.epfoOfficeName             | The EPFO office name under which establishment is registered.                                                                                                                                                                   |
| establishmentDetails.epfoOfficeAddress          | The EPFO office address under which establishment is registered.                                                                                                                                                                |
| establishmentDetails.zone                       | The EPFO zone under which establishment is registered.                                                                                                                                                                          |
| establishmentDetails.region                     | The EPFO region under which establishment is registered.                                                                                                                                                                        |
| establishmentDetails.splitAddress               | This parameter distinguishes the various parts of the address of the ID holder into separate categories like district, state, city, pincode and country. For the country category, acceptable values are “IN”,”IND”and”INDIA”.  |
| pfPaymentDetails                                | This parameter contains the PF payment details of the establishment including date and time of credit, wage month, number of employees and employee name of the establishment.                                                  |
{% endtab %}

{% tab title="Response" %}
```
{
    "essentials": {
        "establishmentId": "PUPUN1753022000",
        "employeeListMonths": "1"
    },
    "id": "617be4b07157fd10dd4eb665",
    "patronId": "<Patron ID>",
    "task": "detailedEstablishmentSearch",
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
        "pfPaymentDetails": [
            {
                "transactionId": "3152110021852",
                "dateOfCredit": "14/10/2021",
                "timeOfCredit": "12:34:26",
                "amount": "14,95,124",
                "wageMonth": "09/2021",
                "noOfEmployees": "154",
                "employeeNames": [
                    "A DINESH KUMAR",
                    "A N CHANDRA MOHAN",
                    "AADESH P",
                    "ABHISHEK KANAUJIA",
                    "ABHISHEK KUMAR YADAV",
                    "ADITI AGARWAL",
                    "ADITYA SAHU",
                    "ADITYA SHARMA",
                    "ADITYA UPADHYAY",
                    "ADYA TRIPATHI",
                    "AJINKYA ARVIND DESHMUKH",
                    "AKASH DASMONDAL",
                    "AKHILESH KUMAR GOSWAMI",
                    "AKSHAT ANUJ",
                    "ALISHA SRIVASTAVA",
                    "AMAN HARISHKUMAR BHARANI",
                    "AMAN SRIVASTAVA",
                    "ANIRUDH BHASKARAN",
                    "ANKIT RATAN",
                    "ANKUR ARORA",
                    "ANKUR PANDEY",
                    "ANOOP SRIVASTAVA",
                    "ANSHU KUMARI",
                    "ANTONY M SEBASTIAN",
                    "ANUBHAV SHRIVASTAVA",
                    "ANVEET MEHTA",
                    "APURBA KUIRY",
                    "ARBAZ AHMED AFZAL ANSARI",
                    "ARGHYA BHATTACHARYA",
                    "ARPIT MALAIYA",
                    "ARPIT RATAN",
                    "ARSALAN AHMAD IMTIYAZ KHAN",
                    "ARSHITA BATRA",
                    "ARUN KUMAR S",
                    "ASHISH GUPTA",
                    "B. KARTHICK",
                    "BIJAYA KUMAR BARIK",
                    "CHIRAG SAINI",
                    "CHIRAG V",
                    "CHITRANGADA PATRA",
                    "CHITRANSH RAJESH",
                    "DEBANJAN BAKSHI",
                    "DEEPAK KUMAR BEHERA",
                    "DEEPAK KUMAR MODI",
                    "DEEPAK M",
                    "DIGVIJAY SANJEEV CHAVAN",
                    "ELIYAZ AHMED",
                    "GANDU VAMSHI KRISHNA",
                    "GIRISH D",
                    "GOWTHAMI M",
                    "HARIHARAN",
                    "HARSH TYAGI",
                    "HARSHAL NIRANJAN SARDA",
                    "HARSHEET KAKAR",
                    "HARSHIT LALIT KARIA",
                    "HIMANI PATHAK",
                    "HIMANSHU RAO",
                    "HINA RANGLANI",
                    "IPSIT CHAKRABORTY",
                    "JEET SHANKER SRIVASTAVA",
                    "JITENDRA SINGH SANKHLA",
                    "KANCHERLA YESHWANTH",
                    "KARAN ARYAN",
                    "KARAN THAKUR",
                    "KASUKURTI RAMAKRISHNA",
                    "KESHAV BANSAL",
                    "KESHAV RAGHU",
                    "KEVAL JAIN",
                    "KOMAL TUKARAM SALUNKHE",
                    "KOPAL AWASTHI",
                    "KUNAL ANAND AKLEKAR",
                    "KUSHAL S PATIL",
                    "MAHESH MOHAN",
                    "MAITREYI KULKARNI",
                    "MANAN SHETH",
                    "MANISH KUMAR",
                    "MANISHA GANAPATI SHETTIGAR",
                    "MAYANK",
                    "MEERA NARAYANAN",
                    "MOHIT GUPTA",
                    "MOHIT GUPTA",
                    "MOUMITA GIRI",
                    "MUNIGELA VARUN",
                    "MURALI KANNAN",
                    "NADEEM MOHAMMAD SALIM NAKKASHI",
                    "NAMAN RAJPUT",
                    "NAVANEETHAN RAJASEKARAN",
                    "NILU DILIP SHINDE",
                    "NISHANT JAIN",
                    "OMKAR GIRISH FADNIS",
                    "PANDEY ABHISHEK RAMASHANKAR",
                    "PARAG NUWAL",
                    "PARDEEP SINGH",
                    "PARITOSH VATSAL TRIPATHI",
                    "PARTH DINESH RAMANI",
                    "PRABHAT SHARMA",
                    "PRANEET MEHTA",
                    "PRASANNA PRASHANT MANGOLI",
                    "PRATEEK GERA",
                    "PRATISH KALIDAS WAGHMARE",
                    "PRAVIN SHRIDHAR POPHALE",
                    "PRIYABRATA PRADHAN",
                    "PURUSHOTTAM KADAM",
                    "RACHNA SINHA",
                    "RAGHUPATURNI KOMAL",
                    "RAJAT VASHISHT",
                    "RAJDEEP SHARMA",
                    "RAKESH M R",
                    "RAVI HEMAN MEHTA",
                    "ROHIT NAGESH PATIL",
                    "RONAK KANTILAL BHANUSHALI",
                    "RUTIKA MAHAGAOKAR",
                    "S VARSHITHA BHAVNI",
                    "SACHIN SHIVPRAKASH VISHWAKARMA",
                    "SANAD DANIYAL",
                    "SANCHIT AGNIHOTRI",
                    "SANDHIYA B",
                    "SAQLAIN AHMED",
                    "SARVANI ADIL ALI KHAN",
                    "SAURABH SHANKAR VASNIK",
                    "SEENA SHEKHAWAT",
                    "SERJIL ALAM",
                    "SHEEBA NADAR",
                    "SHEETAL JAIN",
                    "SHIVAM MITTAL",
                    "SHREYAS HARESH JANI",
                    "SHRISTY",
                    "SHRUTHI SURENDRAN",
                    "SIDDHANT SEHGAL",
                    "SMARAN SOMAIAH N",
                    "SONIE RAI",
                    "SOURAV PAI K",
                    "SRIKANTH PARTHASARATHY",
                    "SUCHETA PATRO",
                    "SUNIL VYAS",
                    "SURESH",
                    "SUSHMITHA",
                    "SWETANK BHARDWAJ",
                    "SWETAPADMA DASH",
                    "TANGELLAPALLI SHALINI",
                    "TANGUDU MANITEJA",
                    "TAPABRATA BHADURI",
                    "TONMOY JYOTI BORAH",
                    "TUSHAR SHARMA",
                    "UDIT PRAKASH JESWANI",
                    "UDIT SINGH",
                    "UMA LAXMAN POTE",
                    "VEDANT BASSI",
                    "VIBHU RAMESH SHIVAGUNDE",
                    "VIDYA RAM SONAWANE",
                    "VIJAY SHANKAR THAKUR",
                    "VIKAS GOSWAMI",
                    "VINEET TIWARI",
                    "YUVRAJ SHARMA"
                ]
            }
        ]
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







&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/8af05e5ad1489e7e7cba)
