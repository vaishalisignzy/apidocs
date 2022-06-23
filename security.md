# Security

### Data transaction&#xD;

We accept only secure HTTPS calls for all APIs, which adhere to strong cipher suite defined using SHA-256 with RSA Encryption. This algorithm first calculates a unique hash of the input data using SHA-256 algorithm. The hash is then encrypted with a private key using the RSA algorithm. This is useful in scenarios where we only need to verify that the data is authentic as well as secure.

All transaction data are encrypted at the source and encryption is maintained throughout, so that there is no unauthorized access.

The URLs expire in 30 seconds by default, unless explicitly specified in the inbound request in the ttl parameter.

### Access Tokens & API keys&#xD;

An important aspect to remember while using the API key/password is that anybody with your API key/password or an Access Token generated using them can access all the information you have created and also send requests on your behalf. Therefore, it is highly recommended that the API-key/Password is not provided to client side. Instead, we can make use of a reverse proxy to call Signzy APIs.

You can disable any active access\_token by logging out. Let us know if your Signzy Password/API-key is compromised as soon as possible, so that we can disable & create new ones and prevent any misuse of your data.

### Getting help&#xD;

If you have any queries regarding security of your data and network calls, feel to connect with us at support@signzy.com



