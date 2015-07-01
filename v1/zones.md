## Zones CRUD operations     
Description of al resources related to zone management (create, edit, delete and updated a zone)  

### Creates new zone 
###### Endpoint
``` http
PUT - /api/v1/json/zones  
```
###### Sample Request
```json
{
    "name": "test",
    "description": "test window upper right corner",
    "sensorOIds": [
        "5505d954be5065d8a5e18143",
        "5505d96ebe5065d8a5e18144"
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
                "oid": "54eb6dfdbe50c9c1a039cfc5",
                "name": "Garage",
                "description": "Garage door and window",
                "sensors": [
                    {
                        "oid": "54eb5198be5036eb7cc530ba",
                        "sensorId": "11100111",
                        "name": "Garage window",
                        "description": "Small garage window",
                        "location": "Garage",
                        "sensorTypeId": "1",
                        "sensorTypeName": "400MHZ 2262 wireless door window sensor",
                        "isActive": true,
                        "dateRegistered": "2015-02-23T18:16:00.192Z"
                    },
                    {
                        "oid": "54eb0435be5077ad51f8dc4f",
                        "sensorId": "11110001",
                        "name": "Garage door",
                        "description": "Garage door",
                        "location": "Garage",
                        "sensorTypeId": "1",
                        "sensorTypeName": "400MHZ 2262 wireless door window sensor",
                        "isActive": true,
                        "dateRegistered": "2015-02-23T18:16:45.192Z"
                    }
                ],
                "dateRegistered": "2015-02-23T18:14:21.171Z"
            }
        ]
    }
}
```    
### Update existing zone 
###### Endpoint
``` http
POST - /api/v1/json/zones  
```
###### Sample Request
```json
{
    "oid": "54eb5587be50f54e60d461bc",
    "name": "Kitchen Window A",
    "description": "Small window upper right corner",
    "sensorOIds": ["54eb5198be5036eb7cc530ba"]
}
```  
######  Response

```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "zones": [
            {
                "oid": "54eb6dfdbe50c9c1a039cfc5",
                "name": "Garage",
                "description": "Garage door and window",
                "sensors": [
                    {
                        "oid": "54eb5198be5036eb7cc530ba",
                        "sensorId": "11100111",
                        "name": "Garage window",
                        "description": "Small garage window",
                        "location": "Garage",
                        "sensorTypeId": "1",
                        "sensorTypeName": "400MHZ 2262 wireless door window sensor",
                        "isActive": true,
                        "dateRegistered": "2015-02-23T18:16:00.192Z"
                    },
                    {
                        "oid": "54eb0435be5077ad51f8dc4f",
                        "sensorId": "11110001",
                        "name": "Garage door",
                        "description": "Garage door",
                        "location": "Garage",
                        "sensorTypeId": "1",
                        "sensorTypeName": "400MHZ 2262 wireless door window sensor",
                        "isActive": true,
                        "dateRegistered": "2015-02-23T18:16:45.192Z"
                    }
                ],
                "dateRegistered": "2015-02-23T18:14:21.171Z"
            }
        ]
    }
}
```  

