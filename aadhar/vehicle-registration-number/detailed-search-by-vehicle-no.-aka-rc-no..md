# Detailed Search by Vehicle No. (Aka RC No.)

### Introduction

This service is used for retrieving the details of vehicle registration and owner details by simply entering the vehicle registration number.

### API Usecase

This API uses the Vehicle number of the user's vehicle and will provide the details of that particular vehicle. It helps in auto-generating the details for the vehicle without having to manually provide the information. This API provides detailed information about the vehicle searched for.

### How to call the API

You will need to log in before sending the request. You are required to pass the access token received from the login call, as the authorization header in the request.

### API Input Guidelines

* Vehicle Number

### <mark style="color:blue;">Sample CURL Request</mark>

{% tabs %}
{% tab title="Input Parameters" %}
| **PARAMETER  NAME** | **DESCRIPTION**                                        |
| ------------------- | ------------------------------------------------------ |
| task                | <p>The type of task performed - “Basic Search”<br></p> |
| essentials          | Contains the essential output data                     |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request POST 
'https://signzy.tech/api/v2/patrons/<PATRON ID>/vehicleregistrations' \
--header 'Authorization: <ACCESS TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "task": "detailedSearch",
    "essentials": {
                    "vehicleNumber": "<Vehicle Number>",
                    "blacklistCheck": "false",
                    "stolen": {
                    "vehicleNumber": "",
                    "vehicleType": ""
                }
            }
        }'

```
{% endtab %}
{% endtabs %}



### <mark style="color:green;">Sample API Response</mark>

{% tabs %}
{% tab title="Response Parameters" %}
| PARAMETER NAME                       | DESCRIPTION                                                                                                                                                                                                                                                            |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result                               | This holds the final result parameters of the response.                                                                                                                                                                                                                |
| result.chassis                       | The chassis number of the registered vehicle is displayed.                                                                                                                                                                                                             |
| result.class                         | The vehicle class information is shown here.                                                                                                                                                                                                                           |
| result.engineNo                      | The engine number of the registered vehicle is displayed in this parameter.                                                                                                                                                                                            |
| result.owner                         | The owner details of the vehicle being searched is displayed here.                                                                                                                                                                                                     |
| result.ownerFatherName               | The father name of the vehicle owner is displayed here.                                                                                                                                                                                                                |
| result.regAuthority                  | The registration authority of the vehicle registration is displayed in this parameter.                                                                                                                                                                                 |
| result.regDate                       | The registration date of the vehicle number being searched.                                                                                                                                                                                                            |
| result.regNo                         | The registration Number of the vehicle number being searched.                                                                                                                                                                                                          |
| result.type                          | The type of fuel that the vehicle uses is shown here.                                                                                                                                                                                                                  |
| result.presentAddress                | The present address of the vehicle owner is displayed here.                                                                                                                                                                                                            |
| result.vehicleColour                 | The colour of the vehicle.                                                                                                                                                                                                                                             |
| result.rcExpiryDate                  | The date of expiry for the vehicle registration.                                                                                                                                                                                                                       |
| result.rcTaxUpto                     | This parameter displays the vehicle tax information (if available).                                                                                                                                                                                                    |
| result.vehicleInsuranceCompanyName   | This parameter holds the name and details of the company which has carried out the insurance for the registered vehicle                                                                                                                                                |
| result.permanentAddress              | The permanent address to which the vehicle is registered.                                                                                                                                                                                                              |
| result.vehicleManufacturingMonthYear | The month and year of manufacturing for the particular vehicle.                                                                                                                                                                                                        |
| result.vehicleManufacturerName       | The name of the vehicle manufacturer is shown here.                                                                                                                                                                                                                    |
| result.vehicleInsuranceUpto          | The date upto which the vehicle registration is valid.                                                                                                                                                                                                                 |
| result.vehicleCubicCapacity          | The vehicle cubic capacity and dimension details are displayed here.                                                                                                                                                                                                   |
| result.grossVehicleWeight            | The gross vehicle weight of the vehicle that is being searched is shown here.                                                                                                                                                                                          |
| result.rcFinancer                    | The financer information for the registration is available here.                                                                                                                                                                                                       |
| result.vehicleCategory               | The category to which the vehicle belongs.                                                                                                                                                                                                                             |
| result.vehicleTaxUpto                | The date upto which the vehicle tax information is paid/valid.                                                                                                                                                                                                         |
| result.vehicleInsurancePolicyNumber  | The policy number of the vehicle insurance for the vehicle being searched.                                                                                                                                                                                             |
| result.vehicleCylindersNo            | The number of cylinders being used by the vehicle is displayed by this parameter.                                                                                                                                                                                      |
| result.vehicleSeatCapacity           | The seating capacity of the vehicle being searched.                                                                                                                                                                                                                    |
| result.splitPermanentAddress         | This parameter displays the various parts of the permanent address to which the vehicle is registered by splitting them into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA” |
| result.addressLine                   | The first line of the permanent address is shown here.                                                                                                                                                                                                                 |
| result.splitPresentAddress           | This parameter displays the various parts of the present address to which the vehicle is registered by splitting them into separate categories like district, state, city, pincode and country. For the country category, acceptable values  is “IN”,”IND”and”INDIA”   |
| result.addressLine                   | The first line of the present address is shown here.                                                                                                                                                                                                                   |

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/f2210d3b1df54187a811)
{% endtab %}

{% tab title="Sample Response" %}
```
{
    "essentials": {
        "vehicleNumber": "MH12BG7237",
        "blacklistCheck": "false",
        "stolen": {
            "vehicleNumber": "",
            "vehicleType": ""
        }
    },
    "id": "6181f29e7157fd10dd4eff14",
    "patronId": "6140962af6d4030eae0496e0",
    "task": "detailedSearch",
    "result": {
        "regNo": "MH12BG7237",
        "class": "Motor Car(LMV)",
        "chassis": "MA3EBE41S00291395",
        "engine": "G3BBN134938",
        "vehicleManufacturerName": "MARUTI SUZUKI INDIA LTD",
        "model": "MARUTI  ESTEEM",
        "vehicleColour": "S WHITE",
        "type": "PETROL",
        "normsType": "Not Available",
        "bodyType": "SALOON",
        "ownerCount": "2",
        "owner": "VISHAL PIPARAIYA",
        "ownerFatherName": "B.K. PIPARAIYA",
        "mobileNumber": "",
        "status": "ACTIVE",
        "statusAsOn": "03/11/2021",
        "regAuthority": "PUNE, MAHARASHTRA",
        "regDate": "20/06/2002",
        "vehicleManufacturingMonthYear": "06/2002",
        "rcExpiryDate": "20/06/2022",
        "vehicleTaxUpto": "31/12/2099",
        "vehicleInsuranceCompanyName": "THE NEW INDIA ASSURANCE CO. LTD.",
        "vehicleInsuranceUpto": "30/11/2017",
        "vehicleInsurancePolicyNumber": "15360031160200010461",
        "rcFinancer": "NA",
        "presentAddress": "NANDAN SPECTRA FLAT NO C-802 SR.NO.23 2AP 2BP 2EP RAMNAGAR BALEWADI PUNE,PUNE 411045",
        "splitPresentAddress": {
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
                "MURKUTENAGAR (N.V.)"
            ],
            "pincode": "411045",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "NANDAN SPECTRA FLAT NO C-802 SR.NO.23 2AP 2BP 2EP RAMNAGAR BALEWADI PUNE"
        },
        "permanentAddress": "NANDAN SPECTRA FLAT NO C-802 SR.NO.23 2AP 2BP 2EP RAMNAGAR BALEWADI PUNE,PUNE 411045",
        "splitPermanentAddress": {
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
                "MURKUTENAGAR (N.V.)"
            ],
            "pincode": "411045",
            "country": [
                "IN",
                "IND",
                "INDIA"
            ],
            "addressLine": "NANDAN SPECTRA FLAT NO C-802 SR.NO.23 2AP 2BP 2EP RAMNAGAR BALEWADI PUNE"
        },
        "vehicleCubicCapacity": "1300.0",
        "grossVehicleWeight": "0",
        "unladenWeight": "875",
        "vehicleCategory": "LMV",
        "rcStandardCap": "NA",
        "vehicleCylindersNo": "4",
        "vehicleSeatCapacity": "5",
        "vehicleSleeperCapacity": "NA",
        "vehicleStandingCapacity": "NA",
        "wheelbase": "NA",
        "vehicleNumber": "MH12BG7237",
        "puccNumber": "NA",
        "puccUpto": "NA",
        "blacklistStatus": "NA",
        "blacklistDetails": [],
        "challanDetails": [],
        "permitIssueDate": "NA",
        "permitNumber": "",
        "permitType": "",
        "permitValidFrom": "NA",
        "permitValidUpto": "NA",
        "nonUseStatus": "",
        "nonUseFrom": "NA",
        "nonUseTo": "NA",
        "nationalPermitNumber": "",
        "nationalPermitUpto": "NA",
        "nationalPermitIssuedBy": "",
        "isCommercial": false,
        "nocDetails": "NA"
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
