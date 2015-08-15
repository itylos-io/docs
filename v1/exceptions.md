## Exceptions  
Description of all exceptions thrown from the Rest API.

When a request has been successfully completed the response looks like the following:
``` json
{
    "meta": {
        "code": 200
    },
    "response": {

    }
}
```

Though when a error occurs the response looks like this:
``` json
{
  "meta": {
        "code": 4005,
        "errorMessage": "Sensor with id [200] already exists"
  }
}
```
The possible exceptions thrown from the rest API are the following:

| Code    | Description                                                                                 |    
| ------- | ------------------------------------------------------------------------------------------- |
| 4001    | Tried to delete token associated to another user.                                           |
| 4002    | Missing required parameter. Consult documentation for the request payload or parameters     |
| 4003    | Tried to update another user's data                                                         |
| 4004    | Tried to create user with an email that is already associated to another user.              |
| 4005    | Provided sensor ID is already associated to another sensor.                                 |
| 4006    | Provided sensor ID is not a valid sensor ID. Probably sensor does not exist?                |
| 4007    | Provided zone OID is not valid. Probably zone with provided OID does not exist?             |
| 4008    | Provided object ID is not a valid object ID.                                                |
| 4009    | Provided sensor type ID does not exist. Consult service for available sensor types.         |
| 4010    | Cannot arm system when no zone has been enabled. At least one zone must be enabled.         |
| 4011    | Entered false password to disarm system.                                                    |