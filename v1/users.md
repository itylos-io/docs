## Users operations  
Description of CRUD operations for users.

### Get users
Returns all users.

###### Endpoint
``` http
GET - /api/v1/json/user
```

###### Sample Response
    
```json
{
    "meta": {
        "code": 200
    },
    "response": {
        "users": [
            {
                "oid": "55716b0480742ee3ca156947",
                "userId": "55716b0480742ee3ca156947",
                "name": "Stefanos",
                "email": "stefanos@gmail.com",
                "webPassword": "123456",
                "alarmPassword": "1234",
                "dateRegistered": 1434718758157,
                "dateRegisteredH": "2015-06-19T12:59:18.157Z",
                "isAdmin": true
            },
            {
                "oid": "5570d45fc8306a6aa138c6c6",
                "userId": "5570d45fc8306a6aa138c6c6",
                "name": "Angelos",
                "email": "admin@myhome.com",
                "webPassword": "123456",
                "alarmPassword": "1234",
                "dateRegistered": 1434718767929,
                "dateRegisteredH": "2015-06-19T12:59:27.929Z",
                "isAdmin": true
            }
        ]
    }
}
```

### Create user
Create new user

###### Parameters
| Name          | Type          | Description                                       |
| --------------| ------------- | ------------------------------------------------- |
| name          | string        | the user's name                                   |
| email         | string        | the user's email                                  |
| webPassword   | string        | the user's password to login to itylos dashboard  |
| alarmPassword | string        | the user's password to arm/disarm system          |
| isAdmin       | boolean       | if true, user is admin                            |

###### Endpoint
``` http
POST - /api/v1/json/users
```

###### Sample Request
```json
{
    "name": "John",
    "email": "john@smith.com",
    "webPassword": "123456",
    "alarmPassword": "1234",
    "isAdmin": true
}
```
  
### Update user
Update a user's data
  
###### Parameters
| Name          | Type          | Description                                       |
| --------------| ------------- | ------------------------------------------------- |
| oid           | string        | the oid of the user to update                     |
| name          | string        | the user's name                                   |
| email         | string        | the user's email                                  |
| webPassword   | string        | the user's password to login to itylos dashboard  |
| alarmPassword | string        | the user's password to arm/disarm system          |
| isAdmin       | boolean       | if true, user is admin                            |

###### Endpoint
``` http
PUT - /api/v1/json/users
```

###### Sample Request
```json
{
  "oid":"55648592c83070c2ce02e48c",
  "email": "apetheriotis@gmail.com",
  "name":"Angelos",
  "webPassword": "123456",
  "alarmPassword": "1234",
  "isAdmin": true
}
```
  
### Delete user
Delete a user
  
###### Parameters
| Name  | Type      | Description                   |
| ------| --------- | ----------------------------  |
| oid   | string    | the oid of the user to delete |

###### Endpoint
``` http
DELETE - /api/v1/json/users
```

###### Sample Request
```json
{
   "oid":"55646783c830bf758cbe6f43"
}
```
