# API Error Codes

Whenever a user encounters an error in the API, certain system messages might be displayed with a unique identifier in number format, known as an error code. These codes denote the status or reason for the error.&#x20;

Our API returns standard HTTP success or error status codes. For errors, we also include extra information about what went wrong encoded in the response as JSON. The various HTTP status codes we might return are listed below.

| _CODE_  | _TITLE_                    | _DESCRIPTION_                                                                                                                                                                                        |
| ------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200		   | OK                         | The request was successful.                                                                                                                                                                          |
| 204	    | No Content                 | There was no new data to return                                                                                                                                                                      |
| 304     | Not Modified               | Successfully Logged Out                                                                                                                                                                              |
| 400     | Bad Request                | The request was invalid or could not be processed. This may happen due to invalid Parameters passed to the API.                                                                                      |
| 401     | Authorization Required     | Missing or incorrect authentication credentials.                                                                                                                                                     |
| 403     | Access Forbidden           | The request is understood, but it has been refused or access is not allowed. An accompanying error message will explain why. This code is used when requests are being denied due to request limits. |
| 404		   | Not Found                  | The URL requested is invalid or the resource requested is not available.                                                                                                                             |
| 422     | Entity cannot be processed | Missing Inputs or the JSON body of a request is badly-formed.                                                                                                                                        |
| 500     | Internal Server Error      | Something is broken. This is usually a temporary error, for example in a high load situation or if an endpoint is temporarily having issues. User needs to try again later..                         |
| 502		   | Internal Server Error      | Signzy is down, or being upgraded.                                                                                                                                                                   |
| 504		   | Gateway Timeout            | The Signzy servers are up, but the request couldn’t be serviced due to some failure within the internal stack. Please try again later.                                                               |

```
{
	"error": {
		"name": "Error",
		"status": 400,
		"message": "wrong element in type"
	}
}
```

****

**Help &** **support**

In case you have any queries, need clarification or have any suggestions/feedback for improving any services or making the docs better, please feel free to tell us.

You can connect with us here: support@signzy.com

