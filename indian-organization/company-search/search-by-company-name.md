# Search by Company Name

### Introduction&#x20;

This API is used for retrieving a unique **Company Identification Number (**CIN) of any registered company. The company name needs to be entered as Input and the unique CIN number assigned to that company comes as output, which can be utilized for further use by the other ROC APIs.

### API Usecase

This API uses the company name and provides the Company ID or CIN as a result. It helps in auto-generating the CIN of the company.

### Sample CURL Request

{% tabs %}
{% tab title="Input Parameters" %}
| Parameter Name | Description                        |
| -------------- | ---------------------------------- |
| model          | Organisation                       |
| method         | Search by name                     |
| name           | Name of the company to be searched |
{% endtab %}

{% tab title="CURL Request" %}
```
curl --location --request GET 'https://roc-smart-search.signzy.tech/smartfills/?model=organization&method=searchByName&name=reliance industries' \
--header 'Connection: keep-alive' \
--header 'Accept: application/json, text/plain, */*'
```
{% endtab %}
{% endtabs %}



{% hint style="info" %}
In this sample code name entered is "`reliance industries`"  so in output, we will get all those companies to name starting from **reliance industries** like

`RELIANCE INDUSTRIES LIMITED`

`RELIANCE INDUSTRIES INVESTMENT AND HOLDING LIMITED`

`RELIANCE INDUSTRIES HOLDING PRIVATE LIMITED`
{% endhint %}

### Response

{% tabs %}
{% tab title="Output Parameters" %}
| Parameter Name | Description                      |
| -------------- | -------------------------------- |
| Company name   | Name of the company searched for |
| Company ID     | CIN of the company               |
{% endtab %}

{% tab title="Response" %}
```
[
    [
        {
            "companyName": "RELIANCE INDUSTRIES LIMITED",
            "companyID": "L17110MH1973PLC019786"
        },
        {
            "companyName": "RELIANCE INDUSTRIES INVESTMENT AND HOLDING LIMITED",
            "companyID": "U67190MH2007PLC168008"
        },
        {
            "companyName": "RELIANCE INDUSTRIES HOLDING PRIVATE LIMITED",
            "companyID": "U51103MH2007PTC168016"
        }
    ]
]
```
{% endtab %}
{% endtabs %}

### Sample Response code

| Status Code | Description                    |
| ----------- | ------------------------------ |
| **200**     | All response details are valid |
| **404**     | Not found                      |
| **400**     | Bad request                    |
| **401**     | Unauthorised                   |
| **422**     | Processable entity             |
