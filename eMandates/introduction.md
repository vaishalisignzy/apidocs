---
description: >-
  Signzy e-mandates enable you to set up and manage recurring payments for your
  customers.
---

# Introduction

## Overview

Recurring payments is used in multiple use cases from app subscriptions to loan repayments. It enables an auto-collection mechanism to enable friction-free onboarding of users. NACH, or the National Automated Clearing House, was a system introduced by the National Payments Corporation of India, for interbank, high volume, electronic transfers, which were periodic in nature. eNACH or Electronic NACH is a new payment collection service in India that allows firms to automate payment collections from customers. Developed by NPCI, the system allows authentication through debit card or internet banking to automate recurring periodic or repetitive payment collections. With eNach mandate registration, the payments can be seamlessly processed without 2nd-factor authentication or customer intervention. The customers just need to provide authorization with their preferred bank at the beginning of a billing cycle to set up the e-mandate, and all the subsequent payments are made debited from that account automatically after that.

## API Use-case

Used for creating and managing eMandates.

While the mandate authorization happens on NPCI screens, there can be an optional screen before that which lets you select your bank account and mode of authentication. This can be automated by passing the values directly in API as well, which forms two types of flows:

1. Default flow\
   In this type of flow, user gets a screen to input his bank details post which they get redirected to NPCI driven authentication page.
2. Custom flow\
   In this type of flow, bank details are given in API, so user directly goes to NPCI driven authentication page.&#x20;

## Frequently Asked Questions (FAQs)

1. What is ENACH? \
   NACH, or the National Automated Clearing House, was a system introduced by the National Payments Corporation of India, for interbank, high volume, electronic transfers, which were periodic in nature. eNACH or Electronic NACH is a new payment collection service in India that allows firms to automate payment collections from customers.
2. What is a mandate and how is it set up Mandate setup is the first step in setting up the Enach process?\
   You can create a mandate with a desired amount, frequency, start date and end date or even on-demand variable debits. One the create mandate API is called the end customer needs to authorize the mandate. This is handled by NPCI screens and can be done by either Debit card details and netbanking credentials. Another mode of authorization - Aadhar OTP was recently introduced and would be available soon as well
3. What banks are supported 43 banks are supported by NPCI as of today and some more banks are various stages of implementation?\
   This link gives an exhaustive list of supported banks - https://www.npci.org.in/PDF/nach/live-members-e-mandates/Live-Banks-in-API-E-Mandate.pdf
4. What happens if there is no money in the bank account on mandate debit date? Are there any charges involved for bounced transactions API would provide for whatever reason the debit failed. \
   Typically there are some charges involved if the Enach mandate debit is bounced (failed due to insufficient balance in customer account) and the charges are dependant on customer’s bank
5. Where is the money collected and when does the debit happen? \
   The money would be collected in a central collection account maintained by our Payments partner cashfree. Usually the debit happens towards the end of the day and you would be able to see the status of the payment on the next day&#x20;
6. How and when is the money collected settled to merchant’s account? \
   Total money collected for a client from all the active Emandates would be settled in the account client sets up while onboarding with Signzy. Settlement will happen on T+2 day
7. Can a client use their own NPCI Utility code to collect the money directly into their own account?\
   &#x20;Currently we use a central common utility code to collect money on your behalf. In case the client has an NPCI approval and already has a Utility code themselves we can create a custom version for them to enable direct transfers to their sponsor banks account. Reach out to Signzy team for further details on this
8.  What is needed from the client to start using this?\
    API Client needs to submit some KYC documents:

    * Certificate of Incorporation&#x20;
    * Business PAN Card&#x20;
    * Authorized signatory/director's PAN card&#x20;
    * Authorized signatory address proof (DL/voter ID/Passport)&#x20;
    * Cancelled cheque/Bank statement
    * &#x20;MOA & AOA&#x20;
    * NBFC License (If not available declaration letter of NBFC supporting them)

    Apart from this we would also need the Bank account details where the collected money should be transferred.
9. How are the ENach APIs charged? \
   There are two charges involved here. First charge is Emandate creation and second is charge associated with per debit. Assuming you have to collect 12 monthly EMIs using Enach you would be charged once for Enach authorization and then 12 times the per month per debit charge as and when the debit happens

## Try it yourself! &#x20;

[Click here](https://www.getpostman.com/collections/b18e4ef586b0d433abb9) to get the postman collection and import to start using the APIs.
