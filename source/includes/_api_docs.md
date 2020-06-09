<!-- Generator: Widdershins v4.0.1 -->

<h1 id="merchant-api-mapi-">Merchant API Details</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Example public API for FriendBuy

Base URLs:

- <a href="https://mapi.fbot.me">https://mapi.fbot.me</a>

Email: <a href="mailto:support@friendbuy.com">Support</a>
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

## Authentication Scheme

- HTTP Authentication, scheme: bearer

## postAuthorization

<a id="opIdpostAuthorization"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/authorization \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://mapi.fbot.me/v1/authorization HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "key": "string",
  "secret": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiO..."
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('https://mapi.fbot.me/v1/authorization',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://mapi.fbot.me/v1/authorization',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('https://mapi.fbot.me/v1/authorization', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/authorization', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/authorization");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/authorization", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/authorization`

> Body parameter

```json
{
  "key": "string",
  "secret": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiO..."
}
```

<h3 id="postauthorization-parameters">Parameters</h3>

| Name     | In   | Type                                                | Required | Description |
| -------- | ---- | --------------------------------------------------- | -------- | ----------- |
| body     | body | [authorizationRequest](#schemaauthorizationrequest) | false    | none        |
| » key    | body | string(uuid)                                        | true     | none        |
| » secret | body | string                                              | true     | none        |

> Example responses

> 200 Response

```json
{
  "tokenType": "Bearer",
  "token": "string",
  "expires": "2020-05-07T22:57:03Z"
}
```

<h3 id="postauthorization-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful authorization request.            | [authorizationResponse](#schemaauthorizationresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                                 |
| 401    | [Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)            | Unauthorized                                 | [Error](#schemaerror)                                 |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                 |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                 |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                 |

<aside class="success">
This operation does not require authentication
</aside>

## postPersonalReferralLink

<a id="opIdpostPersonalReferralLink"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/personal-referral-link \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/personal-referral-link HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "test@example.com",
  "campaignId": "string",
  "customerId": "string",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {},
  "vanity": "string",
  "channel": "purl",
  "short": false,
  "ipAddress": "string",
  "userAgent": "api",
  "widgetId": "string",
  "eventUrl": "string",
  "eventPage": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/personal-referral-link',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://mapi.fbot.me/v1/personal-referral-link',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://mapi.fbot.me/v1/personal-referral-link', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/personal-referral-link', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/personal-referral-link");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/personal-referral-link", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/personal-referral-link`

_Create or retrieve a personal URL for a given customer or email address and campaign._

Generate event

> Body parameter

```json
{
  "email": "test@example.com",
  "campaignId": "string",
  "customerId": "string",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {},
  "vanity": "string",
  "channel": "purl",
  "short": false,
  "ipAddress": "string",
  "userAgent": "api",
  "widgetId": "string",
  "eventUrl": "string",
  "eventPage": "string"
}
```

<h3 id="postpersonalreferrallink-parameters">Parameters</h3>

| Name                        | In   | Type                                                              | Required | Description                          |
| --------------------------- | ---- | ----------------------------------------------------------------- | -------- | ------------------------------------ |
| body                        | body | [personalReferralLinkRequest](#schemapersonalreferrallinkrequest) | false    | none                                 |
| » email                     | body | string(email)                                                     | true     | none                                 |
| » campaignId                | body | string(uuid)                                                      | true     | none                                 |
| » customerId                | body | string                                                            | false    | none                                 |
| » firstName                 | body | string                                                            | false    | none                                 |
| » lastName                  | body | string                                                            | false    | none                                 |
| » destinationUrlQueryParams | body | object                                                            | false    | none                                 |
| » seed                      | body | string                                                            | false    | Specifies the seed for vanity links. |
| » channel                   | body | string                                                            | false    | none                                 |
| » short                     | body | boolean                                                           | false    | none                                 |
| » ipAddress                 | body | string                                                            | false    | none                                 |
| » userAgent                 | body | string                                                            | false    | none                                 |
| » widgetId                  | body | string(uuid)                                                      | false    | none                                 |
| » eventUrl                  | body | string                                                            | false    | none                                 |
| » eventPage                 | body | string                                                            | false    | none                                 |

#### Enumerated Values

| Parameter | Value     |
| --------- | --------- |
| » channel | email     |
| » channel | facebook  |
| » channel | generic   |
| » channel | instagram |
| » channel | messenger |
| » channel | sms       |
| » channel | snap      |
| » channel | twitter   |
| » channel | purl      |

> Example responses

> 200 Response

```json
{
  "link": "string",
  "createdOn": "string"
}
```

<h3 id="postpersonalreferrallink-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                                                | Schema                                                              |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Personal referral link already exists - returning the pre-existing record. | [personalReferralLinkResponse](#schemapersonalreferrallinkresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                                              | [Error](#schemaerror)                                               |
| 404    | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)             | Not found - campaign does not exist or is inactive.                        | [Error](#schemaerror)                                               |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                                                       | [Error](#schemaerror)                                               |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                                                          | [Error](#schemaerror)                                               |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure)                               | [Error](#schemaerror)                                               |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## postPurchaseEvent

<a id="opIdpostPurchaseEvent"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/event/purchase \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/event/purchase HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "orderId": "string",
  "email": "user@example.com",
  "customerId": "string",
  "firstName": "string",
  "lastName": "string",
  "amount": 0,
  "currency": "string",
  "isNewCustomer": false,
  "couponCode": "string",
  "refCode": "string",
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
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/event/purchase',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://mapi.fbot.me/v1/event/purchase',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://mapi.fbot.me/v1/event/purchase', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/event/purchase', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/event/purchase");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/event/purchase", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/event/purchase`

_Generate purchase event._

Generate purchase event

> Body parameter

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
  "refCode": "string",
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

<h3 id="postpurchaseevent-parameters">Parameters</h3>

| Name                        | In   | Type                                                                    | Required | Description |
| --------------------------- | ---- | ----------------------------------------------------------------------- | -------- | ----------- |
| body                        | body | [purchaseEventRequest](#schemapurchaseeventrequest)                     | false    | none        |
| » orderId                   | body | string                                                                  | true     | none        |
| » email                     | body | string(email)                                                           | false    | none        |
| » customerId                | body | string                                                                  | true     | none        |
| » firstName                 | body | string                                                                  | false    | none        |
| » lastName                  | body | string                                                                  | false    | none        |
| » amount                    | body | number                                                                  | true     | none        |
| » currency                  | body | string                                                                  | true     | none        |
| » isNewCustomer             | body | boolean                                                                 | false    | none        |
| » couponCode                | body | string                                                                  | false    | none        |
| » refCode                   | body | string                                                                  | false    | none        |
| » products                  | body | [[purchaseEventRequest_products](#schemapurchaseeventrequest_products)] | false    | none        |
| »» sku                      | body | string                                                                  | true     | none        |
| »» name                     | body | string                                                                  | false    | none        |
| »» quantity                 | body | integer                                                                 | false    | none        |
| »» price                    | body | integer                                                                 | false    | none        |
| » additionalProperties      | body | object                                                                  | false    | none        |
| »» **additionalProperties** | body | string                                                                  | false    | none        |
| » ipAddress                 | body | string                                                                  | false    | none        |
| » userAgent                 | body | string                                                                  | false    | none        |

> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postpurchaseevent-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [purchaseEventResponse](#schemapurchaseeventresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                                 |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                 |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                 |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                 |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## postSignUpEvent

<a id="opIdpostSignUpEvent"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/event/account-sign-up \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/event/account-sign-up HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "user@example.com",
  "customerId": "string",
  "firstName": "string",
  "lastName": "string",
  "refCode": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/event/account-sign-up',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://mapi.fbot.me/v1/event/account-sign-up',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://mapi.fbot.me/v1/event/account-sign-up', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/event/account-sign-up', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/event/account-sign-up");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/event/account-sign-up", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/event/account-sign-up`

_Generate sign-up event._

Generate sign-up event.

> Body parameter

```json
{
  "email": "user@example.com",
  "customerId": "string",
  "firstName": "string",
  "lastName": "string",
  "refCode": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

<h3 id="postsignupevent-parameters">Parameters</h3>

| Name                        | In   | Type                                            | Required | Description |
| --------------------------- | ---- | ----------------------------------------------- | -------- | ----------- |
| body                        | body | [signUpEventRequest](#schemasignupeventrequest) | false    | none        |
| » email                     | body | string(email)                                   | true     | none        |
| » customerId                | body | string                                          | true     | none        |
| » firstName                 | body | string                                          | false    | none        |
| » lastName                  | body | string                                          | false    | none        |
| » refCode                   | body | string                                          | false    | none        |
| » couponCode                | body | string                                          | false    | none        |
| » additionalProperties      | body | object                                          | false    | none        |
| »» **additionalProperties** | body | string                                          | false    | none        |
| » ipAddress                 | body | string                                          | false    | none        |
| » userAgent                 | body | string                                          | false    | none        |

> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postsignupevent-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                            |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [signUpEventResponse](#schemasignupeventresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                             |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                             |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                             |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                             |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## postCustomEvent

<a id="opIdpostCustomEvent"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/event/custom \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/event/custom HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "email": "user@example.com",
  "eventType": "string",
  "isNewCustomer": false,
  "firstName": "string",
  "lastName": "string",
  "refCode": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/event/custom',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://mapi.fbot.me/v1/event/custom',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://mapi.fbot.me/v1/event/custom', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/event/custom', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/event/custom");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/event/custom", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/event/custom`

_Generate a custom event where the structure of the general structure of the request body object is defined by the client._

Generate event

> Body parameter

```json
{
  "email": "user@example.com",
  "eventType": "string",
  "isNewCustomer": false,
  "firstName": "string",
  "lastName": "string",
  "refCode": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "api"
}
```

<h3 id="postcustomevent-parameters">Parameters</h3>

| Name                        | In   | Type                                            | Required | Description |
| --------------------------- | ---- | ----------------------------------------------- | -------- | ----------- |
| body                        | body | [customEventRequest](#schemacustomeventrequest) | false    | none        |
| » email                     | body | string(email)                                   | true     | none        |
| » eventType                 | body | string                                          | true     | none        |
| » isNewCustomer             | body | boolean                                         | false    | none        |
| » firstName                 | body | string                                          | false    | none        |
| » lastName                  | body | string                                          | false    | none        |
| » refCode                   | body | string                                          | false    | none        |
| » couponCode                | body | string                                          | false    | none        |
| » additionalProperties      | body | object                                          | false    | none        |
| »» **additionalProperties** | body | string                                          | false    | none        |
| » ipAddress                 | body | string                                          | false    | none        |
| » userAgent                 | body | string                                          | false    | none        |

> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postcustomevent-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                            |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [customEventResponse](#schemacustomeventresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                             |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                             |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                             |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                             |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## postCustomer

<a id="opIdpostCustomer"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/customer \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/customer HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
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
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/customer',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://mapi.fbot.me/v1/customer',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://mapi.fbot.me/v1/customer', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://mapi.fbot.me/v1/customer', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/customer");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/customer", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/customer`

_Add a new customer to our records._

Generate event

> Body parameter

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

<h3 id="postcustomer-parameters">Parameters</h3>

| Name                        | In   | Type                                      | Required | Description |
| --------------------------- | ---- | ----------------------------------------- | -------- | ----------- |
| body                        | body | [customerRequest](#schemacustomerrequest) | false    | none        |
| » email                     | body | string(email)                             | true     | none        |
| » customerId                | body | string                                    | true     | none        |
| » isNewCustomer             | body | boolean                                   | false    | none        |
| » firstName                 | body | string                                    | false    | none        |
| » lastName                  | body | string                                    | false    | none        |
| » age                       | body | integer                                   | false    | none        |
| » gender                    | body | string                                    | false    | none        |
| » zipCode                   | body | string                                    | false    | none        |
| » state                     | body | string                                    | false    | none        |
| » city                      | body | string                                    | false    | none        |
| » category                  | body | string                                    | false    | none        |
| » country                   | body | string                                    | false    | none        |
| » language                  | body | string                                    | false    | none        |
| » additionalProperties      | body | object                                    | false    | none        |
| »» **additionalProperties** | body | string                                    | false    | none        |
| » ipAddress                 | body | string                                    | false    | none        |
| » userAgent                 | body | string                                    | false    | none        |

> Example responses

> 200 Response

```json
{
  "customerId": "string",
  "createdOn": "string"
}
```

<h3 id="postcustomer-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                      |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Customer already exists - updated            | [customerResponse](#schemacustomerresponse) |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Customer created                             | [customerResponse](#schemacustomerresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                       |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                       |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                       |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                       |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getUserData

<a id="opIdgetUserData"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/user-data \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/user-data HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch("https://mapi.fbot.me/v1/user-data", {
  method: "GET",

  headers: headers,
})
  .then(function (res) {
    return res.json();
  })
  .then(function (body) {
    console.log(body);
  });
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://mapi.fbot.me/v1/user-data',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/user-data', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://mapi.fbot.me/v1/user-data', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/user-data");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/user-data", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/user-data`

<h3 id="getuserdata-parameters">Parameters</h3>

| Name       | In    | Type          | Required | Description |
| ---------- | ----- | ------------- | -------- | ----------- |
| email      | query | string(email) | false    | none        |
| customerId | query | string        | false    | none        |

> Example responses

> 200 Response

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

<h3 id="getuserdata-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                            |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful user data get request.            | [userDataGetResponse](#schemauserdatagetresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                             |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                             |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                             |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                             |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## deleteUserData

<a id="opIddeleteUserData"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE https://mapi.fbot.me/v1/user-data \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
DELETE https://mapi.fbot.me/v1/user-data HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch("https://mapi.fbot.me/v1/user-data", {
  method: "DELETE",

  headers: headers,
})
  .then(function (res) {
    return res.json();
  })
  .then(function (body) {
    console.log(body);
  });
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.delete 'https://mapi.fbot.me/v1/user-data',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.delete('https://mapi.fbot.me/v1/user-data', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('DELETE','https://mapi.fbot.me/v1/user-data', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://mapi.fbot.me/v1/user-data");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "https://mapi.fbot.me/v1/user-data", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /v1/user-data`

<h3 id="deleteuserdata-parameters">Parameters</h3>

| Name       | In    | Type          | Required | Description |
| ---------- | ----- | ------------- | -------- | ----------- |
| email      | query | string(email) | false    | none        |
| customerId | query | string        | false    | none        |

> Example responses

> 200 Response

```json
{
  "jobId": "string"
}
```

<h3 id="deleteuserdata-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                  |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful user data delete request.         | [userDataDeleteResponse](#schemauserdatadeleteresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                                   |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                   |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                   |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                   |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

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
  "vanity": "string",
  "channel": "purl",
  "short": false,
  "ipAddress": "string",
  "userAgent": "api",
  "widgetId": "string",
  "eventUrl": "string",
  "eventPage": "string"
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
| vanity                    | string        | false    | none         | Specifies the seed. |
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
  "refCode": "string",
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
| refCode                    | string                                                                  | false    | none         | none        |
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
  "refCode": "string",
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
| refCode                    | string        | false    | none         | none        |
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
  "refCode": "string",
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
| refCode                    | string        | false    | none         | none        |
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
