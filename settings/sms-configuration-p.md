# SMS Configuration(p)

## **In SMS Configuration,** <a href="#_owo3fiiyrhms" id="_owo3fiiyrhms"></a>

An SMS API is an API for sending short messages over an SMS Gateway.

For eg: VCIP rescheduling messages, OTPs

Here, the API will be called to your webhook from there you can then proceed and send the SMS yourself.

> This feature adds SMS configuration capabilities to the Video KYC product.

The customers would want to be able to send reminders/updates/notifications to their end-users during various points in their onboarding journey. ( For eg, An end-user who drops out of a flow might need a timely reminder to complete their journey. These reminders will be in the form of emails or SMS )

> The purpose of this feature is to allow the admin to configure various aspects of sending such SMS notifications as per organizational requirements.

### **Under this,** <a href="#_mf8m46agbrwu" id="_mf8m46agbrwu"></a>

Custom URL - This is where you provide the Webhook's URL.

From - Contains the name of the person sending the SMS.

Job ID - It is a unique identifier if you want to give it to Signzy.

API Key - If you have an API key, you can add it here but it is optional



### **Click on Restore to default** <a href="#_t3646k5rbfe5" id="_t3646k5rbfe5"></a>

In order to clear all the tabs, you can restore the settings to default by clicking on this button.

## **How to successfully configure?** <a href="#_3myo977iy1fm" id="_3myo977iy1fm"></a>

In order to integrate with us, you must create a webhook as shown below.

```http
// POST request
{
"to": "<phonenumber>",
"from" : "...",
"body": "Hi...",
"jobId": "<jobId - optional>",
}
// Response expected
{
"status": "success/failure",
"message": "..."
}
```
