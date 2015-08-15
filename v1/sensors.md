## Sensors operations  
Description of CRUD operations for sensor data 

### Get sensor types
Returns all sensor types supported by Itylos.io. Each sensor must be associated with a sensor type.

###### Endpoint
``` http
GET - /api/v1/json/sensors/types
```

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "types": [
            {
                "id": "1",
                "name": "Door/Window sensor with battery support",
                "description": "Door or window sensor that sends battery status level",
                "isBatteryPowered": true
            },
            {
                "id": "2",
                "name": "Door/Window sensor without battery support",
                "description": "Door or window sensor that does not provide info about the battery level",
                "isBatteryPowered": false
            },
            {
                "id": "3",
                "name": "Movement sensor with battery support",
                "description": "Movement sensor that sends battery status level",
                "isBatteryPowered": true
            },
            {
                "id": "4",
                "name": "Movement sensor without battery support",
                "description": "Movement sensor that does not provide info about the battery level",
                "isBatteryPowered": false
            },
            {
                "id": "5",
                "name": "Kerberos",
                "description": "Kerberos setup. (Configure webhooks in kerberos instance to point to your itylos setup)",
                "isBatteryPowered": false
            }
        ]
    }
}
```

### Get sensors
Query for all sensors. For each sensor the zones it belongs to are returned, if any.

###### Endpoint
``` http
GET - /api/v1/json/sensors
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
                "oid": "55cba2c7e4b06f9fe85278e7",
                "sensorId": "frontdoor",
                "name": "frontdoor",
                "description": "192.168.2.6",
                "location": "192.168.2.6",
                "sensorTypeId": "5",
                "sensorTypeName": "Kerberos",
                "isActive": true,
                "zones": [
                    {
                        "oid": "55cba34fe4b06f9fe85278e8",
                        "name": "All",
                        "description": "All sensors and cameras",
                        "status": "ENABLED",
                        "dateRegistered": 1439408975112,
                        "dateRegisteredH": "2015-08-12T19:49:35.112Z"
                    }
                ],
                "dateRegistered": 1439408839358,
                "dateRegisteredH": "2015-08-12T19:47:19.358Z"
            },
            {
                "oid": "55cba413e4b06f9fe85278ea",
                "sensorId": "1000",
                "name": "Living room",
                "description": "Living room PIR",
                "location": "Living room",
                "sensorTypeId": "4",
                "sensorTypeName": "Movement sensor without battery support",
                "isActive": true,
                "zones": [
                    {
                        "oid": "55cba34fe4b06f9fe85278e8",
                        "name": "All",
                        "description": "All sensors and cameras",
                        "status": "ENABLED",
                        "dateRegistered": 1439408975112,
                        "dateRegisteredH": "2015-08-12T19:49:35.112Z"
                    }
                ],
                "dateRegistered": 1439409171162,
                "dateRegisteredH": "2015-08-12T19:52:51.162Z"
            }
        ]
    }
}
```


### Create sensor
Create a new sensor. Notice that two sensors cannot have the same sensor Id.

###### Parameters
| Name          | Type          | Description                                                                   |
| ------------- | ------------- | ----------------------------------------------------------------------------- |
| sensorId      | string        | the id of the new sensor. This id will be used when submitting sensor events  |
| name          | string        | the name of the sensor                                                        |
| description   | string        | the description of the sensor                                                 |
| location      | string        | the location of the sensor                                                    |    
| sensorTypeId  | string        | the type of the sensor. See supported sensor types                            | 
| isActive      | boolean       | if true sensor will be taken into account when system is armed else not       |

###### Endpoint
``` http
POST - /api/v1/json/sensors
```

###### Sample Request
```json
{
    "sensorId": "300",
    "name": "Kitchen Window",
    "description": "Small window upper right corner",
    "location": "Kitchen second floor",
    "sensorTypeId": "1",
    "isActive": true
}
```  


### Update sensor
Update sensor's data. Notice that two sensors cannot have the same sensor Id.

###### Parameters
| Name          | Type      | Description                                           |
| ------------- | --------- | ----------------------------------------------------- |
| oid           | string    | the oid of the sensor to update                       |
| sensorId      | string    | the id of the new sensor. This id will be used when submitting sensor events |
| name          | string    | the name of the sensor                                |
| description   | string    | the description of the sensor                         |
| location      | string    | the location of the sensor                            |
| sensorTypeId  | string    | the type of the sensor. See supported sensor types    |
| isActive      | boolean   | if true sensor will be taken into account when system is armed else not |

###### Endpoint
``` http
PUT - /api/v1/json/sensors
```

###### Sample Request
```json
{
    "oid": "54eb0435be5077ad51f8dc4f",
    "sensorId": "300",
    "name": "Kitchen Window",
    "description": "Small window upper right corner",
    "location": "Kitchen second floor",
    "sensorTypeId": "1",
    "isActive": true
}
```  


### Delete sensor 
Deletes a sensor. Notice that sensor will be removed from the associated zones and it's history will be deleted forever.

###### Parameters
| Name          | Type          | Description                     |
| ------------- | ------------- | ------------------------------- |
| oid           | string        | the oid of the sensor to delete |


###### Endpoint
``` http
DELETE - /api/v1/json/sensors  
```
###### Sample Request
```json
{
  "oid": "54eb52b3be50bc0319fb8edd"
}
```  
