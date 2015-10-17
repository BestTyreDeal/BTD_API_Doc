# Errors


## HTTP Codes in response

Status (status) | Error Message |Meaning
---------- | ------- | -------
200 | - | All good (All valid responses - No error message required)
400 | 'Bad Request' | Malformed request or invalid syntax
401 | 'UnAuthorized Access' | Missing/Invalid parameters required for authorization
404 | 'Not Found' | Endpoint could not be found
405 | 'Request Method Not Allowed' | You tried to access with an invalid method
500 | 'Internal Server Error' | We had a problem with our server. Try again later.

```json
{
    "status": "401",
    "error": "UnAuthorized Access"
}
```

## BTD Codes in response

Content Code (ccode) | Error Message |Meaning
---------- | ------- | -------
404 | 'Content not found' | The requested content could not be found on BTD.

```json
{
    "status": 200,
    "content": {
        "ccode": "404",
        "ccmessage": "Content not found"
    }
}
```