## Zones operations     
Description of CRUD operations for zone status and CRUD operations for zone data 

### Get zones status
Get status (enabled/disabled) for each zone

###### Endpoint
``` http
GET - /api/v1/json/zones/status
```
###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zonesStatus": [
            {
                "zoneId": "557757f1c83099a98121b864",
                "status": "ENABLED",
                "zoneName": "Perimeter",
                "dateUpdated": 1434458194332,
                "dateUpdatedH": "2015-06-16T12:36:34.332Z"
            }
        ]
    }
}
``` 

### Update zones status
Update the status for a zone to enabled/disabled. Remember that zone status cannot change when system is armed.

###### Parameters
| Name      | Type      | Description                                       |
| ----------| --------- | ------------------------------------------------- |
| zoneId    | string    | the id of the zone for which to update the status |
| status    | enum      | new status for the zone (enabled or disabled)     |

###### Endpoint
``` http
PUT - /api/v1/json/zones/status
```

###### Sample Request
```json
{
  "zoneId":"54eb6dfdbe50c9c1a039cfc5",
  "status": "ENABLED"
}
```  

###### Sample Response
    
```json
{
  "zoneId":"54eb6dfdbe50c9c1a039cfc5",
  "status": "ENABLED"
}
``` 


### Get zones
Get all zones with the sensors included in each zone.

###### Endpoint
``` http
GET - /api/v1/json/zones
```

###### Sample Response
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zones": [
            {
                "oid": "55cba34fe4b06f9fe85278e8",
                "name": "All",
                "description": "All sensors and cameras",
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
                        "dateRegistered": 1439409171162,
                        "dateRegisteredH": "2015-08-12T19:52:51.162Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439408975112,
                "dateRegisteredH": "2015-08-12T19:49:35.112Z"
            }
        ]
    }
}
```
    
### Creates new zone 
Creates a new zone with the specified sensors.

###### Parameters
| Name          | Type          | Description                                       |
| ------------- | ------------- | ------------------------------------------------- | 
| name          | string        | the name of the zone                              |
| description   | string        | a description for the zone                        |
| sensorOIds    | list<string>  | the OIds of the sensors to include in the zone    |

###### Endpoint
``` http
POST - /api/v1/json/zones
```

###### Sample Request
```json
{
    "name": "Kerberos Zone",
    "description": "Only Kerberos Cameras",
    "sensorOIds": [
        "5505d954be5065d8a5e18143"
    ]
}
```  
 
######  Sample Response
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zones": [
            {
                "oid": "55cba34fe4b06f9fe85278e8",
                "name": "All",
                "description": "All sensors and cameras",
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
                        "dateRegistered": 1439409171162,
                        "dateRegisteredH": "2015-08-12T19:52:51.162Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439408975112,
                "dateRegisteredH": "2015-08-12T19:49:35.112Z"
            },
            {
                "oid": "55cd9ab3e4b0be703ae65088",
                "name": "Kerberos Zone",
                "description": "Only Kerberos Cameras",
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
                        "dateRegistered": 1439408839358,
                        "dateRegisteredH": "2015-08-12T19:47:19.358Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439537843681,
                "dateRegisteredH": "2015-08-14T07:37:23.681Z"
            }
        ]
    }
}
```
    
### Update existing zone 
Update data for an existing zone.  

###### Parameters
| Name          | Type          | Description                                       |
| ------------- | ------------- | ------------------------------------------------- |
| oid           | string        | the oid of the zone to update                     |
| name          | string        | the name of the zone                              |
| description   | string        | a description for the zone                        |
| sensorOIds    | list<string>  | the OIds of the sensors to include in the zone    |

###### Endpoint
``` http
PUT - /api/v1/json/zones
```
###### Sample Request
```json
{
    "oid": "55cba34fe4b06f9fe85278e8",
    "name": "All doors",
    "description": "Only doors",
    "sensorOIds": [
        "55cba413e4b06f9fe85278ea"
    ]
}
```
###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zones": [
            {
                "oid": "55cba34fe4b06f9fe85278e8",
                "name": "All doors",
                "description": "Only doors",
                "sensors": [
                    {
                        "oid": "55cba413e4b06f9fe85278ea",
                        "sensorId": "1000",
                        "name": "Living room",
                        "description": "Living room PIR",
                        "location": "Living room",
                        "sensorTypeId": "4",
                        "sensorTypeName": "Movement sensor without battery support",
                        "isActive": true,
                        "dateRegistered": 1439409171162,
                        "dateRegisteredH": "2015-08-12T19:52:51.162Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439408975112,
                "dateRegisteredH": "2015-08-12T19:49:35.112Z"
            },
            {
                "oid": "55cd9ab3e4b0be703ae65088",
                "name": "Kerberos Zone",
                "description": "Only Kerberos Cameras",
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
                        "dateRegistered": 1439408839358,
                        "dateRegisteredH": "2015-08-12T19:47:19.358Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439537843681,
                "dateRegisteredH": "2015-08-14T07:37:23.681Z"
            }
        ]
    }
}
```
    

### Delete zone 
Deletes a zone.

###### Parameters
| Name  | Type      | Description                   |
| ------| --------- | ----------------------------- |
| oid   | string    | the oid of the zone to delete |

###### Endpoint
``` http
DELETE - /api/v1/json/zones
```
###### Sample Request
```json
{
  "oid": "55cd9ab3e4b0be703ae65088"
}
```  
###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zones": [
            {
                "oid": "55cba34fe4b06f9fe85278e8",
                "name": "All doors",
                "description": "Only doors",
                "sensors": [
                    {
                        "oid": "55cba413e4b06f9fe85278ea",
                        "sensorId": "1000",
                        "name": "Living room",
                        "description": "Living room PIR",
                        "location": "Living room",
                        "sensorTypeId": "4",
                        "sensorTypeName": "Movement sensor without battery support",
                        "isActive": true,
                        "dateRegistered": 1439409171162,
                        "dateRegisteredH": "2015-08-12T19:52:51.162Z"
                    }
                ],
                "status": "ENABLED",
                "dateRegistered": 1439408975112,
                "dateRegisteredH": "2015-08-12T19:49:35.112Z"
            }
        ]
    }
}
```
