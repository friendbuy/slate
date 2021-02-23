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

| Name     | In   | Type         | Required | Description         |
| -------- | ---- | ------------ | -------- | ------------------- |
| body     | body | object       | false    | none                |
| » key    | body | string(uuid) | true     | Your api access key |
| » secret | body | string       | true     | Your api secret key |

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

| Name      | Type              | Required | Restrictions | Description                                             |
| --------- | ----------------- | -------- | ------------ | ------------------------------------------------------- |
| tokenType | string            | false    | none         | The type of the token generated.                        |
| token     | string(byte)      | false    | none         | The token generated. You will use this to authenticate. |
| expires   | string(date-time) | false    | none         | Expires 24 hours after registered.                      |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful authorization request.            | [authorizationResponse](#postauthorization-responses) |
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
  "campaignId": "ef9befc6-18f1-418c-8914-5ee8d09bb5aa",
  "customerId": "CUST1234",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {},
  "seed": "johnsmith",
  "channel": "purl",
  "ipAddress": "127.0.0.1",
  "userAgent": "Mozilla/5.0..."
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
  "campaignId": "ef9befc6-18f1-418c-8914-5ee8d09bb5aa",
  "customerId": "CUST1234",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {},
  "seed": "johnsmith",
  "channel": "purl",
  "ipAddress": "127.0.0.1",
  "userAgent": "Mozilla/5.0..."
}
```

<h3 id="postpersonalreferrallink-parameters">Parameters</h3>

| Name                        | In   | Type          | Required | Description                                                                                      |
| --------------------------- | ---- | ------------- | -------- | ------------------------------------------------------------------------------------------------ |
| body                        | body | object        | false    | none                                                                                             |
| » email                     | body | string(email) | true     | Email of the advocate.                                                                           |
| » campaignId                | body | string(uuid)  | true     | ID of the campaign to use to generate the link.                                                  |
| » customerId                | body | string        | false    | Your customer id for the advocate.                                                               |
| » firstName                 | body | string        | false    | First name of the advocate.                                                                      |
| » lastName                  | body | string        | false    | Last name of the advocate.                                                                       |
| » destinationUrlQueryParams | body | object        | false    | Custom parameters to be inserted into the url that users are directed to when clicking the link. |
| » seed                      | body | string        | false    | Specifies what the vanity url will be based on if provided.                                      |
| » channel                   | body | string        | false    | The share channel the link will be associated with in analytics. Recommended value is "purl".    |
| » ipAddress                 | body | string        | false    | IP Address of the advocate. Used for fraud checks.                                               |
| » userAgent                 | body | string        | false    | User Agent of the advocate. Used for fraud checks.                                               |

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
| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| link      | string           | true     | none         | The link created.       |
| createdOn | string(datetime) | true     | none         | When the link was created        |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                                                | Schema                                                              |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Personal referral link already exists - returning the pre-existing record. | [personalReferralLinkResponse](#postpersonalreferrallink-responses) |
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
  "userAgent": "Mozilla/5.0..."
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
  "userAgent": "Mozilla/5.0..."
}
```

<h3 id="postpurchaseevent-parameters">Parameters</h3>

| Name                      | In                   | Type                           | Required | Description                                                                                          |
| ------------------------- | -------------------- | ------------------------------ | -------- | ---------------------------------------------------------------------------------------------------- |
| body                      | body                 | object                         | false    | none                                                                                                 |
| » orderId                 | body                 | string                         | true     | Unique order id for the purchase.                                                                    |
| » email                   | body                 | string(email)                  | false    | Email of the customer making the purchase.                                                           |
| » customerId              | body                 | string                         | true     | Customer ID of the customer making the purchase.                                                     |
| » firstName               | body                 | string                         | false    | First name of the customer making the purchase.                                                      |
| » lastName                | body                 | string                         | false    | Last name of the customer making the purchase.                                                       |
| » amount                  | body                 | number                         | true     | The order total for the purchase.                                                                    |
| » currency                | body                 | string                         | true     | The currency used for the purchase (i.e. USD).                                                       |
| » isNewCustomer           | body                 | boolean                        | false    | Whether or not the customer making the purchase has made a previous purchase.                        |
| » couponCode              | body                 | string                         | false    | The coupon code used in the purchase, if any. Can be used to establish attribution with an advocate. |
| » attributionId           | body                 | string                         | false    | The attribution ID from the advocate's referral, if any.                                             |
| » additionalProperties    | body                 | object                         | false    | Any additional properties you wish to track with the purchase.                                       |
| »» **additionalProperty** | additionalProperties | string                         | false    | A key value pair indicating the property name and value.                                             |
| » ipAddress               | body                 | string                         | false    | IP address of the customer making the purchase.                                                      |
| » userAgent               | body                 | string                         | false    | User Agent of the customer making the purchase.                                                      |
| » products                | body                 | [product](#product-parameters) | false    | An array of purchased products.                                                                      |

<h3 id="product-parameters">Product Parameters</h3>
| Name     | Type    | Required | Restrictions | Description |
| -------- | ------- | -------- | ------------ | ----------- |
| sku      | string  | true     | none         | none        |
| name     | string  | false    | none         | none        |
| quantity | integer | false    | none         | none        |
| price    | integer | false    | none         | none        |

<h3 id="postpurchaseevent-responses">Responses</h3>
> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

| Name      | Type             | Required | Restrictions | Description                      |
| --------- | ---------------- | -------- | ------------ | -------------------------------- |
| eventId   | string(uuid)     | true     | none         | The Friendbuy id for this event. |
| createdOn | string(datetime) | true     | none         | When this event was created.     |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [purchaseEventResponse](#postpurchaseevent-responses) |
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
  "attributionId": "string",
  "couponCode": "string",
  "additionalProperties": {
    "property1": "string",
    "property2": "string"
  },
  "ipAddress": "string",
  "userAgent": "Mozilla/5.0...",
  "timezone": "America/Los_Angeles",
  "birthday": {
    "day": 1,
    "month": 10,
    "year": 1980,
  }
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

Generate sign-up event.

> Body parameter

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
  "userAgent": "Mozilla/5.0...",
  "timezone": "America/Los_Angeles",
  "birthday": {
    "day": 1,
    "month": 10,
    "year": 1980
  }
}
```

<h3 id="postsignupevent-parameters">Parameters</h3>

| Name                      | In                   | Type          | Required | Description                                                                                        |
| ------------------------- | -------------------- | ------------- | -------- | -------------------------------------------------------------------------------------------------- |
| body                      | body                 | object        | false    | none                                                                                               |
| » email                   | body                 | string(email) | true     | Email of the user signing up.                                                                      |
| » customerId              | body                 | string        | true     | Customer id of the user.                                                                           |
| » firstName               | body                 | string        | false    | First name of the user.                                                                            |
| » lastName                | body                 | string        | false    | Last name of the user.                                                                             |
| » attributionId           | body                 | string        | false    | The attribution ID from the advocate's referral, if any.                                           |
| » couponCode              | body                 | string        | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| » additionalProperties    | body                 | object        | false    | Any additional properties you wish to track with this signup.                                      |
| »» **additionalProperty** | additionalProperties | string        | false    | A key value pair representing the name of the property and the value.                              |
| » ipAddress               | body                 | string        | false    | The IP address of the user.                                                                        |
| » userAgent               | body                 | string        | false    | The User Agent of the user.                                                                        |
| » timezone                | body                 | string        | false    | Timezone of the customer. See [Timezones](#tocS_Timezone)                                          |
| » birthday                | body                 | object        | false    | Birthday of the customer                                                                           |
| »» day                    | birthday             | integer       | true     | Day the event should trigger. 1 - 31.                                                              |
| »» month                  | birthday             | integer       | true     | Month the event should trigger. 1 - 12.                                                            |
| »» year                   | birthday             | integer       | false    | Year the event will trigger (YYYY).                                                                |

> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postsignupevent-responses">Responses</h3>
| Name      | Type             | Required | Restrictions | Description |
| --------- | ---------------- | -------- | ------------ | ----------- |
| eventId   | string(uuid)     | true     | none         | The Friendbuy id for this event.        |
| createdOn | string(datetime) | true     | none         | When this event was created.        |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                            |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [signUpEventResponse](#postsignupevent-responses) |
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
  "customerId": "string",
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
  "userAgent": "Mozilla/5.0..."
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
  "customerId": "string",
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
  "userAgent": "Mozilla/5.0..."
}
```

<h3 id="postcustomevent-parameters">Parameters</h3>

| Name                      | In                   | Type          | Required | Description                                                                                        |
| ------------------------- | -------------------- | ------------- | -------- | -------------------------------------------------------------------------------------------------- |
| body                      | body                 | object        | false    | none                                                                                               |
| » email                   | body                 | string(email) | true     | Email of the user performing the event.                                                            |
| » eventType               | body                 | string        | true     | The type of the event you are tracking (i.e. "newsletter signup", "video view", etc).              |
| » customerId              | body                 | string        | false    | Customer id of the user performing the event.                                                      |
| » isNewCustomer           | body                 | boolean       | false    | Whether or not the user is a new customer.                                                         |
| » firstName               | body                 | string        | false    | First name of the user.                                                                            |
| » lastName                | body                 | string        | false    | Last name of the user.                                                                             |
| » attributionId           | body                 | string        | false    | The attribution ID from the advocate's referral, if any.                                           |
| » couponCode              | body                 | string        | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| » additionalProperties    | body                 | object        | false    | Any additional properties you wish to track with the event.                                        |
| »» **additionalProperty** | additionalProperties | string        | false    | A key value pair representing the name and value of the additional property.                       |
| » ipAddress               | body                 | string        | false    | IP Address of the user.                                                                            |
| » userAgent               | body                 | string        | false    | User Agent of the user.                                                                            |

> Example responses

> 201 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postcustomevent-responses">Responses</h3>

| Name      | Type             | Required | Restrictions | Description                      |
| --------- | ---------------- | -------- | ------------ | -------------------------------- |
| eventId   | string(uuid)     | true     | none         | The Friendbuy id for this event. |
| createdOn | string(datetime) | true     | none         | When this event was created.     |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                            |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------- |
| 201    | [Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)               | Post event created                           | [customEventResponse](#postcustomevent-responses) |
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
  "userAgent": "Mozilla/5.0...",
  "timezone": "America/Los_Angeles",
  "birthday": {
    "day": 1,
    "month": 10,
    "year": 1980,
  }
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
  "userAgent": "Mozilla/5.0...",
  "timezone": "America/Los_Angeles",
  "birthday": {
    "day": 1,
    "month": 10,
    "year": 1980
  }
}
```

<h3 id="postcustomer-parameters">Parameters</h3>

| Name                      | In                   | Type          | Required | Description                                                           |
| ------------------------- | -------------------- | ------------- | -------- | --------------------------------------------------------------------- |
| body                      | body                 | object        | false    | none                                                                  |
| » email                   | body                 | string(email) | true     | Email of the customer.                                                |
| » customerId              | body                 | string        | true     | Your id for the customer.                                             |
| » isNewCustomer           | body                 | boolean       | false    | Whether or not the customer has purchsed before.                      |
| » firstName               | body                 | string        | false    | First name of the customer.                                           |
| » lastName                | body                 | string        | false    | Last name of the customer.                                            |
| » age                     | body                 | integer       | false    | Age of the customer.                                                  |
| » gender                  | body                 | string        | false    | Gender of the customer.                                               |
| » zipCode                 | body                 | string        | false    | Zip code of the customer.                                             |
| » state                   | body                 | string        | false    | State the customer lives in.                                          |
| » city                    | body                 | string        | false    | The customer's city.                                                  |
| » category                | body                 | string        | false    | The category the customer is in, if any.                              |
| » country                 | body                 | string        | false    | The customer's country.                                               |
| » language                | body                 | string        | false    | The customer's preferred language.                                    |
| » additionalProperties    | body                 | object        | false    | Any additional properties you wish to track with this customer.       |
| »» **additionalProperty** | additionalProperties | string        | false    | A key value pair representing the name of the property and its value. |
| » ipAddress               | body                 | string        | false    | IP address of the customer.                                           |
| » userAgent               | body                 | string        | false    | User Agent of the customer.                                           |
| » timezone                | body                 | string        | false    | Timezone of the customer. See [Timezones](#tocS_Timezone)             |
| » birthday                | body                 | object        | false    | Birthday of the customer                                              |
| »» day                    | birthday             | integer       | true     | Day the event should trigger. 1 - 31.                                 |
| »» month                  | birthday             | integer       | true     | Month the event should trigger. 1 - 12                                |
| »» year                   | birthday             | integer       | false    | Year the event will trigger (YYYY).                                   |

> Example responses

> 200 Response

```json
{
  "eventId": "string",
  "createdOn": "string"
}
```

<h3 id="postcustomer-responses">Responses</h3>

| Name      | Type             | Required | Restrictions | Description                                             |
| --------- | ---------------- | -------- | ------------ | ------------------------------------------------------- |
| eventId   | string           | true     | none         | The Friendbuy id for the event to process the customer. |
| createdOn | string(datetime) | true     | none         | When this customer was created.                         |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                      |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Customer already exists - updated            | [customerResponse](#postcustomer-responses) |
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
| shares        | [userDataGetResponse_shares](#tracked_shares_and_conversions_response)          | false    | none         | none        |
| conversions   | [userDataGetResponse_shares](#tracked_shares_and_conversions_response)          | false    | none         | none        |

<h3 id="#schemauserdatagetresponse_trackedevents">Tracked Event Response</h3>
| Name | Type   | Required | Restrictions | Description |
| ---- | ------ | -------- | ------------ | ----------- |
| type | string | false    | none         | The type of the event.        |
| url  | string | false    | none         | The url of the page the event was tracked on.        |

<h3 id="#tracked_shares_and_conversions_response">Tracked Share/Conversion Response</h3>

The same schema applies to both tracked shares and tracked conversions.

| Name      | Type    | Required | Restrictions | Description                                    |
| --------- | ------- | -------- | ------------ | ---------------------------------------------- |
| email     | integer | false    | none         | The number of email shares or conversions.     |
| facebook  | integer | false    | none         | The number of facebook shares or conversions.  |
| messenger | integer | false    | none         | The number of messenger shares or conversions. |
| sms       | integer | false    | none         | The number of sms shares or conversions.       |
| twitter   | integer | false    | none         | The number of twitter shares or conversions.   |
| purl      | integer | false    | none         | The number of purl shares or conversions.      |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                          |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful user data get request.            | [userDataGetResponse](#schemauserdatagetresponse_trackedevents) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                                           |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                           |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                           |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                           |

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

| Name  | Type         | Required | Restrictions | Description                                                                |
| ----- | ------------ | -------- | ------------ | -------------------------------------------------------------------------- |
| jobId | string(uuid) | false    | none         | The id of the task to delete the data. Used for troubleshooting if needed. |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                              |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful user data delete request.         | [userDataDeleteResponse](#deleteuserdata-responses) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                | [Error](#schemaerror)                               |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                               |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                               |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                               |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## timeBasedRegister

<a id="opIdtimeBasedRegister"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/time-based-event/register \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://mapi.fbot.me/v1/time-based-event/register HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "customerId": "string",
  "date": {
    "day": 0,
    "month": 0,
    "year": 0,
    "timezone": "America/Adak"
  },
  "metadata": {},
  "configId": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://mapi.fbot.me/v1/time-based-event/register',
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

result = RestClient.post 'https://mapi.fbot.me/v1/time-based-event/register',
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

r = requests.post('https://mapi.fbot.me/v1/time-based-event/register', headers = headers)

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
    $response = $client->request('POST','https://mapi.fbot.me/v1/time-based-event/register', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/time-based-event/register");
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
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/time-based-event/register", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /v1/time-based-event/register`

_Scheduling an event to be scheduled some time in the future._

Regisdter time based event.

> Body parameter

```json
{
  "customerId": "string",
  "date": {
    "day": 0,
    "month": 0,
    "year": 0,
    "timezone": "America/Adak"
  },
  "metadata": {},
  "configId": "string"
}
```

<h3 id="timebasedregister-parameters">Parameters</h3>

| Name          | In   | Type    | Required    | Description                                                                      |
| ------------- | ---- | ------- | ----------- | -------------------------------------------------------------------------------- |
| body          | body | any     | true        | none                                                                             |
| » customerId  | body | string  | true        | Customer id of the user.                                                         |
| » date        | body | object  | true        | The date the event is scheduled.                                                 |
| »» day        | date | integer | true        | Day the event should trigger. 1 - 31.                                            |
| »» month      | date | integer | true        | Month the event should trigger. 1 - 12                                           |
| »» year       | date | integer | false       | Year the event will trigger (YYYY).                                              |
| » metadata    | body | object  | false       | Any metadata to be included.                                                     |
| » configId \* | body | string  | conditional | Id of the configuration. Required if kind is not provided.                       |
| » kind \*     | body | string  | conditional | One of "birthday", "anniversary", "other". Required if configId is not provided. |

> Example responses

> 200 Response

```json
{
  "event": {
    "id": "string",
    "configId": "string",
    "merchantId": "string",
    "orphaned": true,
    "createdOn": "string",
    "registryId": "string",
    "customerId": "string",
    "originalDate": {
      "day": 0,
      "month": 0,
      "year": 0,
      "timezone": "America/Adak"
    },
    "expiresDate": {
      "day": 0,
      "month": 0,
      "year": 0,
      "timezone": "America/Adak"
    },
    "expireOn": 0,
    "metadata": {},
    "attempt": 0
  }
}
```

<h3 id="timebasedregister-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                                     | Schema                                                        |
| ------ | -------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Event is either created or updated (depends on related config). | [TimeBasedRegisterResponse](#schematimebasedregisterresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                                   | [Error](#schemaerror)                                         |
| 409    | [Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)              | Conflict                                                        | [Error](#schemaerror)                                         |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                                            | [Error](#schemaerror)                                         |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                                               | [Error](#schemaerror)                                         |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure)                    | [Error](#schemaerror)                                         |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getWidgetViews

<a id="opIdgetWidgetViews"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/widget-views',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/widget-views', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/widget-views', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/widget-views", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/widget-views`

_Endpoint to retrieve widget views_

Get widget views.

<h3 id="getWidgetViews-parameters">Parameters</h3>

| Name       | In    | Type              | Required | Description                                                                                                         |
| ---------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate   | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate     | query | string(date-time) | true     | End of the search period.                                                                                           |
| zone       | query | string            | true     | Timezone to use for the search period (e.g. America/Los_Angeles).                                                   |
| campaignId | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| widgetName | query | string            | false    | Widget Name to filter on.                                                                                           |
| widgetType | query | string            | false    | Widget type to filter on (advocateShare or friendIncentive).                                                        |
| pageToken  | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize   | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "customerId": "ad39255f-b7e6-4c8b-baa8-5c7aa0c3e241",
      "email": "user@example.com",
      "widgetName": "Post Purchase Overlay",
      "campaignId": "st27d77a60-c446-4629-81a9-cc2eaa08738ering",
      "campaignName": "Evergreen Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.79 Safari/537.36",
      "ipAddress": "192.168.0.1"
    }
  ]
}
```

<h3 id="getWidgetViews-responses">Responses</h3>

| Name         | Type              | Required | Restrictions | Description                                                  |
| ------------ | ----------------- | -------- | ------------ | ------------------------------------------------------------ |
| customerId   | string            | false    | none         | Customer Id of the user who viewed the widget, if available. |
| email        | string(email)     | false    | none         | Email of the user who viewed the widget, if available.       |
| widgetName   | string            | false    | none         | Name of the viewed widget.                                   |
| campaignId   | string(uuid)      | false    | none         | Campaign Id associated with the viewed widget.               |
| campaignName | string            | false    | none         | Name of the campaign associated with the viewed widget.      |
| createdOn    | string(date-time) | false    | none         | Date and time the widget was viewed.                         |
| userAgent    | string            | false    | none         | User Agent of the user who viewed the widget.                |
| ipAddress    | string(ipv4)      | false    | none         | IP Address of the user who viewed the widget.                |

<h3 id="getWidgetViews-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                  |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getWidgetViewsResponse](#schemagetWidgetViewsresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                   |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                   |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                   |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getShares

<a id="opIdgetShares"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/shares',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/shares', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/shares', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/shares", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/shares`

_Endpoint to retrieve shares_

Get shares.

<h3 id="getShares-parameters">Parameters</h3>

| Name               | In    | Type              | Required | Description |
| ------------------ | ----- | ----------------- | -------- | ----------- |
| fromDate           | query | string(date-time) | true     | none        |
| toDate             | query | string(date-time) | true     | none        |
| zone               | query | string            | true     | none        |
| campaignId         | query | string(uuid)      | false    | none        |
| advocateEmail      | query | string(email)     | false    | none        |
| advocateCustomerId | query | string            | false    | none        |
| channel            | query | string            | false    | none        |
| pageToken          | query | string            | false    | none        |
| pageSize           | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "advocateCustomerId": "c9a58f97-7d2c-4cfd-a8e7-ed404038d2b2",
      "advocateEmail": "user@example.com",
      "advocateName": "Test Advocate",
      "channel": "email",
      "referralCode": "abc123",
      "campaignId": "ad39255f-b7e6-4c8b-baa8-5c7aa0c3e241",
      "campaignName": "Evergreen Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.79 Safari/537.36",
      "ipAddress": "192.168.0.1"
    }
  ]
}
```

<h3 id="getShares-responses">Responses</h3>

| Name               | Type              | Required | Restrictions | Description                                                               |
| ------------------ | ----------------- | -------- | ------------ | ------------------------------------------------------------------------- |
| advocateCustomerId | string            | false    | none         | Customer Id of the advocate who shared.                                   |
| advocateEmail      | string(email)     | false    | none         | Email of the advocate who shared.                                         |
| advocateName       | string            | false    | none         | Name of the advocate who shared.                                          |
| channel            | string            | false    | none         | The channel the user shared through (e.g. email, facebook, twitter, purl) |
| referralCode       | string            | false    | none         | The referral code of the share.                                           |
| campaignId         | string(uuid)      | false    | none         | The id of the campaign the share originated from.                         |
| campaignName       | string            | false    | none         | The name of the campaign the share originated from.                       |
| createdOn          | string(date-time) | false    | none         | The date the share was made.                                              |
| userAgent          | string            | false    | none         | The user agent of the advocate who shared.                                |
| ipAddress          | string(ipv4)      | false    | none         | The ip address of the advocate who shared.                                |

<h3 id="getShares-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                        |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getSharesResponse](#schemagetSharesresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                         |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                         |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                         |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getClicks

<a id="opIdgetClicks"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/clicks',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/clicks', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/clicks', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/clicks", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/clicks`

_Endpoint to retrieve valid clicks_

Get valid clicks.

<h3 id="getClicks-parameters">Parameters</h3>

| Name       | In    | Type              | Required | Description |
| ---------- | ----- | ----------------- | -------- | ----------- |
| fromDate   | query | string(date-time) | true     | none        |
| toDate     | query | string(date-time) | true     | none        |
| zone       | query | string            | true     | none        |
| campaignId | query | string(uuid)      | false    | none        |
| channel    | query | string            | false    | none        |
| pageToken  | query | string            | false    | none        |
| pageSize   | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "advocateCustomerId": "string",
      "advocateEmail": "user@example.com",
      "advocateName": "string",
      "cid": "string",
      "channel": "string",
      "referralCode": "string",
      "campaignId": "string",
      "campaignName": "string",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "string",
      "ipAddress": "192.168.0.1",
      "destinationUrl": "string"
    }
  ]
}
```

<h3 id="getClicks-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                        |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getClicksResponse](#schemagetClicksresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                         |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                         |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                         |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getSignups

<a id="opIdgetSignups"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/signups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/signups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/signups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/signups',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/signups', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/signups', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/signups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/signups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/signups`

_Endpoint to retrieve referral signups_

Get referral signups.

<h3 id="getSignups-parameters">Parameters</h3>

| Name       | In    | Type              | Required | Description |
| ---------- | ----- | ----------------- | -------- | ----------- |
| fromDate   | query | string(date-time) | true     | none        |
| toDate     | query | string(date-time) | true     | none        |
| zone       | query | string            | true     | none        |
| campaignId | query | string(uuid)      | false    | none        |
| customerId | query | string            | false    | none        |
| email      | query | string(email)     | false    | none        |
| pageToken  | query | string            | false    | none        |
| pageSize   | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "customerId": "string",
      "email": "user@example.com",
      "name": "string",
      "campaignId": "string",
      "campaignName": "string",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "string",
      "ipAddress": "192.168.0.1",
      "advocateName": "string",
      "advocateEmail": "user@example.com",
      "advocateCustomerId": "string",
      "cid": "string",
      "newCustomer": true,
      "referralCode": "string"
    }
  ]
}
```

<h3 id="getSignups-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                          |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getSignupsResponse](#schemagetSignupsresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                           |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                           |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                           |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getPurchases

<a id="opIdgetPurchases"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/purchases',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/purchases', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/purchases', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/purchases", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/purchases`

_Endpoint to retrieve referral purchases_

Get referral purchases.

<h3 id="getPurchases-parameters">Parameters</h3>

| Name       | In    | Type              | Required | Description |
| ---------- | ----- | ----------------- | -------- | ----------- |
| fromDate   | query | string(date-time) | true     | none        |
| toDate     | query | string(date-time) | true     | none        |
| zone       | query | string            | true     | none        |
| campaignId | query | string(uuid)      | false    | none        |
| customerId | query | string            | false    | none        |
| email      | query | string(email)     | false    | none        |
| pageToken  | query | string            | false    | none        |
| pageSize   | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "customerId": "string",
      "email": "user@example.com",
      "name": "string",
      "campaignId": "string",
      "campaignName": "string",
      "createdOn": "2021-02-23T01:20:14Z",
      "ipAddress": "192.168.0.1",
      "advocateName": "string",
      "advocateEmail": "user@example.com",
      "advocateCustomerId": "string",
      "cid": "string",
      "newCustomer": true,
      "referralCode": "string",
      "totalAmount": 0,
      "couponCode": "string",
      "nextPageToken": "string",
      "products": [
        {
          "sku": "string",
          "name": "string",
          "quantity": 0,
          "price": 0
        }
      ]
    }
  ]
}
```

<h3 id="getPurchases-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                              |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getPurchasesResponse](#schemagetPurchasesresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                               |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                               |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                               |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getDistributedAdvocateRewards

<a id="opIdgetDistributedAdvocateRewards"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/distributed-advocate-rewards`

_Endpoint to retrieve distributed advocate rewards_

Get distributed advocate rewards.

<h3 id="getDistributedAdvocateRewards-parameters">Parameters</h3>

| Name               | In    | Type              | Required | Description |
| ------------------ | ----- | ----------------- | -------- | ----------- |
| fromDate           | query | string(date-time) | true     | none        |
| toDate             | query | string(date-time) | true     | none        |
| zone               | query | string            | true     | none        |
| campaignId         | query | string(uuid)      | false    | none        |
| advocateCustomerId | query | string            | false    | none        |
| advocateEmail      | query | string(email)     | false    | none        |
| pageToken          | query | string            | false    | none        |
| pageSize           | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "createdOn": "string",
      "rewardType": "string",
      "rewardAmount": 0,
      "couponCode": "string",
      "trigger": "string",
      "advocateEmail": "string",
      "advocateName": "string",
      "advocateCustomerId": "string",
      "referralCode": "string",
      "channel": "string",
      "friendEmail": "string",
      "friendName": "string",
      "friendCustomerId": "string",
      "campaignId": "string",
      "campaignName": "string",
      "cid": "string"
    }
  ]
}
```

<h3 id="getDistributedAdvocateRewards-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [distributedRewardsGetResponse](#schemadistributedrewardsgetresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                                 |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                                 |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                                 |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getDistributedFriendIncentives

<a id="opIdgetDistributedFriendIncentives"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/distributed-friend-incentives',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/distributed-friend-incentives', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/distributed-friend-incentives', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/distributed-friend-incentives", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/distributed-friend-incentives`

_Endpoint to retrieve distributed friend incentives_

Get distributed friend incentives.

<h3 id="getDistributedFriendIncentives-parameters">Parameters</h3>

| Name             | In    | Type              | Required | Description |
| ---------------- | ----- | ----------------- | -------- | ----------- |
| fromDate         | query | string(date-time) | true     | none        |
| toDate           | query | string(date-time) | true     | none        |
| zone             | query | string            | true     | none        |
| campaignId       | query | string(uuid)      | false    | none        |
| friendCustomerId | query | string            | false    | none        |
| friendEmail      | query | string(email)     | false    | none        |
| pageToken        | query | string            | false    | none        |
| pageSize         | query | string            | false    | none        |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "createdOn": "string",
      "rewardType": "string",
      "rewardAmount": 0,
      "couponCode": "string",
      "trigger": "string",
      "advocateEmail": "string",
      "advocateName": "string",
      "advocateCustomerId": "string",
      "referralCode": "string",
      "channel": "string",
      "friendEmail": "string",
      "friendName": "string",
      "friendCustomerId": "string",
      "campaignId": "string",
      "campaignName": "string",
      "cid": "string"
    }
  ]
}
```

<h3 id="getDistributedFriendIncentives-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                                |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [distributedRewardsGetResponse](#schemadistributedrewardsgetresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                                 |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                                 |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                                 |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getEmailCaptures

<a id="opIdgetEmailCaptures"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles",
  {
    method: "GET",

    headers: headers,
  }
)
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/email-captures',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)',
'zone' => 'string'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/email-captures', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z',  'zone': 'America/Los_Angeles'
}, headers = headers)

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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/email-captures', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/email-captures", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/email-captures`

_Endpoint to retrieve email captures_

Get email captures.

<h3 id="getEmailCaptures-parameters">Parameters</h3>

| Name             | In    | Type              | Required | Description |
| ---------------- | ----- | ----------------- | -------- | ----------- |
| fromDate         | query | string(date-time) | true     | none        |
| toDate           | query | string(date-time) | true     | none        |
| zone             | query | string            | true     | none        |
| campaignId       | query | string(uuid)      | false    | none        |
| emailCaptureType | query | string            | false    | none        |
| email            | query | string(email)     | false    | none        |
| pageToken        | query | string            | false    | none        |
| pageSize         | query | string            | false    | none        |

#### Enumerated Values

| Parameter        | Value    |
| ---------------- | -------- |
| emailCaptureType | advocate |
| emailCaptureType | friend   |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "string",
  "totalResults": 0,
  "results": [
    {
      "name": "string",
      "email": "user@example.com",
      "widgetName": "string",
      "campaignId": "string",
      "campaignName": "string",
      "createdOn": "2021-02-23T01:20:14Z",
      "ipAddress": "192.168.0.1",
      "emailCaptureType": "advocate",
      "newsletterOptIn": true
    }
  ]
}
```

<h3 id="getEmailCaptures-responses">Responses</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                      |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getEmailCapturesResponse](#schemagetEmailCapturesresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                       |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                       |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                       |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## Errors

<a id="schemaerror"></a>

| Name      | Type   | Required | Restrictions | Description                                                     |
| --------- | ------ | -------- | ------------ | --------------------------------------------------------------- |
| error     | string | false    | none         | The error name.                                                 |
| message   | string | false    | none         | The error details.                                              |
| code      | number | false    | none         | The status code of the error.                                   |
| reference | string | false    | none         | A reference string that can be sent to friendbuy for debugging. |

<h2 id="tocS_Timezone">Timezones</h2>
<!-- backwards compatibility -->
<a id="schematimezone"></a>
<a id="schema_Timezone"></a>
<a id="tocStimezone"></a>
<a id="tocstimezone"></a>

```json
"America/Adak"
```

### Properties

| Name        | Type   | Required | Restrictions | Description |
| ----------- | ------ | -------- | ------------ | ----------- |
| _anonymous_ | string | false    | none         | none        |

#### Enumerated Values

| Property    | Value                  |
| ----------- | ---------------------- |
| _anonymous_ | America/Adak           |
| _anonymous_ | America/Anchorage      |
| _anonymous_ | America/Anguilla       |
| _anonymous_ | America/Antigua        |
| _anonymous_ | America/Araguaina      |
| _anonymous_ | America/Argentina      |
| _anonymous_ | America/Aruba          |
| _anonymous_ | America/Asuncion       |
| _anonymous_ | America/Atikokan       |
| _anonymous_ | America/Atka           |
| _anonymous_ | America/Bahia          |
| _anonymous_ | America/Bahia_Banderas |
| _anonymous_ | America/Barbados       |
| _anonymous_ | America/Belem          |
| _anonymous_ | America/Belize         |
| _anonymous_ | America/Blanc          |
| _anonymous_ | America/Boa_Vista      |
| _anonymous_ | America/Bogota         |
| _anonymous_ | America/Boise          |
| _anonymous_ | America/Buenos_Aires   |
| _anonymous_ | America/Cambridge_Bay  |
| _anonymous_ | America/Campo_Grande   |
| _anonymous_ | America/Cancun         |
| _anonymous_ | America/Caracas        |
| _anonymous_ | America/Catamarca      |
| _anonymous_ | America/Cayenne        |
| _anonymous_ | America/Cayman         |
| _anonymous_ | America/Chicago        |
| _anonymous_ | America/Chihuahua      |
| _anonymous_ | America/Coral_Harbour  |
| _anonymous_ | America/Cordoba        |
| _anonymous_ | America/Costa_Rica     |
| _anonymous_ | America/Creston        |
| _anonymous_ | America/Cuiaba         |
| _anonymous_ | America/Curacao        |
| _anonymous_ | America/Danmarkshavn   |
| _anonymous_ | America/Dawson         |
| _anonymous_ | America/Dawson_Creek   |
| _anonymous_ | America/Denver         |
| _anonymous_ | America/Detroit        |
| _anonymous_ | America/Dominica       |
| _anonymous_ | America/Edmonton       |
| _anonymous_ | America/Eirunepe       |
| _anonymous_ | America/El_Salvador    |
| _anonymous_ | America/Ensenada       |
| _anonymous_ | America/Fortaleza      |
| _anonymous_ | America/Fort_Nelson    |
| _anonymous_ | America/Fort_Wayne     |
| _anonymous_ | America/Glace_Bay      |
| _anonymous_ | America/Godthab        |
| _anonymous_ | America/Goose_Bay      |
| _anonymous_ | America/Grand_Turk     |
| _anonymous_ | America/Grenada        |
| _anonymous_ | America/Guadeloupe     |
| _anonymous_ | America/Guatemala      |
| _anonymous_ | America/Guayaquil      |
| _anonymous_ | America/Guyana         |
| _anonymous_ | America/Halifax        |
| _anonymous_ | America/Havana         |
| _anonymous_ | America/Hermosillo     |
| _anonymous_ | America/Indiana        |
| _anonymous_ | America/Indianapolis   |
| _anonymous_ | America/Inuvik         |
| _anonymous_ | America/Iqaluit        |
| _anonymous_ | America/Jamaica        |
| _anonymous_ | America/Jujuy          |
| _anonymous_ | America/Juneau         |
| _anonymous_ | America/Kentucky       |
| _anonymous_ | America/Knox_IN        |
| _anonymous_ | America/Kralendijk     |
| _anonymous_ | America/La_Paz         |
| _anonymous_ | America/Lima           |
| _anonymous_ | America/Los_Angeles    |
| _anonymous_ | America/Louisville     |
| _anonymous_ | America/Lower_Princes  |
| _anonymous_ | America/Maceio         |
| _anonymous_ | America/Managua        |
| _anonymous_ | America/Manaus         |
| _anonymous_ | America/Marigot        |
| _anonymous_ | America/Martinique     |
| _anonymous_ | America/Matamoros      |
| _anonymous_ | America/Mazatlan       |
| _anonymous_ | America/Mendoza        |
| _anonymous_ | America/Menominee      |
| _anonymous_ | America/Merida         |
| _anonymous_ | America/Metlakatla     |
| _anonymous_ | America/Mexico_City    |
| _anonymous_ | America/Miquelon       |
| _anonymous_ | America/Moncton        |
| _anonymous_ | America/Monterrey      |
| _anonymous_ | America/Montevideo     |
| _anonymous_ | America/Montreal       |
| _anonymous_ | America/Montserrat     |
| _anonymous_ | America/Nassau         |
| _anonymous_ | America/New_York       |
| _anonymous_ | America/Nipigon        |
| _anonymous_ | America/Nome           |
| _anonymous_ | America/Noronha        |
| _anonymous_ | America/North_Dakota   |
| _anonymous_ | America/Ojinaga        |
| _anonymous_ | America/Panama         |
| _anonymous_ | America/Pangnirtung    |
| _anonymous_ | America/Paramaribo     |
| _anonymous_ | America/Phoenix        |
| _anonymous_ | America/Port           |
| _anonymous_ | America/Porto_Acre     |
| _anonymous_ | America/Porto_Velho    |
| _anonymous_ | America/Port_of_Spain  |
| _anonymous_ | America/Puerto_Rico    |
| _anonymous_ | America/Punta_Arenas   |
| _anonymous_ | America/Rainy_River    |
| _anonymous_ | America/Rankin_Inlet   |
| _anonymous_ | America/Recife         |
| _anonymous_ | America/Regina         |
| _anonymous_ | America/Resolute       |
| _anonymous_ | America/Rio_Branco     |
| _anonymous_ | America/Rosario        |
| _anonymous_ | America/Santarem       |
| _anonymous_ | America/Santa_Isabel   |
| _anonymous_ | America/Santiago       |
| _anonymous_ | America/Santo_Domingo  |
| _anonymous_ | America/Sao_Paulo      |
| _anonymous_ | America/Scoresbysund   |
| _anonymous_ | America/Shiprock       |
| _anonymous_ | America/Sitka          |
| _anonymous_ | America/St_Barthelemy  |
| _anonymous_ | America/St_Johns       |
| _anonymous_ | America/St_Kitts       |
| _anonymous_ | America/St_Lucia       |
| _anonymous_ | America/St_Thomas      |
| _anonymous_ | America/St_Vincent     |
| _anonymous_ | America/Swift_Current  |
| _anonymous_ | America/Tegucigalpa    |
| _anonymous_ | America/Thule          |
| _anonymous_ | America/Thunder_Bay    |
| _anonymous_ | America/Tijuana        |
| _anonymous_ | America/Toronto        |
| _anonymous_ | America/Tortola        |
| _anonymous_ | America/Vancouver      |
| _anonymous_ | America/Virgin         |
| _anonymous_ | America/Whitehorse     |
| _anonymous_ | America/Winnipeg       |
| _anonymous_ | America/Yakutat        |
| _anonymous_ | America/Yellowknife    |
