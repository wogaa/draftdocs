# Data Glossary

!!! abstract This section shall cover the **raw data fields** tracked and their definitions.

!!! warning This document is not complete and is subjected to further changes and updates.

## Event Level Contexts

!!! info The following data points are the base fields collected regardless of event type being triggered.

### User Related Fields

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| network\_userid | text | User ID set by Snowplow using 3rd party cookie | No | 'ecdff4d0-9175-40ac-a8bb-325c49733607' |
| user\_ipaddress | text | User IP address | No | '92.231.54.234' |

### Device Fields

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| useragent | text | Raw useragent | Yes |  |
| dvce\_screenheight | int | Screen height in pixels | No | 1024 |
| dvce\_screenwidth | int | Screen width in pixels | No | 1900 |

### Location Fields

!!! info As of version 1.1.4, GPS geo-location data is not captured and will only be derived from the IP address. In prior versions, GPS geo-location data is only captured when GPS location access is granted by the user for the Mobile App.

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| geo\_country | text | ISO 3166-1 code for the country the visitor is located in | No | 'GB', 'US' |
| geo\_region | text | ISO-3166-2 code for country region the visitor is in | No | 'I9', 'TX' |
| geo\_city | text | City the visitor is in | No | 'New York', 'London' |
| geo\_zipcode | text | Postcode the visitor is in | No | '94109' |
| geo\_latitude | text | Visitor location latitude | No | 37.443604 |
| geo\_longitude | text | Visitor location longitude | No | -122.4124 |
| geo\_region\_name | text | Visitor region name | No | 'Florida' |
| geo\_timezone | text | Visitor timezone name | No | 'Europe/London' |

### Custom Tracking Fields

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| se\_category | text | Category of event | Yes | 'ecomm', 'video' |
| se\_action | text | Action performed / event name | Yes | 'add-to-basket', 'play-video' |
| se\_label | text | The object of the action e.g. the ID of the video played or SKU of the product added-to-basket | No | pbz00123' |
| se\_property | text | A property associated with the object of the action | No | HD', 'large' |
| se\_value | decimal | A value associated with the event / action e.g. the value of goods added-to-basket | No |  |

## Mobile Specific Contexts

!!! info The following contexts have been implemented by WOGAA Mobile and will be tracked on specific events taking place on the app.

| Schema Name | Description |
| :--- | :--- |
| [Application]() | Schema for an application context which automatically tracks version number and build name when using the mobile SDKs |
| [Application Background]() | Schema for an application background event |
| [Application Error]() | Schema for an application error |
| [Application Foreground]() | Schema for an application foreground event |
| [Application Install]() | Schema for an event where a mobile application is installed |
| [Client Session]() | Schema for a client-generated user session |
| [Mobile Context]() | Schema for mobile contexts |
| [Screen View]() | Schema for a screen view event |
| [Screen]() | Schema for a context that represents information pertaining to the current screen being viewed when an event occurs |

### Application

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| version | string | Version number of the application | Yes | 1.1.0 |
| build | string | Build name of the application | Yes | 1.1.0 beta |

### Application Background

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| backgroundIndex | integer | The running index of the moment app goes into user background | No | 1 |

### Application Error

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| programmingLanguage | enum | The undelying programming language used | Yes | JAVA |
| message | string | The error message | Yes |  |
| threadName | string |  | No |  |
| threadId | integer |  | No |  |
| stackTrace | string |  | No |  |
| causeStackTrace | string |  | No |  |
| lineNumber | integer |  | No |  |
| className | string |  | No |  |
| exceptionName | string |  | No |  |
| isFatal | boolean |  | No |  |
| lineColumn | integer |  | No |  |
| fileName | string |  | No |  |

### Application Foreground

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| foregroundIndex | integer | The running index of the moment app comes into user foreground in session | No | 1 |

### Application Install

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| root\_id | string | An `application_install` event is triggered and recorded | Yes |  |

### Client Session

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| userId | string | The userId used | Yes |  |
| sessionId | string | A unique uuid to identify a specific session | Yes | 06ed76c5-d27d-4992-b0b7-92faf52c745b |
| sessionIndex | integer |  | Yes |  |
| previousSessionId | string | The unique uuid of the previous session | Yes | c5dba3c8-fa05-466e-9e14-57b326c03ce5 |
| storageMechanism | enum | The storage location of the client information | Yes | SQLITE, COOKIE\_1, COOKIE\_3, LOCAL\_STORAGE, FLASH\_LSO |
| firstEventIds | string | The uuid of the first event in the session | No |  |

### Mobile Context

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| osType | string | The operating system of the device | Yes | android |
| osVersion | string | The version of the operating system used | Yes | 10 |
| deviceManufacturer | string | The manufacturer of the device | Yes | Google |
| deviceModel | string | The model of the device used | Yes | Pixel 2 XL |
| carrier | string | The service provider used | No | Singtel |
| networkType | enum | The type of network connection used to access service | No | mobile, wifi, offline |
| networkTechnology | string |  | No |  |
| openIdfa | string | [OpenIDFA Github](https://github.com/ylechelle/OpenIDFA) | No |  |
| appleIdfa | string | An alphanumeric string unique to each device, used only for serving ads | No | [reference](https://developer.apple.com/documentation/adsupport/asidentifiermanager) |
| appleIdfv | string | An alphanumeric string that uniquely identifies a device to the app's vendor | No | [reference](https://developer.apple.com/documentation/uikit/uidevice/1620059-identifierforvendor) |
| androidIdfa | string | The Android Idfa code is a unique identifier for google advertising | No |  |

### Screen View

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| name | string | The name of the screen viewed | Yes |  |
| type | string | The type of screen that was viewed | No | feed, carousel |
| id | string | An unique uuid from the associated screenview event | Yes |  |
| previousName | string | The name of the previous screen | No |  |
| previousId | string | The uuid of the previous screenview |  |  |
| previousType | string | The screen type of the previous screenview | No |  |
| transitionType | string | The type of transition that led to the screen being viewed | No |  |

### Screen

| Data Field | Type | Description | Required | Example |
| :--- | :--- | :--- | :--- | :--- |
| name | string | The name of the screen viewed | Yes |  |
| type | string | The type of screen that was viewed | No |  |
| id | string | A uuid from the associated screenview event | Yes |  |
| viewController | string | iOS specific : class name of the view controller | No |  |
| topViewController | string | iOS specific: class name of the top level view controller | No |  |
| activity | string | Android specific: name of activity | No |  |
| fragment | string | Android specific: name of fragment | No |  |

