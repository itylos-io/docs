## Settings operations  
Description of CRUD operations for settings.

### Get settings
Returns all settings.

###### Endpoint
``` http
GET - /api/v1/json/settings
```

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "settings": {
            "systemSettings": {
                "maxAlarmPasswordRetries": 3,
                "maxSecondsToDisarm": 15,
                "delayToArm": 15,
                "playSoundsForSensorEvents": true,
                "playSoundsForTriggeredAlarm": true,
                "playSoundsForAlarmStatusUpdates":true,
                "accessToken": "teylr33ByHfAnJD8TieTjNCLid220"
            },
            "emailSettings": {
                "isEnabled": false,
                "smtpStartTLSEnabled": true,
                "smtpHost": "smtp.gmail.com",
                "smtpUser": "email@gmail.com",
                "smtpPassword": "123",
                "smtpPort": 587,
                "smtpAuth": true,
                "emailsToNotify": [
                    "john@smith.com"
                ]
            },
            "nexmoSettings": {
                "isEnabled": false,
                "nexmoKey": "nexmoKey",
                "nexmoSecret": "nexmoSecret",
                "mobilesToNotify": [
                    "306978787877"
                ]
            },
            "webHookSettings": {
                "isEnabled": false,
                "uris": [
                    "http://10.11.12.1/alarm"
                ]
            },
            "pushBulletSettings": {
                "isEnabled": false,
                "accessToken": "lr33ByHjNCLid220rnF6a60",
                "notifyForSensorEvents": true,
                "notifyForAlarms": true,
                "notifyForAlarmsStatusUpdates": true,
                "devices": [
                    {
                        "isEnabled": true,
                        "iden": "uj3a60s2gAq",
                        "deviceName": "Asus Nexus 7"
                    },
                    {
                        "isEnabled": true,
                        "iden": "uja60djVsKn",
                        "deviceName": "Chrome"
                    }
                ]
            }
        }
    }
}
```

### Update system settings
Update the system settings only

###### Parameters
| Name                              | Type    | Description                                                               |
| --------------------------------- | ------- | ------------------------------------------------------------------------- |
| maxAlarmPasswordRetries           | string  | how many false retries before triggering alarm                            |
| maxSecondsToDisarm                | string  | how many seconds before triggering alarm after no deactivation of alarm   |
| delayToArm                        | string  | how many seconds before arming the system                                 |
| playSoundsForSensorEvents         | string  | if true sounds will be played on server if new sensor event is submitted  |
| playSoundsForTriggeredAlarm       | string  | if true sounds will be played on server if alarm is triggered             |
| playSoundsForAlarmStatusUpdates   | string  | if true sounds will be played on server if alarm status changes
| accessToken                       | boolean | the itylos.io access token                                                |

###### Endpoint
``` http
POST - /api/v1/json/settings/system
```

###### Sample Request
```json
{
    "maxAlarmPasswordRetries": 3,
    "maxSecondsToDisarm": 15,
    "delayToArm": 15,
    "playSoundsForSensorEvents": true,
    "playSoundsForTriggeredAlarm": true,
    "playSoundsForAlarmStatusUpdates":true,
    "accessToken": "teylr33ByHfAnJD8TieTjNCLid220"
}
```
  
### Update email settings
Update the email settings only
  
###### Parameters
| Name            | Type          | Description                                          |
| ----------------| ------------- | ---------------------------------------------------- |
| isEnabled       | boolean       | if true, emails will be sent when alarm is triggered |
| emailsToNotify  | list<string>  | the emails to which notifications will be sent to    |

###### Endpoint
``` http
POST - /api/v1/json/settings/email
```

###### Sample Request
```json
{
    "isEnabled": false,
    "smtpStartTLSEnabled": true,
    "smtpHost": "smtp.gmail.com",
    "smtpUser": "admin@gmail.com",
    "smtpPassword": "123foo123",
    "smtpPort": 587,
    "smtpAuth": true,
    "emailsToNotify": [
        "john@smith.com"
    ]
}
```
  
### Update nexmo settings
Update the nexmo service settings only
  
###### Parameters
| Name            | Type          | Description                                           |
| ----------------| ------------- | ----------------------------------------------------  |
| isEnabled       | boolean       | if true, emails will be sent when alarm is triggered  |
| nexmoKey        | string        | the key from the nexmo service                        |
| nexmoSecret     | string        | the secret from the nexmo service                     |
| mobilesToNotify | list<string>  | the mobiles to which notifications will be sent to    |

###### Endpoint
``` http
POST - /api/v1/json/settings/email
```

###### Sample Request
```json
{
    "isEnabled": true,
    "nexmoKey": "nexmoKey",
    "nexmoSecret": "nexmoSecret",
    "mobilesToNotify": [
        "306978787877"
    ]
}
```
  
### Get pushbullet devices
Returns the configured devices directly from the pushbullet service. Use the result to update pushbullet settings
  
###### Parameters
| Name                  | Type    | Description                                                 |
| ----------------------| ------- | ----------------------------------------------------------  |
| pushBulletAccessToken | string  | The access token as retrieved from the pushbullet dashboard |

###### Endpoint
``` http
GET - /api/v1/json/settings/pushbullet/devices/{pushBulletAccessToken}
```

###### Sample Request
```json
{
  "meta": {
    "code": 200
  },
  "response": {
    "devices": [
      {
        "isEnabled": true,
        "iden": "ujnF6aeRE",
        "deviceName": "Galaxy Note II"
      },
      {
        "isEnabled": true,
        "iden": "unF6a60sj",
        "deviceName": "Asus Nexus 7"
      },
      {
        "isEnabled": true,
        "iden": "ujAD3nF6a",
        "deviceName": "Chrome"
      }
    ]
  }
}
```
 
### Update pushbullet settings
Update the pushbullet service settings only
  
###### Parameters
| Name                        | Type          | Description                                                   |
| ----------------------------| ------------- | ------------------------------------------------------------  |
| isEnabled                   | boolean       | if true, pushbullet notifications will be sent                |
| accessToken                 | string        | the pushbullet access token                                   |
| notifyForSensorEvents       | boolean       | if true, notifications for sensor events will be sent         |
| notifyForAlarms             | boolean       | if true, notifications for triggered alarms will be sent      |
| notifyForAlarmsStatusUpdates| boolean       | if true, notifications for alarms status updates will be sent |
| devices                     | list<device>  | the devices to which notifications will be sent               |

###### Endpoint
``` http
POST - /api/v1/json/settings/pushbullet
```

###### Sample Request
```json
{
    "isEnabled": true,
    "accessToken": "TieTjNCLid220",
    "notifyForSensorEvents": true,
    "notifyForAlarms": false,
    "notifyForAlarmsStatusUpdates": true,
    "devices": [
        {
            "isEnabled": true,
            "iden": "ujADasq",
            "deviceName": "Asus Nexus 7"
        },
        {
            "isEnabled": true,
            "iden": "ujADasqs",
            "deviceName": "Chrome"
        }
    ]
}
```