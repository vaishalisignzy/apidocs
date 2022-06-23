# Vehicle RC Number API

## Overview

A vehicle registration certificate or a vehicle RC is an official document issued by the respective Regional Transport Office (RTO). It acts as a proof that a particular vehicle is registered with the Government of India. According to the Motor Vehicles Act, 1988, it is mandatory for all vehicle owners to have an RC number for each of their vehicles in order to drive it on Indian roads. At the time of registration, the respective RTO captures all the important information related to the vehicle, for example, engine number, chassis number, owner’s name, vehicle class, fuel type, etc. Currently, there are 28 crores vehicles registered with the Government of India.&#x20;

Our Vehicle RC API enables you to search for any vehicle RC number and get all the necessary information related to the particular vehicle. A few of the basic information, you can get to know are:

* Chassis Number&#x20;
* Engine Number&#x20;
* Vehicle Owner’s Name&#x20;
* Vehicle Manufacturer Name&#x20;
* Vehicle Model&#x20;
* Vehicle Color&#x20;
* Fuel Type&#x20;
* RC Status

Please go through the API response structure to see the complete list of information available for a particular vehicle RC number.

## Search a Vehicle RC Number

{% swagger method="post" path="/vehicle/vehicleDetailed" baseUrl="https://api.signzy.app/api/v3" summary="Search for a vehicle RC number to get all the necessary information related to that particular vehicle number" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Authorization key to access the API
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-type" required="true" %}
**application/json**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="vehicleNumber" required="true" %}
Vehicle RC Number 
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "result": 
    {
        "regNo":"...regNo...",
        "class":"...class...",
        "chassis":"...chassis...",
        "engine":"...engine...",
        "vehicleManufacturerName":"...vehicleManufacturerName...",
        "model":"...model...", 
        "vehicleColour":"...vehicleColour...",
        "type":"...type...",
        "normsType":"...normsType...",
        "bodyType":"...bodyType...",
        "ownerCount":"...ownerCount...", 
        "owner":"...owner...",
        "ownerFatherName":"...ownerFatherName...",
        "mobileNumber":"...mobileNumber...",
        "status":"...status...",
        "statusAsOn":"...statusAsOn...",
        "regAuthority":"...regAuthority...", 
        "regDate":"...regDate...",
        "vehicleManufacturingMonthYear":"...vehicleManufacturingMonthYear...",
        "rcExpiryDate":"...rcExpiryDate...",
        "vehicleTaxUpto":"...vehicleTaxUpto...",
        "vehicleInsuranceCompanyName":"...vehicleInsuranceCompanyName...",
        "vehicleInsuranceUpto":"...vehicleInsuranceUpto...", 
        "vehicleInsurancePolicyNumber":"...vehicleInsurancePolicyNumber...",
        "rcFinancer":"...rcFinancer...",
        "presentAddress":"...presentAddress...",
        "permanentAddress": "...permanentAddress...",
        "vehicleCubicCapacity": "...vehicleCubicCapacity...", 
        "grossVehicleWeight": "...grossVehicleWeight...",
        "unladenWeight": "...unladenWeight...", 
        "vehicleCategory": "...vehicleCategory...",
        "rcStandardCap": "...rcStandardCap...", 
        "vehicleCylindersNo": "...vehicleCylindersNo...", 
        "vehicleSeatCapacity": "...vehicleSeatCapacity...",
        "vehicleSleeperCapacity": "...vehicleSleeperCapacity...", 
        "vehicleStandingCapacity": "...vehicleStandingCapacity...", 
        "wheelbase": "...wheelbase...",
        "vehicleNumber": "...vehicleNumber...",
        "puccNumber": "...puccNumber...", 
        "puccUpto": "...puccUpto...",
        "blacklistStatus": "...blacklistStatus...", 
        "permitIssueDate": "...permitIssueDate...",
        "permitNumber": "...permitNumber...",
        "permitType": "...permitType...",
        "permitValidFrom": "...permitValidFrom...",
        "permitValidUpto": "...permitValidUpto...",
        "nonUseStatus": "...nonUseStatus...",
        "nonUseFrom": "...nonUseFrom...",
        "nonUseTo": "...nonUseTo...",
        "nationalPermitNumber": "...nationalPermitNumber...",
        "nationalPermitUpto": "...nationalPermitUpto...",
        "nationalPermitIssuedBy": "...nationalPermitIssuedBy...",
        "isCommercial": "...isCommercial(true/false)...",
        "nocDetails": "...nocDetails..."
    }    
}
```
{% endswagger-response %}
{% endswagger %}

### Sample CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| PARAMETER  NAME | DESCRIPTION                                      |
| --------------- | ------------------------------------------------ |
| vehicleNumber   | The Vehicle RC Number which needs to be searched |
{% endtab %}

{% tab title="Sample CURL" %}
```
curl --location --request POST 'https://api.signzy.app/api/v3/vehicle/vehicleDetailed' \
--header 'Authorization: … AuthKey… (Unique to Each Consumer)' \
--header 'Content-Type: application/json' \
--data-raw '{
    "vehicleNumber": "MH19BU5995"
}'
```
{% endtab %}
{% endtabs %}

