# Create Contract

The Create Contract API by Signzy, as the name suggests, is used by the user to create a new contract request. Using this API, the customer can create the necessary pdf and send to the concerned person/organisation who needs to sign the contract.

For creating a new contract, customer can pass either contract url(pdf url) or contract base64 and the list of signers.For each signer customer has to pass signer email address, signerName, their signing order (who will sign first,second and so on).

```
  // Data exchange
    For Test Credentials
    // POST ::https://contracting-preproduction.signzy.tech/api/customers/..customerId../contractdetails
    For Production Credentials
    // POST ::https://contracting.signzy.tech/api/customers/..customerId../contractdetails
    // Input post body

     input contract in pdf format

     {
     "pdfurl": "..pdfurl..",
     "multiPages": "true/false",
     "pageNo": [],
     "signerdetail": [{
         "signerName": "..signerName..",
         "signerEmail": "..signerEmail..",
         "signerUid": "..signerUid..",
         "signOrder": "..signOrder..",
         "signerPincode": "..signerPincode..",
         "signerGender": "..signerGender..",
         "signerDateOfBirth": "..signerDateOfBirth..",
         "signerUidLastFourDigits": "..signerUidLastFourDigits..",
         "biometricSign": "..biometricSign..",
         "signatureOptions" :[...signatureOptions...],
         "additionalVerification" : [..additionalVerification...],
         "showId" : "..showId...",
         "idImage" : "...idImage...",
         "signerMobile" : "...signerMobile...",
         "signerOtpMobile" : "...signerOtpMobile..."
     }, {
         "signerName": "..signerName..",
         "signerEmail": "..signerEmail..",
         "signerUid": "..signerUid..",
         "signOrder": "..signOrder..",
         "signerPincode": "..signerPincode..",
         "signerGender": "..signerGender..",
         "signerDateOfBirth": "..signerDateOfBirth..",
         "signerUidLastFourDigits": "..signerUidLastFourDigits..",
         "biometricSign": "..biometricSign..",
         "signatureOptions" :[...signatureOptions...],
         "additionalVerification" : [..additionalVerification...],
         "showId" : "..showId...",
         "idImage" : "...idImage...",
         "signerMobile" : "...signerMobile...",
         "signerOtpMobile" : "...signerOtpMobile..."
     }],
     "customerMailList": ["..customerMailList.."],
     "fileFormat": "..fileFormat..",
     "logoUrl" : "...logoUrl...",
     "contractName" : "...contractName...",
     "tnc" : "...tnc...",
     "contractExecuterName": "...contractExecuterName...",
     "initiationEmailSubject": "...initiationEmailSubject...",
     "userReminderTime": "..userReminderTime..",
     "adminReminderTime": "..adminReminderTime..",
     "maximumValidityTime": "..maximumValidityTime..",
     "callbackUrl": "..callbackUrl..",
     "callbackUrlAuthPresent": "true/false",
     "callbackUrlAuthType": "....callbackUrlAuthType...",
     "callbackUrlAuthCredentials": {
         "username": "...username...",
         "password": "...password..."
     },
     "customerCallbackExtraParameters" : ["...customerCallbackExtraParameters..."],
     "signerCallbackUrl": "..signer callbackUrl..",
     "signerCallbackUrlAuthPresent": "true/false",
     "signerCallbackUrlAuthType": "....signer callbackUrlAuthType...",
     "signerCallbackUrlAuthCredentials": {
         "username": "...username...",
         "password": "...password..."
     }
    },
    "iacceptSubject" : "..iacceptSubject..",
    "iacceptMessage" : "..iacceptMessage..",
    "iacceptCCEmailIds" : [..iacceptCCEmailIds..],
    "iacceptNegativeTexts" : [..iacceptNegativeTexts..]

    input contract in pdfbase64 format

    {
    "pdfbase64": "..pdfbase64..",
    "multiPages": "true/false",
    "pageNo": [],
    "signerdetail": [{
        "signerName": "..signerName..",
        "signerEmail": "..signerEmail..",
        "signerUid": "..signerUid..",
        "signOrder": "..signOrder..",
        "signerPincode": "..signerPincode..",
        "signerGender": "..signerGender..",
        "signerDateOfBirth": "..signerDateOfBirth..",
        "signerUidLastFourDigits": "..signerUidLastFourDigits..",
        "biometricSign": "..biometricSign..",
        "signatureOptions" :[...signatureOptions...],
        "additionalVerification" : [..additionalVerification...],
        "showId" : "..showId...",
        "idImage" : "...idImage...",
        "signerMobile" : "...signerMobile...",
        "signerOtpMobile" : "...signerOtpMobile..."
    }, {
        "signerName": "..signerName..",
        "signerEmail": "..signerEmail..",
        "signerUid": "..signerUid..",
        "signOrder": "..signOrder..",
        "signerPincode": "..signerPincode..",
        "signerGender": "..signerGender..",
        "signerDateOfBirth": "..signerDateOfBirth..",
        "signerUidLastFourDigits": "..signerUidLastFourDigits..",
        "biometricSign": "..biometricSign..",
        "signatureOptions" :[...signatureOptions...],
        "additionalVerification" : [..additionalVerification...],
        "showId" : "..showId...",
        "idImage" : "...idImage...",
        "signerMobile" : "...signerMobile...",
        "signerOtpMobile" : "...signerOtpMobile..."
    }],
    "logoUrl" : "...logoUrl...",
    "contractName" : "...contractName...",
    "tnc" : "...tnc...",
     "contractExecuterName": "...contractExecuterName...",
     "initiationEmailSubject": "...initiationEmailSubject...",
    "customerMailList": ["..customerMailList.."],
    "fileFormat": "..fileFormat..",
    "userReminderTime": "..userReminderTime..",
    "adminReminderTime": "..adminReminderTime..",
    "maximumValidityTime": "..maximumValidityTime..",
    "callbackUrl": "..callbackUrl..",
    "callbackUrlAuthPresent": "true/false",
    "callbackUrlAuthType": "....callbackUrlAuthType...",
    "callbackUrlAuthCredentials": {
        "username": "...username...",
        "password": "Tarita123"
    },
    "customerCallbackExtraParameters" : ["...customerCallbackExtraParameters..."],
    "signerCallbackUrl": "..signer callbackUrl..",
    "signerCallbackUrlAuthPresent": "true/false",
    "signerCallbackUrlAuthType": "....signer callbackUrlAuthType...",
    "signerCallbackUrlAuthCredentials": {
        "username": "...username...",
        "password": "...password..."
    }
    },
   "iacceptSubject" : "..iacceptSubject..",
   "iacceptMessage" : "..iacceptMessage..",
   "iacceptCCEmailIds" : [..iacceptCCEmailIds..],
   "iacceptNegativeTexts" : [..iacceptNegativeTexts..]
    // Expected response

    Expected response of pdf format input
    {
    "pdfurl": "..pdfurl..",
    "signerdetail": [
        {
            "signerName": "..signerName..",
            "signerEmail": "..signerEmail..",
            "signerUid": "..signerUid..",
            "signOrder": "..signOrder..",
            "signerPincode": "..signerPincode..",
            "signerGender": "..signerGender..",
            "signerDateOfBirth": "..signerDateOfBirth..",
            "signerUidLastFourDigits": "..signerUidLastFourDigits..",
            "biometricSign": "..biometricSign..",
            "signatureOptions" :[...signatureOptions...],
            "additionalVerification" : [..additionalVerification...],
            "showId" : "..showId...",
            "idImage" : "...idImage...",
            "signerMobile" : "...signerMobile...",
            "signerOtpMobile" : "...signerOtpMobile..."
        },
        {
            "signerName": "..signerName..",
            "signerEmail": "..signerEmail..",
            "signerUid": "..signerUid..",
            "signOrder": "..signOrder..",
            "signerPincode": "..signerPincode..",
            "signerGender": "..signerGender..",
            "signerDateOfBirth": "..signerDateOfBirth..",
            "signerUidLastFourDigits": "..signerUidLastFourDigits..",
            "biometricSign": "..biometricSign..",
            "signatureOptions" :[...signatureOptions...],
            "additionalVerification" : [..additionalVerification...],
            "showId" : "..showId...",
            "idImage" : "...idImage...",
            "signerMobile" : "...signerMobile...",
            "signerOtpMobile" : "...signerOtpMobile..."
        }
    ],
    "customerMailList": [
        "..customerMailList..",
        "..customerMailList.."
    ],
    "id": "..The Unique Contract Id created for each request which will be used for pulling the data of each contract..",
    "customerId": "..customerId..",
    "callbackUrl": "..callbackUrl..",
    "fileFormat": "directURL",
    "iacceptSubject" : "..iacceptSubject..",
    "iacceptMessage" : "..iacceptMessage..",
    "iacceptCCEmailIds" : [..iacceptCCEmailIds..],
    "iacceptNegativeTexts" : [..iacceptNegativeTexts..]
   }

    Expected response of pdfbase64 format input

    {
        "signerdetail": [
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signOrder": "...signOrder...",
                "signerUid" : "..signerUid..",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "signerPincode" : "..signerPincode..",
                "signerGender" : "..signerGender..",
                "signerDateOfBirth" : "..signerDateOfBirth..",
                "signerUidLastFourDigits" : "..signerUidLastFourDigits..",
                "biometricSign" : "..biometricSign..",
                "signatureOptions" :[...signatureOptions...],
                "additionalVerification" : [..additionalVerification...],
                "showId" : "..showId...",
                "idImage" : "...idImage...",
                "signerMobile" : "...signerMobile...",
                "signerOtpMobile" : "...signerOtpMobile..."
            },
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signOrder": "...signOrder...",
                "signerUid" : "..signerUid..",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "signerPincode" : "..signerPincode..",
                "signerGender" : "..signerGender..",
                "signerDateOfBirth" : "..signerDateOfBirth..",
                "signerUidLastFourDigits" : "..signerUidLastFourDigits..",
                "biometricSign" : "..biometricSign..",
                "signatureOptions" :[...signatureOptions...],
                "additionalVerification" : [..additionalVerification...],
                "showId" : "..showId...",
                "idImage" : "...idImage...",
                "signerMobile" : "...signerMobile...",
                "signerOtpMobile" : "...signerOtpMobile..."
            },
            {
                "signerName": "..signerName..",
                "signerEmail": "..signerEmail..",
                "signerUid" : "..signerUid..",
                "signOrder": "...signOrder...",
                "signerId": "..signerId..",
                "signaturePosition": "..signaturePosition..",
                "signerPincode" : "..signerPincode..",
                "signerGender" : "..signerGender..",
                "signerDateOfBirth" : "..signerDateOfBirth..",
                "signerUidLastFourDigits" : "..signerUidLastFourDigits..",
                "biometricSign" : "..biometricSign..",
                "signatureOptions" :[...signatureOptions...],
                "additionalVerification" : [..additionalVerification...],
                "showId" : "..showId...",
                "idImage" : "...idImage...",
                "signerMobile" : "...signerMobile...",
                "signerOtpMobile" : "...signerOtpMobile..."
            }
        ],
        "customerMailList": [
            "..customerMailList..",
            "..customerMailList.."
        ],
        "id": "..contractId..",
        "customerId": "..customerId..",
        "pdfbase64": "..pdfbase64..",
        "callbackUrl": "..callbackUrl..",
        "fileFormat": "base64",
        "iacceptSubject" : "..iacceptSubject..",
        "iacceptMessage" : "..iacceptMessage..",
        "iacceptCCEmailIds" : [..iacceptCCEmailIds..],
        "iacceptNegativeTexts" : [..iacceptNegativeTexts..]
    }

```



#### Input Parameters

| PARAMETERS                         | DESCRIPTION                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | POSSIBLE VALUES                 |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| pdfbase64/pdfurl                   | Pdf file converted into base64 format/Pdf file uploaded to a file format directURL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Compulsory                      |
| contractName                       | Name of the contract.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Optional                        |
| tnc                                | Terms and Conditions of the contract while signing through iaccept and iacceptwithemail method. If field is empty or not passed then signzy default text will come.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Optional                        |
| contractExecuterName               | Name of the entity who has initiated/created/started the contract signing process.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Optional                        |
| initiationEmailSubject             | Subject of the Email send to the signer for starting the contract signing process.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Optional                        |
| MultiPages                         | <p>Attribute value defines whether you have to sign on all pages of the PDF or some specific page."true" means sign on all pages of PDF and "false" means sign on the specific page.</p><p><strong>Default Value :</strong> true</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Optional (true/false in string) |
| pageNo                             | Attribute value defines if multiPages is "false" and you want sign on a specific page then send the pageNo in array.If pageNo is not specified and multiPages is "false" then it will sign on last page of the PDF.If Multipages value is "true" but if you are passing pageNo value then also it will sign on all the pages of PDF file.                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Optional (array)                |
| logoUrl                            | Url of the logo of the customer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional                        |
| signerdetail                       | Details about the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Compulsory                      |
| signerName                         | Name of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Compulsory                      |
| signerEmail                        | Email-ID of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Compulsory                      |
| signerMobile                       | Mobile number of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Optional (String)               |
| signerUid                          | Unique ID Number of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional                        |
| signerPincode                      | Pincode of the address of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Optional                        |
| signerGender                       | Gender of the signer (Male/Female/Transgender).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional                        |
| signerDateOfBirth                  | Date of the signer (ie DD/MM/YYYY).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Optional                        |
| signerUidLastFourDigits            | Last 4 digits of the Aadhaar Number of the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Optional                        |
| signOrder                          | Order in which signer has to sign in the contract.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Optional (Integer)              |
| biometricSign                      | Biometric evidence at time of signature is required or not(true/false).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Optional (String)               |
| idImage                            | This field is taken for each signer which is the image of the idcard of the particular signer which has to matched with the face in the video.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Optional (String)               |
| showId                             | <p>This field is taken for each signer which denotes whether the particular idCard uploaded by the initiator has to been shown to the signer.</p><p><strong>Default Value:</strong> "true"</p><p><strong>Possible Values :</strong> "true/false"</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Optional (String)               |
| signatureOptions                   | <p>All the options of signature given by the initiator using one of which the the signer can choose to sign the contract.</p><ol><li>aadhaaresign</li><li>esign</li><li>iaccept</li><li>iacceptwithemail</li></ol><p><strong>Default Value :</strong> ['aadhaaresign']</p><p><strong>Possible Values :</strong> ["aadhaaresign", "esign", "iaccept","iacceptwithemail"]</p>                                                                                                                                                                                                                                                                                                                                                                                                               | Optional (Array)                |
| additionalVerification             | <p>All the additional type of verification available.</p><ol><li>idvideo</li><li>video</li><li>mobileotp</li><li>emailotp</li></ol><p><strong>Default Value :</strong> [] No additional verification</p><p><strong>Possible Values :</strong> [ "idvideo", "mobileotp", "emailotp"],</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Optional (Array)                |
| signerOtpMobile                    | This field is taken for each signer where initiator gives the mobile number of signer where otp has to be sent in the case where initiator has chosen mobileotp in additionalVerification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Optional (String)               |
| customerMailList                   | List of the admin mail ids of customers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Optional                        |
| fileFormat                         | Format of the PDF passed in the contract whether it is in base64 format or directURL uploaded to file system.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Compulsory(base64,directURL)    |
| userReminderTime                   | <p>The Time Interval after which the user will be sent a reminder email for signing the contract.</p><p><strong>Default Time :</strong> 24 hrs</p><p><strong>Minimum Time :</strong> 24 hrs</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional (in hours)             |
| adminReminderTime                  | <p>The Time Interval after which the user will be sent a reminder email with admin email address in <strong>cc</strong> for signing the contract.This is admin emailIds is the same emailIds which is passed in the customerMailList field.</p><p><strong>Default Time :</strong> 120 hrs</p><p><strong>Minimum Time :</strong> 24 hrs</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                | Optional (in hours)             |
| maximumValidityTime                | <p>The maximum time after which the contract gets expired.</p><p><strong>Default Time :</strong> 720 hrs</p><p><strong>Minimum Time :</strong> 24 hrs</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Optional (in hours)             |
| Callback URL                       | Callback url for posting data if it is required to post the post data to some other url for the particular request.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Compulsory                      |
| Callback Auth Present              | <p>Whether a authentication is required to post to callbackUrl.</p><p><strong>Default Value :</strong> false</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Optional (true/false in string) |
| Callback Auth Type                 | <p>If authentication is required to post to callbackUrl,then what is authentication type.</p><p><strong>Default Value :</strong> basic-auth</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional                        |
| Callback Auth Credentials          | If authentication is required to post to callbackUrl and authentication type is basic-auth,then this takes the auth username and auth password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Optional                        |
| Customer Callback Extra Parameters | <p>All the additional parameters that you want to push to callbackUrl apart from standard parameters.</p><ol><li>initialContract</li><li>initialPdfHash</li><li>contractName</li><li>contractExecuterName</li><li>contractPageCount</li><li>finalSignedContractHash</li><li>finalDscSignedContract</li><li>finalDscSignedContractHash</li><li>auditCertificate</li><li>auditCertificateHash</li><li>signerdetail</li></ol><p><strong>Default Value :</strong> [] No additional parameters</p><p><strong>Possible Values :</strong> ["initialContract", "initialPdfHash", "contractName", "contractExecuterName", "contractPageCount", "finalSignedContractHash", "finalDscSignedContract", "finalDscSignedContractHash", "auditCertificate", "auditCertificateHash", "signerdetail"],</p> | Optional (Array)                |
| Signer Callback URL                | Signer Callback url for posting data once Aadhaar ESign Process for the particular transaction is completed by the signer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Optional                        |
| Signer Callback Auth Present       | <p>Whether a authentication is required to post to Signer Callback url .</p><p><strong>Default Value :</strong> false</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Optional (true/false in string) |
| Signer Callback Auth Type          | <p>If authentication is required to post to Signer callbackUrl,then what is authentication type.</p><p><strong>Default Value :</strong> basic-auth</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Optional                        |
| Signer Callback Auth Credentials   | If authentication is required to post to Signer callbackUrl and authentication type is basic-auth,then this takes the auth username and auth password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Optional                        |
| iacceptSubject                     | The Subject the signer needs to send in the consent email                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Optional                        |
| iacceptMessage                     | The Message body the signer needs to send in the consent email                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Optional                        |
| iacceptCCEmailIds                  | The Email IDs the signer needs to add in cc while sending the consent email                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Optional                        |
| iacceptNegativeTexts               | The Negative words that the contract initiator wants to check if it is there in the consent email,then the consent email is rejected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Optional                        |

#### Output Parameters

| PARAMETERS       | DESCRIPTION                                                                                                         |
| ---------------- | ------------------------------------------------------------------------------------------------------------------- |
| signerdetail     | Details about the signer.                                                                                           |
| signerName       | Name of the signer.                                                                                                 |
| signerEmail      | Email-ID of the signer.                                                                                             |
| signOrder        | Order in which signer has to sign in the contract.                                                                  |
| customerMailList | List of the admin mail ids of customers.                                                                            |
| id               | The Unique **ContractId** created for each request which will be used for pulling the data of each contract.        |
| customerId       | The Unique **CustomerId** for each customer.                                                                        |
| callbackUrl      | Callback url for posting data if it is required to post the post data to some other url for the particular request. |
| fileFormat       | Format of the PDF passed in the contract whether it is in base64 format or directURL uploaded to file system.       |

#### Posting data to signer callback system

For every signer involved in the contracting signing procedure, data for the success or failure scenarios of the signing procedure is posted back to the signer callback system.Please find undermentioned the data to be posted in the signer callback URL.

Success scenario :

```

  {
	"contractId": "..contractId...",
	"customerId": "..customerId..",
	"signerEmail": "..signerEmail..",
	"signerName": "..signerName..",
	"signerId": "..signerId..",
	"status": "..status..",
	"aadhaarErrorCode": "..aadhaarErrorCode..",
	"aadhaarErrorMessage": "..aadhaarErrorMessage..",
	"aadhaarStatus": "..aadhaarStatus..",
	"signerSignedContract": "..signerSignedContract..",
    "signerEventTimestamp" : ...signerEventTimestamp..,
	"signerMatchData": {
		"nameMatch": "No Match/PARTIAL Match/DIRECT MATCH",
		"pincodeMatch": "No Match/Match",
		"genderMatch": "No Match/Match",
		"dobMatch": "No Match/Match",
		"uidLastFourDigitsMatch": "No Match/Match"
	}
}
```

Failure scenario :

```

  {
	"contractId": "..contractId..",
	"customerId": "..customerId..",
	"signerEmail": "..signerEmail..",
	"signerName": "..signerName..",
	"signerId": "..signerId..",
	"status": "..status..",
	"aadhaarErrorCode": "..aadhaarErrorCode..",
	"aadhaarErrorMessage": "..aadhaarErrorMessage..",
	"aadhaarStatus": "..aadhaarStatus..",
	"signerSignedContract": "..signerSignedContract..",
    "signerEventTimestamp" : ...signerEventTimestamp..,
	"signerMatchData": {}
}
```

#### Output Parameters

| PARAMETERS             | DESCRIPTION                                                                                                                                                                                                                                                         |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId             | The Unique **CustomerId** for each customer.                                                                                                                                                                                                                        |
| contractId             | The Unique **ContractId** generated for each contract.                                                                                                                                                                                                              |
| signerName             | Name of the signer.                                                                                                                                                                                                                                                 |
| signerEmail            | Email-ID of the signer.                                                                                                                                                                                                                                             |
| signerEventTimestamp   | EPOCH Timestamp of the time at which Aadhaar ESign Process for the particular transaction is completed by the signer (Integer).                                                                                                                                     |
| status                 | Signzy status says whether user has successfully signed contract or not.(Possible Values:200 for success/500 for failure).                                                                                                                                          |
| aadhaarErrorCode       | Received Error code of Aadhaar ESign Process for the particular transaction from upstream(UIDAI).                                                                                                                                                                   |
| aadhaarErrorMessage    | Received Error Message of Aadhaar ESign Process for the particular transaction from upstream(UIDAI).                                                                                                                                                                |
| aadhaarStatus          | Received Status of Aadhaar ESign Process for the particular transaction from upstream(UIDAI).                                                                                                                                                                       |
| signerSignedContract   | Esigned Contract signed by the signer(Possible Values:pdf url/base64 data in case of successful signing or empty string in case Esign Process fails).                                                                                                               |
| signerMatchData Block  | These block returns the match results of the data given in the signer block and data returned by Aadhaar in the Digital Signature Certificate(Possible Values:All individual match data in case of successful signing or empty object in case Esign Process fails). |
| nameMatch              | Name Match Result matches the name given in the signer block with name returned by Aadhaar in Digital Signature Certificate (Possible values Direct Match/Partial Match/No Match).                                                                                  |
| pincodeMatch           | Pincode Match Result matches the pincode given in the signer block with pincode returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                                                                              |
| genderMatch            | Gender Match Result matches the gender given in the signer block with gender returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                                                                                 |
| dobMatch               | Date of Birth Match Result matches the year of date of birth given in the signer block with year of birth returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                                                    |
| uidLastFourDigitsMatch | uidLastFourDigitsMatch matches the gender last signerUidLastFourDigits given in the signer block with the last 4 digits of the aadhaar Number returned by Aadhaar in Digital Signature Certificate (Possible values Match/No Match).                                |

#### Posting Data to customer callback after completion of Signing procedure

Once the contract signing procedure is completed i.e; when all the signers mentioned in the signerdetail block have signed the contract callback data is posted to the callback URL.Please find undermentioned the data to be posted in the customer callback URL.

```

{
    "customerId":"..customerId...",
    "contractId":"...contractId..",
    "finalSignedContract": "...finalSignedContract...",
    "contractCompletionTime": ...time at which the contract is completed(time is in EPOCH format)...,
    "initialSignerCount": ..initialSignerCount..,
    "signerCount": ..signerCount..,
    "deletedSignerCount": ..deletedSignerCount..,
    "initialContract": "...initialContract...",
	"initialPdfHash": "...initialPdfHash...",
	"contractName": "...contractName...",
	"contractExecuterName": "...contractExecuterName...",
	"contractPageCount": "...contractPageCount...",
	"finalSignedContractHash": "...finalSignedContractHash...",
	"finalDscSignedContract": "...finalDscSignedContract...",
	"finalDscSignedContractHash": "...finalDscSignedContractHash...",
	"auditCertificate": "...auditCertificate...",
	"auditCertificateHash": "...auditCertificateHash...",
	"signerdetail": ["...signerdetail..."]
}
```

#### Output Parameters

**Mandatory Parameters**

| PARAMETERS             | DESCRIPTION                                                                                                                                                             |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId             | The Unique **CustomerId** for each customer (String).                                                                                                                   |
| contractId             | The Unique **ContractId** generated for each contract (String).                                                                                                         |
| finalSignedContract    | Final Signed Contract signed by all the designated signers.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String). |
| contractCompletionTime | EPOCH Timestamp of the time at which Final Signed Contract was signed by all the designated signers (Integer).                                                          |
| initialSignerCount     | Initial Number of Signers when the contract was created(Integer).                                                                                                       |
| signerCount            | Actual Number of signers who signed the contract(Integer).                                                                                                              |
| deletedSignerCount     | Number of signers who were deleted once the contract was created(Integer).                                                                                              |

**Optional Parameters**

This values are passed based on values passed in array in customerCallbackExtraParameters in create contract request

| PARAMETERS                 | DESCRIPTION                                                                                                                                                                                                                                                                 |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| initialContract            | Initial Contract file used for initiating the contracting process.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String).                                                                                              |
| initialPdfHash             | Hash of the initial Contract file used for initiating the contracting process (String).                                                                                                                                                                                     |
| contractName               | Name of the contract (String).                                                                                                                                                                                                                                              |
| contractExecuterName       | Name of the executer of the contract(String).                                                                                                                                                                                                                               |
| contractPageCount          | Number of pages in the contract file(String).                                                                                                                                                                                                                               |
| finalSignedContractHash    | Hash of the final Signed Contract signed by all the designated signers.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String).                                                                                         |
| finalDscSignedContract     | Signzy DSC signed Contract once the contract is signed by all the designated signers.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String).                                                                           |
| finalDscSignedContractHash | Hash of the Signzy DSC signed Contract once the contract is signed by all the designated signers.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String).                                                               |
| auditCertificate           | Audit Certificate is a certificate generated and digitally signed by signzy which contains contract details,signer Details and auditTrail of the Contract.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String).      |
| auditCertificateHash       | Hash Audit Certificate is a certificate generated and digitally signed by signzy which contains contract details,signer Details and auditTrail of the Contract.File Format is either DIRECTURL or BASE64 based on fileFormat specified in Create Contract request (String). |

&#x20;[![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/f9b7ad7eb0ccc6572377)
