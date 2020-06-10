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

| Name     | In   | Type                                                | Required | Description         |
| -------- | ---- | --------------------------------------------------- | -------- | ------------------- |
| body     | body | [authorizationRequest](#schemaauthorizationrequest) | false    | none                |
| » key    | body | string(uuid)                                        | true     | Your api access key |
| » secret | body | string                                              | true     | Your api secret key |

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

| Name                        | In   | Type                                                              | Required | Description                                                                                      |
| --------------------------- | ---- | ----------------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| body                        | body | [personalReferralLinkRequest](#schemapersonalreferrallinkrequest) | false    | none                                                                                             |
| » email                     | body | string(email)                                                     | true     | Email of the advocate.                                                                           |
| » campaignId                | body | string(uuid)                                                      | true     | ID of the campaign to use to generate the link.                                                  |
| » customerId                | body | string                                                            | false    | Your customer id for the advocate.                                                               |
| » firstName                 | body | string                                                            | false    | First name of the advocate.                                                                      |
| » lastName                  | body | string                                                            | false    | Last name of the advocate.                                                                       |
| » destinationUrlQueryParams | body | object                                                            | false    | Custom parameters to be inserted into the url that users are directed to when clicking the link. |
| » seed                      | body | string                                                            | false    | Specifies what the vanity url will be based on if provided.                                      |
| » channel                   | body | string                                                            | false    | The share channel the link will be associated with in analytics. Recommended value is "purl".    |
| » short                     | body | boolean                                                           | false    | none                                                                                             |
| » ipAddress                 | body | string                                                            | false    | IP Address of the advocate. Used for fraud checks.                                               |
| » userAgent                 | body | string                                                            | false    | User Agent of the advocate. Used for fraud checks.                                               |
| » widgetId                  | body | string(uuid)                                                      | false    | none                                                                                             |
| » eventUrl                  | body | string                                                            | false    | none                                                                                             |
| » eventPage                 | body | string                                                            | false    | none                                                                                             |

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

| Name                        | In   | Type                                                                    | Required | Description                                                                                          |
| --------------------------- | ---- | ----------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------- |
| body                        | body | [purchaseEventRequest](#schemapurchaseeventrequest)                     | false    | none                                                                                                 |
| » orderId                   | body | string                                                                  | true     | Unique order id for the purchase.                                                                    |
| » email                     | body | string(email)                                                           | false    | Email of the customer making the purchase.                                                           |
| » customerId                | body | string                                                                  | true     | Customer ID of the customer making the purchase.                                                     |
| » firstName                 | body | string                                                                  | false    | First name of the customer making the purchase.                                                      |
| » lastName                  | body | string                                                                  | false    | Last name of the customer making the purchase.                                                       |
| » amount                    | body | number                                                                  | true     | The order total for the purchase.                                                                    |
| » currency                  | body | string                                                                  | true     | The currency used for the purchase (i.e. USD).                                                       |
| » isNewCustomer             | body | boolean                                                                 | false    | Whether or not the customer making the purchase has made a previous purchase.                        |
| » couponCode                | body | string                                                                  | false    | The coupon code used in the purchase, if any. Can be used to establish attribution with an advocate. |
| » refCode                   | body | string                                                                  | false    | The referral code from the advocate's referral link, if any.                                         |
| » additionalProperties      | body | object                                                                  | false    | Any additional properties you wish to track with the purchase.                                       |
| »» **additionalProperties** | body | string                                                                  | false    | A key value pair indicating the property name and value.                                             |
| » ipAddress                 | body | string                                                                  | false    | IP address of the customer making the purchase.                                                      |
| » userAgent                 | body | string                                                                  | false    | User Agent of the customer making the purchase.                                                      |
| » products                  | body | [[purchaseEventRequest_products](#schemapurchaseeventrequest_products)] | false    | An array of purchased products.                                                                      |
| »» sku                      | body | string                                                                  | true     | The SKU of the product.                                                                              |
| »» name                     | body | string                                                                  | false    | The name of the product.                                                                             |
| »» quantity                 | body | integer                                                                 | false    | The number of this product bought.                                                                   |
| »» price                    | body | integer                                                                 | false    | The individual price of this product.                                                                |
|                             |

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

| Name                        | In   | Type                                            | Required | Description                                                                                        |
| --------------------------- | ---- | ----------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------- |
| body                        | body | [signUpEventRequest](#schemasignupeventrequest) | false    | none                                                                                               |
| » email                     | body | string(email)                                   | true     | Email of the user signing up.                                                                      |
| » customerId                | body | string                                          | true     | Customer id of the user.                                                                           |
| » firstName                 | body | string                                          | false    | First name of the user.                                                                            |
| » lastName                  | body | string                                          | false    | Last name of the user.                                                                             |
| » refCode                   | body | string                                          | false    | The referral code from the advocate's referral link, if any.                                       |
| » couponCode                | body | string                                          | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| » additionalProperties      | body | object                                          | false    | Any additional properties you wish to track with this signup.                                      |
| »» **additionalProperties** | body | string                                          | false    | A key value pair representing the name of the property and the value.                              |
| » ipAddress                 | body | string                                          | false    | The IP address of the user.                                                                        |
| » userAgent                 | body | string                                          | false    | The User Agent of the user.                                                                        |

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

| Name                        | In   | Type                                            | Required | Description                                                                                        |
| --------------------------- | ---- | ----------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------- |
| body                        | body | [customEventRequest](#schemacustomeventrequest) | false    | none                                                                                               |
| » email                     | body | string(email)                                   | true     | Email of the user performing the event.                                                            |
| » eventType                 | body | string                                          | true     | The type of the event you are tracking (i.e. "newsletter signup", "video view", etc).              |
| » isNewCustomer             | body | boolean                                         | false    | Whether or not the user is a new customer.                                                         |
| » firstName                 | body | string                                          | false    | First name of the user.                                                                            |
| » lastName                  | body | string                                          | false    | Last name of the user.                                                                             |
| » refCode                   | body | string                                          | false    | The referral code from the advocate's referral link, if any.                                       |
| » couponCode                | body | string                                          | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| » additionalProperties      | body | object                                          | false    | Any additional properties you wish to track with the event.                                        |
| »» **additionalProperties** | body | string                                          | false    | A key value pair representing the name and value of the additional property.                       |
| » ipAddress                 | body | string                                          | false    | IP Address of the user.                                                                            |
| » userAgent                 | body | string                                          | false    | User Agent of the user.                                                                            |

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

| Name                        | In   | Type                                      | Required | Description                                                           |
| --------------------------- | ---- | ----------------------------------------- | -------- | --------------------------------------------------------------------- |
| body                        | body | [customerRequest](#schemacustomerrequest) | false    | none                                                                  |
| » email                     | body | string(email)                             | true     | Email of the customer.                                                |
| » customerId                | body | string                                    | true     | Your id for the customer.                                             |
| » isNewCustomer             | body | boolean                                   | false    | Whether or not the customer has purchsed before.                      |
| » firstName                 | body | string                                    | false    | First name of the customer.                                           |
| » lastName                  | body | string                                    | false    | Last name of the customer.                                            |
| » age                       | body | integer                                   | false    | Age of the customer.                                                  |
| » gender                    | body | string                                    | false    | Gender of the customer.                                               |
| » zipCode                   | body | string                                    | false    | Zip code of the customer.                                             |
| » state                     | body | string                                    | false    | State the customer lives in.                                          |
| » city                      | body | string                                    | false    | The customer's city.                                                  |
| » category                  | body | string                                    | false    | The category the customer is in, if any.                              |
| » country                   | body | string                                    | false    | The customer's country.                                               |
| » language                  | body | string                                    | false    | The customer's preferred language.                                    |
| » additionalProperties      | body | object                                    | false    | Any additional properties you wish to track with this customer.       |
| »» **additionalProperties** | body | string                                    | false    | A key value pair representing the name of the property and its value. |
| » ipAddress                 | body | string                                    | false    | IP address of the customer.                                           |
| » userAgent                 | body | string                                    | false    | User Agent of the customer.                                           |

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

| Name       | In    | Type          | Required | Description               |
| ---------- | ----- | ------------- | -------- | ------------------------- |
| email      | query | string(email) | false    | Email of the user.        |
| customerId | query | string        | false    | Your id for the customer. |

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

| Name       | In    | Type          | Required | Description               |
| ---------- | ----- | ------------- | -------- | ------------------------- |
| email      | query | string(email) | false    | Email for the user.       |
| customerId | query | string        | false    | Your id for the customer. |

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
