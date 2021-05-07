# Schemas

<h2 id="tocS_authorizationRequest">authorizationRequest</h2>
<!-- backwards compatibility -->
<a id="schemaauthorizationrequest"></a>
<a id="schema_authorizationRequest"></a>
<a id="tocSauthorizationrequest"></a>
<a id="tocsauthorizationrequest"></a>

```json
{
  "key": "string",
  "secret": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiO..."
}
```

### Properties

| Name   | Type         | Required | Restrictions | Description |
| ------ | ------------ | -------- | ------------ | ----------- |
| key    | string(uuid) | true     | none         | none        |
| secret | string       | true     | none         | none        |

<h2 id="tocS_authorizationResponse">authorizationResponse</h2>
<!-- backwards compatibility -->
<a id="schemaauthorizationresponse"></a>
<a id="schema_authorizationResponse"></a>
<a id="tocSauthorizationresponse"></a>
<a id="tocsauthorizationresponse"></a>

```json
{
  "tokenType": "Bearer",
  "token": "string",
  "expires": "2020-05-07T22:57:03Z"
}
```

### Properties

| Name      | Type              | Required | Restrictions | Description                        |
| --------- | ----------------- | -------- | ------------ | ---------------------------------- |
| tokenType | string            | false    | none         | none                               |
| token     | string(byte)      | false    | none         | none                               |
| expires   | string(date-time) | false    | none         | Expires 24 hours after registered. |

<h2 id="tocS_personalReferralLinkRequest">personalReferralLinkRequest</h2>
<!-- backwards compatibility -->
<a id="schemapersonalreferrallinkrequest"></a>
<a id="schema_personalReferralLinkRequest"></a>
<a id="tocSpersonalreferrallinkrequest"></a>
<a id="tocspersonalreferrallinkrequest"></a>

```json
{
  "email": "test@example.com",
  "campaignId": "string",
  "customerId": "string",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {},
  "seed": "string",
  "channel": "purl",
  "short": false,
  "ipAddress": "string",
  "userAgent": "api"
}
```

### Properties

| Name                      | Type          | Required | Restrictions | Description         |
| ------------------------- | ------------- | -------- | ------------ | ------------------- |
| email                     | string(email) | true     | none         | none                |
| campaignId                | string(uuid)  | true     | none         | none                |
| customerId                | string        | false    | none         | none                |
| firstName                 | string        | false    | none         | none                |
| lastName                  | string        | false    | none         | none                |
| destinationUrlQueryParams | object        | false    | none         | none                |
| seed                      | string        | false    | none         | Specifies the seed. |
| channel                   | string        | false    | none         | none                |
| short                     | boolean       | false    | none         | none                |
| ipAddress                 | string        | false    | none         | none                |
| userAgent                 | string        | false    | none         | none                |
| widgetId                  | string(uuid)  | false    | none         | none                |
| eventUrl                  | string        | false    | none         | none                |
| eventPage                 | string        | false    | none         | none                |

#### Enumerated Values

| Property | Value     |
| -------- | --------- |
| channel  | email     |
| channel  | facebook  |
| channel  | generic   |
| channel  | instagram |
| channel  | messenger |
| channel  | sms       |
| channel  | snap      |
| channel  | twitter   |
| channel  | purl      |

<h2 id="tocS_personalReferralLinkResponse">personalReferralLinkResponse</h2>
<!-- backwards compatibility -->
<a id="schemapersonalreferrallinkresponse"></a>
<a id="schema_personalReferralLinkResponse"></a>
<a id="tocSpersonalreferrallinkresponse"></a>
<a id="tocspersonalreferrallinkresponse"></a>

```json
{
  "link": "string",
  "referralCode": "string",
  "createdOn": "string"
}
```

### Properties

| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| link      | string           | true     | none         | none        |
| createdOn | string(datetime) | true     | none         | none        |

<h2 id="tocS_customerRequest">customerRequest</h2>
<!-- backwards compatibility -->
<a id="schemacustomerrequest"></a>
<a id="schema_customerRequest"></a>
<a id="tocScustomerrequest"></a>
<a id="tocscustomerrequest"></a>

```json
{
  "email": "user@example.com",
  "customerId": "string",
  "isNewCustomer": false,
  "firstName": "string",
  "lastName": "string",
  "age": 0,
  "gender": "string",
  "zipCode": "string",
  "state": "string",
  "city": "string",
  "category": "string",
  "country": "string",
  "language": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

### Properties

| Name                       | Type          | Required | Restrictions | Description |
| -------------------------- | ------------- | -------- | ------------ | ----------- |
| email                      | string(email) | true     | none         | none        |
| customerId                 | string        | true     | none         | none        |
| isNewCustomer              | boolean       | false    | none         | none        |
| firstName                  | string        | false    | none         | none        |
| lastName                   | string        | false    | none         | none        |
| age                        | integer       | false    | none         | none        |
| gender                     | string        | false    | none         | none        |
| zipCode                    | string        | false    | none         | none        |
| state                      | string        | false    | none         | none        |
| city                       | string        | false    | none         | none        |
| category                   | string        | false    | none         | none        |
| country                    | string        | false    | none         | none        |
| language                   | string        | false    | none         | none        |
| additionalProperties       | object        | false    | none         | none        |
| » **additionalProperties** | string        | false    | none         | none        |
| ipAddress                  | string        | false    | none         | none        |
| userAgent                  | string        | false    | none         | none        |

<h2 id="tocS_customerResponse">customerResponse</h2>
<!-- backwards compatibility -->
<a id="schemacustomerresponse"></a>
<a id="schema_customerResponse"></a>
<a id="tocScustomerresponse"></a>
<a id="tocscustomerresponse"></a>

```json
{
  "customerId": "string",
  "createdOn": "string"
}
```

### Properties

| Name       | Type             | Required | Restrictions | Description |
| ---------- | ---------------- | -------- | ------------ | ----------- |
| customerId | string           | true     | none         | none        |
| createdOn  | string(datetime) | true     | none         | none        |

<h2 id="tocS_purchaseEventRequest">purchaseEventRequest</h2>
<!-- backwards compatibility -->
<a id="schemapurchaseeventrequest"></a>
<a id="schema_purchaseEventRequest"></a>
<a id="tocSpurchaseeventrequest"></a>
<a id="tocspurchaseeventrequest"></a>

```json
{
  "orderId": "string",
  "email": "user@example.com",
  "customerId": "string",
  "firstName": "string",
  "lastName": "string",
  "amount": 0,
  "currency": "string",
  "isNewCustomer": false,
  "couponCode": "string",
  "attributionId": "string",
  "products": [
    {
      "sku": "string",
      "name": "string",
      "quantity": 0,
      "price": 0
    }
  ],
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

### Properties

| Name                       | Type                                                                    | Required | Restrictions | Description |
| -------------------------- | ----------------------------------------------------------------------- | -------- | ------------ | ----------- |
| orderId                    | string                                                                  | true     | none         | none        |
| email                      | string(email)                                                           | false    | none         | none        |
| customerId                 | string                                                                  | true     | none         | none        |
| firstName                  | string                                                                  | false    | none         | none        |
| lastName                   | string                                                                  | false    | none         | none        |
| amount                     | number                                                                  | true     | none         | none        |
| currency                   | string                                                                  | true     | none         | none        |
| isNewCustomer              | boolean                                                                 | false    | none         | none        |
| couponCode                 | string                                                                  | false    | none         | none        |
| attributionId              | string                                                                  | false    | none         | none        |
| products                   | [[purchaseEventRequest_products](#schemapurchaseeventrequest_products)] | false    | none         | none        |
| additionalProperties       | object                                                                  | false    | none         | none        |
| » **additionalProperties** | string                                                                  | false    | none         | none        |
| ipAddress                  | string                                                                  | false    | none         | none        |
| userAgent                  | string                                                                  | false    | none         | none        |

<h2 id="tocS_purchaseEventResponse">purchaseEventResponse</h2>
<!-- backwards compatibility -->
<a id="schemapurchaseeventresponse"></a>
<a id="schema_purchaseEventResponse"></a>
<a id="tocSpurchaseeventresponse"></a>
<a id="tocspurchaseeventresponse"></a>

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

### Properties

| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| eventId   | string(uuid)     | true     | none         | none        |
| createdOn | string(datetime) | true     | none         | none        |

<h2 id="tocS_customEventRequest">customEventRequest</h2>
<!-- backwards compatibility -->
<a id="schemacustomeventrequest"></a>
<a id="schema_customEventRequest"></a>
<a id="tocScustomeventrequest"></a>
<a id="tocscustomeventrequest"></a>

```json
{
  "email": "user@example.com",
  "eventType": "string",
  "isNewCustomer": false,
  "firstName": "string",
  "lastName": "string",
  "attributionId": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

### Properties

| Name                       | Type          | Required | Restrictions | Description |
| -------------------------- | ------------- | -------- | ------------ | ----------- |
| email                      | string(email) | true     | none         | none        |
| eventType                  | string        | true     | none         | none        |
| isNewCustomer              | boolean       | false    | none         | none        |
| firstName                  | string        | false    | none         | none        |
| lastName                   | string        | false    | none         | none        |
| attributionId              | string        | false    | none         | none        |
| couponCode                 | string        | false    | none         | none        |
| additionalProperties       | object        | false    | none         | none        |
| » **additionalProperties** | string        | false    | none         | none        |
| ipAddress                  | string        | false    | none         | none        |
| userAgent                  | string        | false    | none         | none        |

<h2 id="tocS_customEventResponse">customEventResponse</h2>
<!-- backwards compatibility -->
<a id="schemacustomeventresponse"></a>
<a id="schema_customEventResponse"></a>
<a id="tocScustomeventresponse"></a>
<a id="tocscustomeventresponse"></a>

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

### Properties

| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| eventId   | string(uuid)     | true     | none         | none        |
| createdOn | string(datetime) | true     | none         | none        |

<h2 id="tocS_signUpEventRequest">signUpEventRequest</h2>
<!-- backwards compatibility -->
<a id="schemasignupeventrequest"></a>
<a id="schema_signUpEventRequest"></a>
<a id="tocSsignupeventrequest"></a>
<a id="tocssignupeventrequest"></a>

```json
{
  "email": "user@example.com",
  "customerId": "string",
  "firstName": "string",
  "lastName": "string",
  "attributionId": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

### Properties

| Name                       | Type          | Required | Restrictions | Description |
| -------------------------- | ------------- | -------- | ------------ | ----------- |
| email                      | string(email) | true     | none         | none        |
| customerId                 | string        | true     | none         | none        |
| firstName                  | string        | false    | none         | none        |
| lastName                   | string        | false    | none         | none        |
| attributionId              | string        | false    | none         | none        |
| couponCode                 | string        | false    | none         | none        |
| additionalProperties       | object        | false    | none         | none        |
| » **additionalProperties** | string        | false    | none         | none        |
| ipAddress                  | string        | false    | none         | none        |
| userAgent                  | string        | false    | none         | none        |

<h2 id="tocS_signUpEventResponse">signUpEventResponse</h2>
<!-- backwards compatibility -->
<a id="schemasignupeventresponse"></a>
<a id="schema_signUpEventResponse"></a>
<a id="tocSsignupeventresponse"></a>
<a id="tocssignupeventresponse"></a>

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

### Properties

| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| eventId   | string(uuid)     | true     | none         | none        |
| createdOn | string(datetime) | true     | none         | none        |

<h2 id="tocS_userDataDeleteResponse">userDataDeleteResponse</h2>
<!-- backwards compatibility -->
<a id="schemauserdatadeleteresponse"></a>
<a id="schema_userDataDeleteResponse"></a>
<a id="tocSuserdatadeleteresponse"></a>
<a id="tocsuserdatadeleteresponse"></a>

```json
{
  "jobId": "string"
}
```

### Properties

| Name  | Type         | Required | Restrictions | Description |
| ----- | ------------ | -------- | ------------ | ----------- |
| jobId | string(uuid) | false    | none         | none        |

<h2 id="tocS_userDataGetResponse">userDataGetResponse</h2>
<!-- backwards compatibility -->
<a id="schemauserdatagetresponse"></a>
<a id="schema_userDataGetResponse"></a>
<a id="tocSuserdatagetresponse"></a>
<a id="tocsuserdatagetresponse"></a>

```json
{
  "emails": ["user@example.com"],
  "names": ["string"],
  "customerIds": ["string"],
  "ipAddresses": ["string"],
  "languages": ["string"],
  "userAgents": ["string"],
  "colorDepths": [0],
  "platforms": ["string"],
  "screenSizes": ["string"],
  "trackedEvents": [
    {
      "type": "string",
      "url": "string"
    }
  ],
  "shares": {
    "email": 0,
    "facebook": 0,
    "messenger": 0,
    "sms": 0,
    "twitter": 0,
    "purl": 0
  },
  "conversions": {
    "email": 0,
    "facebook": 0,
    "messenger": 0,
    "sms": 0,
    "twitter": 0,
    "purl": 0
  }
}
```

### Properties

| Name          | Type                                                                            | Required | Restrictions | Description |
| ------------- | ------------------------------------------------------------------------------- | -------- | ------------ | ----------- |
| emails        | [string]                                                                        | false    | none         | none        |
| names         | [string]                                                                        | false    | none         | none        |
| customerIds   | [string]                                                                        | false    | none         | none        |
| ipAddresses   | [string]                                                                        | false    | none         | none        |
| languages     | [string]                                                                        | false    | none         | none        |
| userAgents    | [string]                                                                        | false    | none         | none        |
| colorDepths   | [number]                                                                        | false    | none         | none        |
| platforms     | [string]                                                                        | false    | none         | none        |
| screenSizes   | [string]                                                                        | false    | none         | none        |
| trackedEvents | [[userDataGetResponse_trackedEvents](#schemauserdatagetresponse_trackedevents)] | false    | none         | none        |
| shares        | [userDataGetResponse_shares](#schemauserdatagetresponse_shares)                 | false    | none         | none        |
| conversions   | [userDataGetResponse_shares](#schemauserdatagetresponse_shares)                 | false    | none         | none        |

<h2 id="tocS_Error">Error</h2>
<!-- backwards compatibility -->
<a id="schemaerror"></a>
<a id="schema_Error"></a>
<a id="tocSerror"></a>
<a id="tocserror"></a>

```json
{
  "error": "string",
  "message": "string",
  "code": 0,
  "reference": "string"
}
```

### Properties

| Name      | Type   | Required | Restrictions | Description |
| --------- | ------ | -------- | ------------ | ----------- |
| error     | string | false    | none         | none        |
| message   | string | false    | none         | none        |
| code      | number | false    | none         | none        |
| reference | string | false    | none         | none        |

<h2 id="tocS_purchaseEventRequest_products">purchaseEventRequest_products</h2>
<!-- backwards compatibility -->
<a id="schemapurchaseeventrequest_products"></a>
<a id="schema_purchaseEventRequest_products"></a>
<a id="tocSpurchaseeventrequest_products"></a>
<a id="tocspurchaseeventrequest_products"></a>

```json
{
  "sku": "string",
  "name": "string",
  "quantity": 0,
  "price": 0
}
```

### Properties

| Name     | Type    | Required | Restrictions | Description |
| -------- | ------- | -------- | ------------ | ----------- |
| sku      | string  | true     | none         | none        |
| name     | string  | false    | none         | none        |
| quantity | integer | false    | none         | none        |
| price    | integer | false    | none         | none        |

<h2 id="tocS_userDataGetResponse_trackedEvents">userDataGetResponse_trackedEvents</h2>
<!-- backwards compatibility -->
<a id="schemauserdatagetresponse_trackedevents"></a>
<a id="schema_userDataGetResponse_trackedEvents"></a>
<a id="tocSuserdatagetresponse_trackedevents"></a>
<a id="tocsuserdatagetresponse_trackedevents"></a>

```json
{
  "type": "string",
  "url": "string"
}
```

### Properties

| Name | Type   | Required | Restrictions | Description |
| ---- | ------ | -------- | ------------ | ----------- |
| type | string | false    | none         | none        |
| url  | string | false    | none         | none        |

<h2 id="tocS_userDataGetResponse_shares">userDataGetResponse_shares</h2>
<!-- backwards compatibility -->
<a id="schemauserdatagetresponse_shares"></a>
<a id="schema_userDataGetResponse_shares"></a>
<a id="tocSuserdatagetresponse_shares"></a>
<a id="tocsuserdatagetresponse_shares"></a>

```json
{
  "email": 0,
  "facebook": 0,
  "messenger": 0,
  "sms": 0,
  "twitter": 0,
  "purl": 0
}
```

### Properties

| Name      | Type    | Required | Restrictions | Description |
| --------- | ------- | -------- | ------------ | ----------- |
| email     | integer | false    | none         | none        |
| facebook  | integer | false    | none         | none        |
| messenger | integer | false    | none         | none        |
| sms       | integer | false    | none         | none        |
| twitter   | integer | false    | none         | none        |
| purl      | integer | false    | none         | none        |
