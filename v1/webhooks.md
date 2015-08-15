## Webhooks Description

Webhooks allow you to easily integrate Itylos.io with external apps.
When an event is triggered, Itylos.io will send a HTTP POST payload to the webhook’s configured URLs. 

Webhooks can be used for example to:   
* trigger a custom TCP/IP siren
* trigger an external alarm system
* trigger a custom notification service
* and much more...

Itylos.io will send a HTTP POST payload when:
* alarm is triggered
* new sensor event is submitted
* alarm status gets updated

### Alarm triggered event
When alarm has been triggered the following payload will be sent:
```json
{
    "eventType": "alarmTriggered"
}
```
 
### New sensor event detected
When a new sensor event has been detected the following payload will be sent:
```json
{
    "eventType": "newSensorEvent",
    "message": {
        "oid": "",
        "sensorId": "200",
        "sensorName": "Garage Door",
        "sensorLocation": "Garage",
        "status": "OPEN",
        "dateOfEvent": 1436083463420,
        "dateOfEventH": "2015-07-05T08:04:23.420Z"
    }
}
``` 

### Alarm status updated
When alarm status gets updated the following payload will be sent:
```json
{
    "eventType": "updatedAlarmStatus",
    "message": {
        "currentStatus": "ARMED",
        "user": {
            "oid": "5570d45fc8306a6aa138c6c6",
            "userId": "5570d45fc8306a6aa138c6c6",
            "name": "Angelos",
            "email": "admin@itylos.io",
            "phones": [
                "6945144024"
            ],
            "dateRegistered": 1434718767929,
            "dateRegisteredH": "2015-06-19T12:59:27.929Z",
            "isAdmin": true
        }
    }
}
``` 

