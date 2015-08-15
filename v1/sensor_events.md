## Sensor events operations  
Description of CRUD operations for sensor events 

### Submit new sensor event
Submit a new sensor event. Notice that this service requires authentication using only the access token. Read documentation on how to get the access token.

###### Parameters
| Name          | Type      | Description                                       |
| ------------- | --------- | ------------------------------------------------- |
| sensorId      | string    | the id of the sensor to associate the event with  |
| status        | enum      |  new status for the sensor (open or closed)       |
| batteryLevel  | int       | the battery level of the sensor (optional)        |

###### Endpoint
``` http
POST - /api/v1/json/sensors/events
```

###### Sample Request
```json
{
    "sensorId": "100",
    "status": "open",
    "batteryLevel": "99"
}
```  

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "sensorEvents": []
    }
}
``` 

### Get sensor events
Query for past sensor events 

###### Optional Parameters
| Name      | Type      | Description                               |
| --------- | --------  | ----------------------------------------  |
| limit     | int       |  How many events to return                |
| offset    | int       | How many events to skip                   |
| sensorId  | String    | The id of the sensor to filter events for |

###### Endpoint
``` http
GET - /api/v1/json/sensors/events
```

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "sensors": [
            {
                "oid": "5570daa3c8306a6aa138c6cc",
                "sensorId": "100",
                "name": "Garage window",
                "description": "Small window at garage",
                "location": "Garage",
                "sensorTypeId": "1",
                "sensorTypeName": "Door/Window Sensor with battery support",
                "isActive": true,
                "zones": [
                    {
                        "oid": "557757f1c83099a98121b864",
                        "name": "Perimeter",
                        "description": "All doors and windows of the perimeter",
                        "status": "ENABLED",
                        "dateRegistered": 1433884656991,
                        "dateRegisteredH": "2015-06-09T21:17:36.991Z"
                    }
                ],
                "dateRegistered": 1436121110016,
                "dateRegisteredH": "2015-07-05T18:31:50.016Z"
            },
            {
                "oid": "5570da42c8306a6aa138c6cb",
                "sensorId": "200",
                "name": "Garage door",
                "description": "Main garage door",
                "location": "Garage",
                "sensorTypeId": "2",
                "sensorTypeName": "Door/Window Sensor without battery support",
                "isActive": true,
                "zones": [
                    {
                        "oid": "557757f1c83099a98121b864",
                        "name": "Perimeter",
                        "description": "All doors and windows of the perimeter",
                        "status": "ENABLED",
                        "dateRegistered": 1433884656991,
                        "dateRegisteredH": "2015-06-09T21:17:36.991Z"
                    }
                ],
                "dateRegistered": 1436121152296,
                "dateRegisteredH": "2015-07-05T18:32:32.296Z"
            }
        ]
    }
}
```


### Get sensors latest status
Returns latest status for each available sensor.

###### Endpoint
``` http
GET - /api/v1/json/sensors/status
```

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "sensorEvents": [
            {
                "oid": "559977c980742709d2fe5975",
                "sensorId": "100",
                "sensorName": "Garage window",
                "sensorLocation": "Garage",
                "status": "OPEN",
                "batteryLevel": -1,
                "dateOfEvent": 1436121033677,
                "dateOfEventH": "2015-07-05T18:30:33.677Z"
            },
            {
                "oid": "55995f9780742709d2fe5973",
                "sensorId": "200",
                "sensorName": "Garage door",
                "sensorLocation": "Garage",
                "status": "OPEN",
                "batteryLevel": 85,
                "dateOfEvent": 1436114839031,
                "dateOfEventH": "2015-07-05T16:47:19.031Z"
            }
        ]
    }
}
```