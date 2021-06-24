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
| key      | body | string(uuid) | true     | Your api access key |
| secret   | body | string       | true     | Your api secret key |

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
| tokenType | string            | false    | none         | The type of the token generated (Bearer).               |
| token     | string(byte)      | false    | none         | The token generated. You will use this to authenticate. |
| expires   | string(date-time) | false    | none         | Expires 20 minutes after being registered.                    |

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
| email                       | body | string(email) | true     | Email of the advocate.                                                                           |
| campaignId                  | body | string(uuid)  | true     | ID of the campaign to use to generate the link.                                                  |
| customerId                  | body | string        | false    | Your customer id for the advocate.                                                               |
| firstName                   | body | string        | false    | First name of the advocate.                                                                      |
| lastName                    | body | string        | false    | Last name of the advocate.                                                                       |
| destinationUrlQueryParams   | body | object        | false    | Custom parameters to be inserted into the url that users are directed to when clicking the link. |
| seed                        | body | string        | false    | Specifies what the vanity url will be based on if provided.                                      |
| channel                     | body | string        | false    | The share channel the link will be associated with in analytics. Recommended value is "purl".    |
| ipAddress                   | body | string        | false    | IP Address of the advocate. Used for fraud checks.                                               |
| userAgent                   | body | string        | false    | User Agent of the advocate. Used for fraud checks.                                               |

#### Enumerated Values

| Parameter | Value     |
| --------- | --------- |
| channel   | email     |
| channel   | facebook  |
| channel   | generic   |
| channel   | instagram |
| channel   | messenger |
| channel   | sms       |
| channel   | snap      |
| channel   | twitter   |
| channel   | purl      |

> Example responses

> 200 Response

```json
{
  "link": "string",
  "referralCode": "string",
  "createdOn": "string"
}
```

<h3 id="postpersonalreferrallink-responses">Responses</h3>
| Name         | Type             | Required | Restrictions | Description |
| ------------ | ---------------- | -------- | ------------ | ----------- |
| link         | string           | true     | none         | The referral link that was created. |
| referralCode | string           | true     | none         | Referral code associated with new referral link. |
| createdOn    | string(datetime) | true     | none         | When the link was created        |

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

## postPersonalReferralLinkBatch

<a id="opIdpostPersonalReferralLinkBatch"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://mapi.fbot.me/v1/personal-referral-link-batch \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'
```

```http
POST https://mapi.fbot.me/v1/personal-referral-link-batch HTTP/1.1
Host: mapi.fbot.me
Content-Type: application/json
Accept: application/json
```

```javascript
const inputBody = '{
  "requests": [
    {
      "email": "test@example.com",
      "campaignId": "string",
      "customerId": "string",
      "firstName": "John",
      "lastName": "Smith",
      "destinationUrlQueryParams": {},
      "seed": "string",
      "prefix": "string",
      "channel": "purl",
      "short": false,
      "ipAddress": "string",
      "userAgent": "api",
      "widgetId": "string",
      "eventUrl": "string",
      "eventPage": "string"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};
fetch('https://mapi.fbot.me/v1/personal-referral-link-batch',
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
result = RestClient.post 'https://mapi.fbot.me/v1/personal-referral-link-batch',
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
r = requests.post('https://mapi.fbot.me/v1/personal-referral-link-batch', headers = headers)
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
    $response = $client->request('POST','https://mapi.fbot.me/v1/personal-referral-link-batch', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/personal-referral-link-batch");
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
    req, err := http.NewRequest("POST", "https://mapi.fbot.me/v1/personal-referral-link-batch", data)
    req.Header = headers
    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}
```

`POST /v1/personal-referral-link-batch`

_Create or retrieve a personal URL for a given customer or email address and campaign. The URL provided uses input for seed and prefix from the campaign however those attributes can be overridden by the corresponding attributes within the request body._

Generate event

> Body parameter

```json
{
  "requests": [
    {
      "email": "test@example.com",
      "campaignId": "string",
      "customerId": "string",
      "firstName": "John",
      "lastName": "Smith",
      "destinationUrlQueryParams": {},
      "seed": "string",
      "prefix": "string",
      "channel": "purl",
      "short": false,
      "ipAddress": "string",
      "userAgent": "api",
      "widgetId": "string",
      "eventUrl": "string",
      "eventPage": "string"
    }
  ]
}
```

<h3 id="postpersonalreferrallinkbatch-parameters">Parameters</h3>

| Name                         | In       | Type          | Required | Description                                                                                      |
| ---------------------------- | -------- | ------------- | -------- | ------------------------------------------------------------------------------------------------ |
| requests                     | body     | array         | true     | Array of PURL requests.                                                                          |
| email                        | requests | string(email) | true     | Email of the advocate.                                                                           |
| campaignId                   | requests | string(uuid)  | true     | ID of the campaign to use to generate the link.                                                  |
| customerId                   | requests | string        | false    | Your customer id for the advocate.                                                               |
| firstName                    | requests | string        | false    | First name of the advocate.                                                                      |
| lastName                     | requests | string        | false    | Last name of the advocate.                                                                       |
| destinationUrlQueryParams    | requests | object        | false    | Custom parameters to be inserted into the url that users are directed to when clicking the link. |
| seed                         | requests | string        | false    | Specifies what the vanity url will be based on if provided.                                      |
| channel                      | requests | string        | false    | The share channel the link will be associated with in analytics. Recommended value is "purl".    |
| ipAddress                    | requests | string        | false    | IP Address of the advocate. Used for fraud checks.                                               |
| userAgent                    | requests | string        | false    | User Agent of the advocate. Used for fraud checks.                                               |

#### Enumerated Values

| Parameter | Value     |
| --------- | --------- |
| channel   | email     |
| channel   | facebook  |
| channel   | generic   |
| channel   | instagram |
| channel   | messenger |
| channel   | sms       |
| channel   | snap      |
| channel   | twitter   |
| channel   | purl      |

> Example responses

> 200 Response

```json
{
  "purls": [
    {
      "link": "string",
      "referralCode": "string",
      "createdOn": "string",
      "email": "user@example.com",
      "campaignId": "string",
      "customerId": "string"
    }
  ]
}
```

<h3 id="postpersonalreferrallinkbatch-responses">Responses</h3>

| Name         | Type             | Required | Restrictions | Description                                                |
| ------------ | ---------------- | -------- | ------------ | ---------------------------------------------------------- |
| link         | string           | true     | none         | The personal referral link that was created.               |
| referralCode | string           | true     | none         | Referral code associated with new referral link.           |
| createdOn    | string(datetime) | true     | none         | Timestamp for when the link was created.                   |
| email        | string(email)    | true     | none         | Email for the personal referral link in question.          |
| campaignId   | string(uuid)     | true     | none         | Campaign ID the personal referral link is associated with. |
| customerId   | string           | false    | none         | Customer ID the personal referral link is associated with. |

<h3>Response Codes</h3>

| Status | Meaning                                                                    | Description                                                                             | Schema                                                                        |
| ------ | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | Successful request, returning either pre-existing or generated personal referral links. | [personalReferralLinkBatchResponse](#schemapersonalreferrallinkbatchresponse) |
| 400    | [Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)           | Invalid input, object invalid                                                           | [Error](#schemaerror)                                                         |
| 404    | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)             | Not found - campaign does not exist or is inactive.                                     | [Error](#schemaerror)                                                         |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                                                                    | [Error](#schemaerror)                                                         |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                                                                       | [Error](#schemaerror)                                                         |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure)                                            | [Error](#schemaerror)                                                         |

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
  "referralCode": "string",
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
  "referralCode": "string",
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
| orderId                   | body                 | string                         | true     | Unique order id for the purchase.                                                                    |
| email                     | body                 | string(email)                  | false    | Email of the customer making the purchase.                                                           |
| customerId                | body                 | string                         | true     | Customer ID of the customer making the purchase.                                                     |
| firstName                 | body                 | string                         | false    | First name of the customer making the purchase.                                                      |
| lastName                  | body                 | string                         | false    | Last name of the customer making the purchase.                                                       |
| amount                    | body                 | number                         | true     | The order total for the purchase.                                                                    |
| currency                  | body                 | string                         | true     | The currency used for the purchase (i.e. USD).                                                       |
| isNewCustomer             | body                 | boolean                        | false    | Whether or not the customer making the purchase has made a previous purchase.                        |
| couponCode                | body                 | string                         | false    | The coupon code used in the purchase, if any. Can be used to establish attribution with an advocate. |
| attributionId             | body                 | string                         | false    | The attribution ID from the advocate's referral, if any.                                             |
| referralCode              | body                 | string                         | false    | A referral code to be used to establish attribution with an advocate.                                |
| additionalProperties      | body                 | object                         | false    | Any additional properties you wish to track with the purchase.                                       |
| **additionalProperty**    | additionalProperties | string                         | false    | A key value pair indicating the property name and value.                                             |
| ipAddress                 | body                 | string                         | false    | IP address of the customer making the purchase.                                                      |
| userAgent                 | body                 | string                         | false    | User Agent of the customer making the purchase.                                                      |
| products                  | body                 | [product](#product-parameters) | false    | An array of purchased products.                                                                      |

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
  "couponCode": "string",
  "attributionId": "string",
  "referralCode": "string",
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
| email                     | body                 | string(email) | true     | Email of the user signing up.                                                                      |
| customerId                | body                 | string        | true     | Customer id of the user.                                                                           |
| firstName                 | body                 | string        | false    | First name of the user.                                                                            |
| lastName                  | body                 | string        | false    | Last name of the user.                                                                             |
| couponCode                | body                 | string        | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| attributionId             | body                 | string        | false    | The attribution ID from the advocate's referral, if any.                                           |
| referralCode              | body                 | string        | false    | A referral code to be used to establish attribution with an advocate.                              |
| additionalProperties      | body                 | object        | false    | Any additional properties you wish to track with this signup.                                      |
| **additionalProperty**    | additionalProperties | string        | false    | A key value pair representing the name of the property and the value.                              |
| ipAddress                 | body                 | string        | false    | The IP address of the user.                                                                        |
| userAgent                 | body                 | string        | false    | The User Agent of the user.                                                                        |
| timezone                  | body                 | string        | false    | Timezone of the customer. See [Timezones](#tocS_Timezone)                                          |
| birthday                  | body                 | object        | false    | Birthday of the customer                                                                           |
| day                       | birthday             | integer       | true     | Day the event should trigger. 1 - 31.                                                              |
| month                     | birthday             | integer       | true     | Month the event should trigger. 1 - 12.                                                            |
| year                      | birthday             | integer       | false    | Year the event will trigger (YYYY).                                                                |

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
  "couponCode": "string",
  "attributionId": "string",
  "referralCode": "string",
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
| email                     | body                 | string(email) | true     | Email of the user performing the event.                                                            |
| eventType                 | body                 | string        | true     | The type of the event you are tracking (i.e. "newsletter signup", "video view", etc).              |
| customerId                | body                 | string        | false    | Customer id of the user performing the event.                                                      |
| isNewCustomer             | body                 | boolean       | false    | Whether or not the user is a new customer.                                                         |
| firstName                 | body                 | string        | false    | First name of the user.                                                                            |
| lastName                  | body                 | string        | false    | Last name of the user.                                                                             |
| couponCode                | body                 | string        | false    | The coupon code used in the signup, if any. Can be used to establish attribution with an advocate. |
| attributionId             | body                 | string        | false    | The attribution ID from the advocate's referral, if any.                                           |
| referralCode              | body                 | string        | false    | A referral code to be used to establish attribution with an advocate.                              |
| additionalProperties      | body                 | object        | false    | Any additional properties you wish to track with the event.                                        |
| **additionalProperty**    | additionalProperties | string        | false    | A key value pair representing the name and value of the additional property.                       |
| ipAddress                 | body                 | string        | false    | IP Address of the user.                                                                            |
| userAgent                 | body                 | string        | false    | User Agent of the user.                                                                            |

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
| email                     | body                 | string(email) | true     | Email of the customer.                                                |
| customerId                | body                 | string        | true     | Your id for the customer.                                             |
| isNewCustomer             | body                 | boolean       | false    | Whether or not the customer has purchsed before.                      |
| firstName                 | body                 | string        | false    | First name of the customer.                                           |
| lastName                  | body                 | string        | false    | Last name of the customer.                                            |
| age                       | body                 | integer       | false    | Age of the customer.                                                  |
| gender                    | body                 | string        | false    | Gender of the customer.                                               |
| zipCode                   | body                 | string        | false    | Zip code of the customer.                                             |
| state                     | body                 | string        | false    | State the customer lives in.                                          |
| city                      | body                 | string        | false    | The customer's city.                                                  |
| category                  | body                 | string        | false    | The category the customer is in, if any.                              |
| country                   | body                 | string        | false    | The customer's country.                                               |
| language                  | body                 | string        | false    | The customer's preferred language.                                    |
| additionalProperties      | body                 | object        | false    | Any additional properties you wish to track with this customer.       |
| **additionalProperty**    | additionalProperties | string        | false    | A key value pair representing the name of the property and its value. |
| ipAddress                 | body                 | string        | false    | IP address of the customer.                                           |
| userAgent                 | body                 | string        | false    | User Agent of the customer.                                           |
| timezone                  | body                 | string        | false    | Timezone of the customer. See [Timezones](#tocS_Timezone)             |
| birthday                  | body                 | object        | false    | Birthday of the customer                                              |
| day                       | birthday             | integer       | true     | Day the event should trigger. 1 - 31.                                 |
| month                     | birthday             | integer       | true     | Month the event should trigger. 1 - 12                                |
| year                      | birthday             | integer       | false    | Year the event will trigger (YYYY).                                   |

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

<h3 id="schemauserdatagetresponse_trackedevents">Tracked Event Response</h3>
| Name | Type   | Required | Restrictions | Description |
| ---- | ------ | -------- | ------------ | ----------- |
| type | string | false    | none         | The type of the event.        |
| url  | string | false    | none         | The url of the page the event was tracked on.        |

<h3 id="tracked_shares_and_conversions_response">Tracked Share/Conversion Response</h3>

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

Register time based event.

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
| customerId    | body | string  | true        | Customer id of the user.                                                         |
| date          | body | object  | true        | The date the event is scheduled.                                                 |
| day           | date | integer | true        | Day the event should trigger. 1 - 31.                                            |
| month         | date | integer | true        | Month the event should trigger. 1 - 12                                           |
| year          | date | integer | false       | Year the event will trigger (YYYY).                                              |
| metadata      | body | object  | false       | Any metadata to be included.                                                     |
| configId   \* | body | string  | conditional | Id of the configuration. Required if kind is not provided.                       |
| kind   \*     | body | string  | conditional | One of "birthday", "anniversary", "other". Required if configId is not provided. |

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
curl -X GET https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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
| campaignId | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| widgetName | query | string            | false    | Widget Name to filter on.                                                                                           |
| widgetType | query | string            | false    | Widget type to filter on (advocateShare or emailCapture).                                                           |
| pageToken  | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize   | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
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
      "ipAddress": "192.168.0.1",
      "widgetType": "advocateShare"
    }
  ]
}
```

<h3 id="getWidgetViews-responses">Responses</h3>

| Name          | Type                                                        | Required | Restrictions | Description                                                                                            |
| ------------- | ----------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                                      | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                                      | false    | none         | The total number of results.                                                                           |
| results       | [[widgetViewsGetResponse_results](#getWidgetViews-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getWidgetViews-results">Results</h3>

| Name         | Type              | Required | Restrictions | Description                                                          |
| ------------ | ----------------- | -------- | ------------ | -------------------------------------------------------------------- |
| customerId   | string            | false    | none         | Customer Id of the user who viewed the widget, if available.         |
| email        | string(email)     | false    | none         | Email of the user who viewed the widget, if available.               |
| widgetName   | string            | false    | none         | Name of the viewed widget.                                           |
| campaignId   | string(uuid)      | false    | none         | Campaign Id associated with the viewed widget.                       |
| campaignName | string            | false    | none         | Name of the campaign associated with the viewed widget.              |
| createdOn    | string(date-time) | false    | none         | Date and time the widget was viewed.                                 |
| userAgent    | string            | false    | none         | User Agent of the user who viewed the widget.                        |
| ipAddress    | string(ipv4)      | false    | none         | IP Address of the user who viewed the widget.                        |
| widgetType   | string            | false    | none         | Type of the widget viewed. Either "advocateShare" or "emailCapture". |

<h3 id="getWidgetViews-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                              |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getWidgetViewsResponse](#getWidgetViews-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                               |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                               |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                               |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getShares

<a id="opIdgetShares"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name               | In    | Type              | Required | Description                                                                                                         |
| ------------------ | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate           | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate             | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId         | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| advocateEmail      | query | string(email)     | false    | Advocate email to filter on.                                                                                        |
| advocateCustomerId | query | string            | false    | Advocate customer id to filter on.                                                                                  |
| channel            | query | string            | false    | Share channel to filter on.                                                                                         |
| pageToken          | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize           | query | string            | false    | Page size limit.                                                                                                    |

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

| Name          | Type                                              | Required | Restrictions | Description                                                                                            |
| ------------- | ------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                            | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                            | false    | none         | The total number of results.                                                                           |
| results       | [[sharesGetResponse_results](#getShares-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getShares-results">Results</h3>

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

| Status | Meaning                                                                    | Description                                  | Schema                                    |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getSharesResponse](#getShares-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                     |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                     |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                     |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getClicks

<a id="opIdgetClicks"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name       | In    | Type              | Required | Description                                                                                                         |
| ---------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate   | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate     | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| channel    | query | string            | false    | Filter for clicks that came from a specific channel.                                                                |
| pageToken  | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize   | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 0,
  "results": [
    {
      "advocateCustomerId": "e24b313b-c941-4baf-8762-34b3af8cddee",
      "advocateEmail": "user@example.com",
      "advocateName": "Test Advocate",
      "channel": "purl",
      "referralCode": "abc123",
      "campaignId": "1b9accd7-8ec5-4ff6-8d22-941fdc7338f4",
      "campaignName": "Holiday Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.79 Safari/537.36",
      "ipAddress": "192.168.0.1",
      "destinationUrl": "https://example.com"
    }
  ]
}
```

<h3 id="getClicks-responses">Responses</h3>

| Name          | Type                                              | Required | Restrictions | Description                                                                                            |
| ------------- | ------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                            | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                            | false    | none         | The total number of results.                                                                           |
| results       | [[clicksGetResponse_results](#getClicks-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getClicks-results">Results</h3>

| Name               | Type              | Required | Restrictions | Description                                                           |
| ------------------ | ----------------- | -------- | ------------ | --------------------------------------------------------------------- |
| advocateCustomerId | string            | false    | none         | Customer Id associated of the advocate who's link was clicked on.     |
| advocateEmail      | string(email)     | false    | none         | Email of the advocate who's link was clicked on.                      |
| advocateName       | string            | false    | none         | Name of the advocate who's link was clicked on.                       |
| channel            | string            | false    | none         | The channel of the link that was clicked (e.g. email, facebook, etc.) |
| referralCode       | string            | false    | none         | The referral code of the link that was clicked.                       |
| campaignId         | string(uuid)      | false    | none         | The campaign id of the link that was clicked.                         |
| campaignName       | string            | false    | none         | The campaign name of the link that was clicked.                       |
| createdOn          | string(date-time) | false    | none         | Timestamp of the click.                                               |
| userAgent          | string            | false    | none         | User agent of the user who clicked the link.                          |
| ipAddress          | string(ipv4)      | false    | none         | Ip address of the user who clicked the link.                          |
| destinationUrl     | string            | false    | none         | The url the user was directed to after clicking the link.             |

<h3 id="getClicks-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                    |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getClicksResponse](#getClicks-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                     |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                     |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                     |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getSignups

<a id="opIdgetSignups"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/account-sign-ups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/account-sign-ups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/account-sign-ups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/account-sign-ups',
  params: {
  'fromDate' => 'string(date-time)',
'toDate' => 'string(date-time)'

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/account-sign-ups', params={
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/account-sign-ups', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/account-sign-ups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/account-sign-ups", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/account-sign-ups`

_Endpoint to retrieve referral signups_

Get referral signups.

<h3 id="getSignups-parameters">Parameters</h3>

| Name       | In    | Type              | Required | Description                                                                                                         |
| ---------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate   | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate     | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| customerId | query | string            | false    | Customer id to filter on. This will filter based on the customer id of the user who signed up.                      |
| email      | query | string(email)     | false    | Email to filter on. This will filter based on the email of the user who signed up.                                  |
| pageToken  | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize   | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "customerId": "1b9accd7-8ec5-4ff6-8d22-941fdc7338f4",
      "email": "user@example.com",
      "name": "Test Friend",
      "campaignId": "03bbcf1f-c0d1-4868-af7c-3b65d44a410d",
      "campaignName": "Evergreen Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.79 Safari/537.36",
      "ipAddress": "192.168.0.1",
      "advocateName": "Test Advocate",
      "advocateEmail": "advocate@example.com",
      "advocateCustomerId": "61dbe3d5-8134-4a96-80e4-540f2df678b2",
      "newCustomer": true,
      "referralCode": "abc123"
    }
  ]
}
```

<h3 id="getSignups-responses">Responses</h3>

| Name          | Type                                                | Required | Restrictions | Description                                                                                            |
| ------------- | --------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                              | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                              | false    | none         | The total number of results.                                                                           |
| results       | [[signupsGetResponse_results](#getSignups-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getSignups-results">Results</h3>

| Name               | Type              | Required | Restrictions | Description                                                                                   |
| ------------------ | ----------------- | -------- | ------------ | --------------------------------------------------------------------------------------------- |
| customerId         | string            | false    | none         | The customer id of the user who signed up.                                                    |
| email              | string(email)     | false    | none         | Email of the user who signed up.                                                              |
| name               | string            | false    | none         | Name of the user who signed up.                                                               |
| campaignId         | string            | false    | none         | Id of the campaign that the user who signed up was referred through.                          |
| campaignName       | string            | false    | none         | Name of the campaign that the user who signed up was referred through.                        |
| createdOn          | string(date-time) | false    | none         | Timestamp of the signup.                                                                      |
| userAgent          | string            | false    | none         | User agent of the user who signed up.                                                         |
| ipAddress          | string(ipv4)      | false    | none         | IP address of the user who signed up.                                                         |
| advocateName       | string            | false    | none         | Name of the advocate who referred the user that signed up.                                    |
| advocateEmail      | string(email)     | false    | none         | Email of the advocate who referred the user that signed up.                                   |
| advocateCustomerId | string            | false    | none         | Customer id of the advocate who referred the user that signed up.                             |
| newCustomer        | boolean           | false    | none         | Indicates whether or not the user who signed up was a new customer.                           |
| referralCode       | string            | false    | none         | The referral code of the link the user who signed up clicked on.                              |
| channel            | string            | false    | none         | The channel of the link the user who signed up clicked on (e.g. email, purl, facebook, etc.). |

<h3 id="getSignups-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                      |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getSignupsResponse](#getSignups-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                       |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                       |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                       |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getPurchases

<a id="opIdgetPurchases"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name       | In    | Type              | Required | Description                                                                                                         |
| ---------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate   | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate     | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| customerId | query | string            | false    | Customer id to filter on. This will filter based on the customer id of the user who signed up.                      |
| email      | query | string(email)     | false    | Email to filter on. This will filter based on the email of the user who signed up.                                  |
| pageToken  | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize   | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "customerId": "fbdb5742-6fe4-40cb-95da-df8b02708627",
      "email": "user@example.com",
      "name": "Test Customer",
      "campaignId": "abc52d7f-828d-44e4-8b0d-79df62fdae9c",
      "campaignName": "Evergreen Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "ipAddress": "192.168.0.1",
      "advocateName": "Test Advocate",
      "advocateEmail": "advocate@example.com",
      "advocateCustomerId": "da6c99b7-4040-4677-a152-ef7bebc13b99",
      "newCustomer": true,
      "referralCode": "abc123",
      "amount": 50.0,
      "couponCode": "test-coupon-1",
      "products": [
        {
          "sku": "test-product-1",
          "name": "Test Product",
          "quantity": 2,
          "price": 25.0
        }
      ]
    }
  ]
}
```

<h3 id="getPurchases-responses">Responses</h3>

| Name          | Type                                                    | Required | Restrictions | Description                                                                                            |
| ------------- | ------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                                  | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                                  | false    | none         | The total number of results.                                                                           |
| results       | [[purchasesGetResponse_results](#getPurchases-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getPurchases-results">Results</h3>

| Name               | Type                                        | Required | Restrictions | Description                                                                |
| ------------------ | ------------------------------------------- | -------- | ------------ | -------------------------------------------------------------------------- |
| customerId         | string                                      | false    | none         | Customer id of the user who made the purchase.                             |
| email              | string(email)                               | false    | none         | Email of the user who made the purchase.                                   |
| name               | string                                      | false    | none         | Name of the user who made the purchase.                                    |
| campaignId         | string                                      | false    | none         | Id of the campaign the user who made the purchase was referred from.       |
| campaignName       | string                                      | false    | none         | Name of the campaign the user who made the purchase was referred from.     |
| createdOn          | string(date-time)                           | false    | none         | Timestamp of the purchase.                                                 |
| ipAddress          | string(ipv4)                                | false    | none         | IP address of the user who made the purchase.                              |
| advocateName       | string                                      | false    | none         | Name of the advocate who referred the user who made a purchase.            |
| advocateEmail      | string(email)                               | false    | none         | Email of the advocate who referred the user who made a purchase.           |
| advocateCustomerId | string                                      | false    | none         | Customer id of the advocate who referred the user who made a purchase.     |
| newCustomer        | boolean                                     | false    | none         | Indicates whether or not the user who made the purchase is a new customer. |
| referralCode       | string                                      | false    | none         | The referral code of the link the user who made the purchase clicked on.   |
| amount             | number                                      | false    | none         | Total amount of the purchase.                                              |
| couponCode         | string                                      | false    | none         | Any coupon code used on the purchase.                                      |
| products           | [[product](#getPurchases-product-response)] | false    | none         | Any products contained in the purchase.                                    |

<h3 id="getPurchases-product-response">Product Response</h3>

| Name     | Type    | Required | Restrictions | Description                   |
| -------- | ------- | -------- | ------------ | ----------------------------- |
| sku      | string  | true     | none         | SKU of the product.           |
| name     | string  | false    | none         | Name of the product.          |
| quantity | integer | false    | none         | Number of products purchased. |
| price    | integer | false    | none         | Price of the product.         |

<h3 id="getPurchases-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                          |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ----------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getPurchasesResponse](#getPurchases-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                           |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                           |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                           |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getDistributedAdvocateRewards

<a id="opIdgetDistributedAdvocateRewards"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name               | In    | Type              | Required | Description                                                                                                         |
| ------------------ | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate           | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate             | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId         | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| advocateCustomerId | query | string            | false    | Customer id to filter on. This will filter based on the customer id of the advocate who received the reward.        |
| advocateEmail      | query | string(email)     | false    | Email to filter on. This will filter based on the email of the advocate who received the reward.                    |
| pageToken          | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize           | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "createdOn": "2021-02-23T23:18:59Z",
      "rewardType": "Coupon Code",
      "rewardAmount": 10.0,
      "couponCode": "test-coupon-1",
      "trigger": "purchase",
      "advocateEmail": "advocate@example.com",
      "advocateName": "Test Advocate",
      "advocateCustomerId": "4fe0f0cc-14c6-44c3-ba51-dda17412199a",
      "referralCode": "abc123",
      "channel": "facebook",
      "friendEmail": "friend@example.com",
      "friendName": "Test Friend",
      "friendCustomerId": "2a3e06d4-4e99-47c6-b57f-8cb6b86f77ab",
      "campaignId": "5727868f-1a1f-4b26-8104-b8a93b0c30db",
      "campaignName": "Holiday Campaign"
    }
  ]
}
```

<h3 id="getDistributedAdvocateRewards-responses">Responses</h3>

| Name          | Type                                                                                      | Required | Restrictions | Description                                                                                            |
| ------------- | ----------------------------------------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                                                                    | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                                                                    | false    | none         | The total number of results.                                                                           |
| results       | [[distributedAdvocateRewardsGetResponse_results](#getDistributedAdvocateRewards-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getDistributedAdvocateRewards-results">Results</h3>

| Name               | Type   | Required | Restrictions | Description                                                                                                                    |
| ------------------ | ------ | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| createdOn          | string | false    | none         | Timestamp indicating when the reward was created.                                                                              |
| rewardType         | string | false    | none         | One of "Account Credit", "Coupon Code", "Gift Card", "Custom", or "Ledger"                                                     |
| rewardAmount       | number | false    | none         | The monetary value of the reward.                                                                                              |
| couponCode         | string | false    | none         | The coupon code issued with the reward, if any.                                                                                |
| trigger            | string | false    | none         | The event that triggered the reward.                                                                                           |
| advocateEmail      | string | false    | none         | The email of the advocate who received the reward.                                                                             |
| advocateName       | string | false    | none         | The name of the advocate who received the reward.                                                                              |
| advocateCustomerId | string | false    | none         | The customer id of the advocate who received the reward.                                                                       |
| referralCode       | string | false    | none         | The referral code associated with the reward. This code belongs to the share the referred friend clicked on before converting. |
| channel            | string | false    | none         | The share channel the referred friend clicked on before converting.                                                            |
| friendEmail        | string | false    | none         | The email of the referred friend.                                                                                              |
| friendName         | string | false    | none         | The name of the referred friend.                                                                                               |
| friendCustomerId   | string | false    | none         | The customer id of the referred friend.                                                                                        |
| campaignId         | string | false    | none         | The id of the campaign the reward was issued from.                                                                             |
| campaignName       | string | false    | none         | The name of the campaign the reward was issued from.                                                                           |

<h3 id="getDistributedAdvocateRewards-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                                    |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [distributedRewardsGetResponse](#getDistributedAdvocateRewards-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                                     |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                                     |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                                     |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getDistributedFriendIncentives

<a id="opIdgetDistributedFriendIncentives"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name             | In    | Type              | Required | Description                                                                                                         |
| ---------------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate         | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate           | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId       | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| friendCustomerId | query | string            | false    | Customer Id to filter on. This will filter based on the customer id of the user who received the incentive.         |
| friendEmail      | query | string(email)     | false    | Email to filter on. This will filter based on the email of the user who received the incentive.                     |
| pageToken        | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize         | query | string            | false    | Page size limit.                                                                                                    |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "createdOn": "2019-11-05T01:07:38.509Z",
      "rewardType": "Coupon Code",
      "rewardAmount": 5.0,
      "couponCode": "test-coupon-2",
      "trigger": "email_capture",
      "advocateEmail": "advocate@example.com",
      "advocateName": "Test Advocate",
      "advocateCustomerId": "0655e7df-a925-4e56-8509-5c1cbdb78bc2",
      "referralCode": "abc123",
      "channel": "messenger",
      "friendEmail": "friend@example.com",
      "friendName": "Test Friend",
      "friendCustomerId": "ea31b0f9-6af8-4c05-835f-c60cd18f0c50",
      "campaignId": "8c3153f2-2692-4e42-8f95-72eacd36860b",
      "campaignName": "Test Campaign"
    }
  ]
}
```

<h3 id="getDistributedFriendIncentives-responses">Responses</h3>

| Name          | Type                                                                                        | Required | Restrictions | Description                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                                                                      | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                                                                      | false    | none         | The total number of results.                                                                           |
| results       | [[distributedFriendIncentivesGetResponse_results](#getDistributedFriendIncentives-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getDistributedFriendIncentives-results">Results</h3>

| Name               | Type   | Required | Restrictions | Description                                                                                                                       |
| ------------------ | ------ | -------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| createdOn          | string | false    | none         | Timestamp indicating when the incentive was created.                                                                              |
| incentiveType      | string | false    | none         | One of "Account Credit", "Coupon Code", "Gift Card", "Custom", or "Ledger"                                                        |
| incentiveAmount    | number | false    | none         | The monetary value of the incentive.                                                                                              |
| couponCode         | string | false    | none         | The coupon code issued with the incentive, if any.                                                                                |
| trigger            | string | false    | none         | The event that triggered the incentive.                                                                                           |
| advocateEmail      | string | false    | none         | The email of the advocate who referred their friend.                                                                              |
| advocateName       | string | false    | none         | The name of the advocate who referred their friend.                                                                               |
| advocateCustomerId | string | false    | none         | The customer id of the advocate who referred their friend.                                                                        |
| referralCode       | string | false    | none         | The referral code associated with the incentive. This code belongs to the share the referred friend clicked on before converting. |
| channel            | string | false    | none         | The share channel the referred friend clicked on before converting.                                                               |
| friendEmail        | string | false    | none         | The email of the referred friend who received the incentive.                                                                      |
| friendName         | string | false    | none         | The name of the referred friend who received the incentive.                                                                       |
| friendCustomerId   | string | false    | none         | The customer id of the referred friend who received the incentive.                                                                |
| campaignId         | string | false    | none         | The id of the campaign the incentive was issued from.                                                                             |
| campaignName       | string | false    | none         | The name of the campaign the incentive was issued from.                                                                           |

<h3 id="getDistributedFriendIncentives-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                                     |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | -------------------------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [distributedRewardsGetResponse](#getDistributedFriendIncentives-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                                      |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                                      |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                                      |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getEmailCaptures

<a id="opIdgetEmailCaptures"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z",
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
'toDate' => 'string(date-time)'
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
  'fromDate': '2020-01-05T01:07:38.509Z',  'toDate': '2021-01-05T01:07:38.509Z'
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z");
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

| Name             | In    | Type              | Required | Description                                                                                                         |
| ---------------- | ----- | ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| fromDate         | query | string(date-time) | true     | Beginning of the search period.                                                                                     |
| toDate           | query | string(date-time) | true     | End of the search period.                                                                                           |
| campaignId       | query | string(uuid)      | false    | Campaign Id to filter on.                                                                                           |
| emailCaptureType | query | string            | false    | The type of email capture to filter on. One of "advocate" or "friend".                                              |
| email            | query | string(email)     | false    | Email to filter on. This will filter based on the email captured.                                                   |
| pageToken        | query | string            | false    | The page token used to specify which page of results to use. Will be provided in the response to previous requests. |
| pageSize         | query | string            | false    | Page size limit.                                                                                                    |

#### Enumerated Values

| Parameter        | Value    |
| ---------------- | -------- |
| emailCaptureType | advocate |
| emailCaptureType | friend   |

> Example responses

> 200 Response

```json
{
  "nextPageToken": "eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0",
  "totalResults": 1,
  "results": [
    {
      "name": "Test Customer",
      "email": "user@example.com",
      "widgetName": "Friend Incentive Widget",
      "campaignId": "de07e043-0730-4d32-b52c-146ba61cb859",
      "campaignName": "Evergreen Campaign",
      "createdOn": "2021-02-23T01:20:14Z",
      "ipAddress": "192.168.0.1",
      "emailCaptureType": "friend",
      "newsletterOptIn": true
    }
  ]
}
```

<h3 id="getEmailCaptures-responses">Responses</h3>

| Name          | Type                                                            | Required | Restrictions | Description                                                                                            |
| ------------- | --------------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------ |
| nextPageToken | string                                                          | false    | none         | A token representing the next page of results. Pass this token in as pageToken with your next request. |
| totalResults  | number                                                          | false    | none         | The total number of results.                                                                           |
| results       | [[emailCapturesGetResponse_results](#getEmailCaptures-results)] | false    | none         | The records retrieved for this page.                                                                   |

<h3 id="getEmailCaptures-results">Results</h3>

| Name             | Type              | Required | Restrictions | Description                                                                                                                                                                                                                                |
| ---------------- | ----------------- | -------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| name             | string            | false    | none         | Name submitted with the email capture, if any.                                                                                                                                                                                             |
| email            | string(email)     | false    | none         | The captured email.                                                                                                                                                                                                                        |
| widgetName       | string            | false    | none         | The name of the widget used to capture the email.                                                                                                                                                                                          |
| campaignId       | string(uuid)      | false    | none         | The id of the campaign used to capture the email.                                                                                                                                                                                          |
| campaignName     | string            | false    | none         | The name of the campaign used to capture the email.                                                                                                                                                                                        |
| createdOn        | string(date-time) | false    | none         | Timestamp of the email capture.                                                                                                                                                                                                            |
| ipAddress        | string(ipv4)      | false    | none         | IP address of the user who submitted their email.                                                                                                                                                                                          |
| emailCaptureType | string            | false    | none         | The type of email capture based on the widget the email was submitted to. One of "advocate", "friend", or "other". "Other" means the email was captured by a friend incentive widget, but did not have any attribution associated with it. |
| newsletterOptIn  | boolean           | false    | none         | Whether or not the user opted in to receive newsletters.                                                                                                                                                                                   |

<h3 id="getEmailCaptures-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                  |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [getEmailCapturesResponse](#getEmailCaptures-responses) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                   |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                   |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                   |

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
bearerAuth
</aside>

## getEmailMetrics

> Code samples

```shell
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/email-metrics?fromDate=2021-04-07&toDate=2021-04-07&zone=America%2FLos_Angeles&includeSeries=true \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://mapi.fbot.me/v1/analytics/email-metrics?fromDate=2021-04-07&toDate=2021-04-07&zone=America%2FLos_Angeles&includeSeries=true HTTP/1.1
Host: mapi.fbot.me
Accept: application/json

```

```javascript
const headers = {
  Accept: "application/json",
  Authorization: "Bearer {access-token}",
};

fetch(
  "https://mapi.fbot.me/v1/analytics/email-metrics?fromDate=2021-04-07&toDate=2021-04-07&zone=America%2FLos_Angeles&includeSeries=true",
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

result = RestClient.get 'https://mapi.fbot.me/v1/analytics/email-metrics',
  params: {
  'fromDate' => 'string(date)',
'toDate' => 'string(date)',
'zone' => 'string',
'includeSeries' => 'true',
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://mapi.fbot.me/v1/analytics/email-metrics', params={
  'fromDate': '2021-04-07',  'toDate': '2021-04-07',  'zone': 'America/Los_Angeles',
  'includeSeries': 'true',
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
    $response = $client->request('GET','https://mapi.fbot.me/v1/analytics/email-metrics', array(
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
URL obj = new URL("https://mapi.fbot.me/v1/analytics/email-metrics?fromDate=2021-04-07&toDate=2021-04-07&zone=America%2FLos_Angeles&includeSeries=true");
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
    req, err := http.NewRequest("GET", "https://mapi.fbot.me/v1/analytics/email-metrics", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /v1/analytics/email-metrics`

_Endpoint to retrieve email metrics_

Get email metrics.

<h3 id="emailmetricsget-parameters">Parameters</h3>

| Name          | In    | Type         | Required | Description                                                                         |
| ------------- | ----- | ------------ | -------- | ----------------------------------------------------------------------------------- |
| fromDate      | query | string(date) | true     | Beginning of the search period. Whole dates only (no timestamps).                   |
| toDate        | query | string(date) | true     | End of the search period. Whole dates only (no timestamps).                         |
| zone          | query | string       | true     | Timezone for the search period.                                                     |
| campaignId    | query | string(uuid) | false    | Campaign Id to filter results on.                                                   |
| widgetId      | query | string(uuid) | false    | Widget Id to filter results on.                                                     |
| includeSeries | query | string       | false    | Indicates whether or not to include a timeseries in the results. Defaults to false. |

> Example responses

> 200 Response

```json
{
  "fromDate": "2021-04-07",
  "toDate": "2021-04-07",
  "zone": "string",
  "shareEmails": {
    "totalOpens": 10,
    "uniqueOpens": 7,
    "uniqueClicks": 13,
    "totalClicks": 15,
    "shares": 14,
    "recipients": 17,
    "delivered": 14,
    "bounced": 0,
    "spam": 0
  },
  "reminderEmails": {
    "totalOpens": 5,
    "uniqueOpens": 2,
    "uniqueClicks": 5,
    "totalClicks": 7,
    "shares": 4,
    "recipients": 4,
    "delivered": 4,
    "bounced": 0,
    "spam": 0
  },
  "series": [
    {
      "date": "2021-04-07",
      "shareEmails": {
        "totalOpens": 10,
        "uniqueOpens": 7,
        "uniqueClicks": 13,
        "totalClicks": 15,
        "shares": 14,
        "recipients": 17,
        "delivered": 14,
        "bounced": 0,
        "spam": 0
      },
      "reminderEmails": {
        "totalOpens": 5,
        "uniqueOpens": 2,
        "uniqueClicks": 5,
        "totalClicks": 7,
        "shares": 4,
        "recipients": 4,
        "delivered": 4,
        "bounced": 0,
        "spam": 0
      }
    }
  ]
}
```

<h3 id="emailmetricsget-responses">Responses</h3>

| Name           | Type                                                                                  | Required | Restrictions | Description                                                                           |
| -------------- | ------------------------------------------------------------------------------------- | -------- | ------------ | ------------------------------------------------------------------------------------- |
| fromDate       | string(date)                                                                          | false    | none         | Beginning of the search period.                                                       |
| toDate         | string(date)                                                                          | false    | none         | End of the search period.                                                             |
| zone           | string                                                                                | false    | none         | Timezone for the search period.                                                       |
| shareEmails    | [ShareEmailMetricsSeriesItem](#emailmetricsget-share-email-metrics-series-item)       | false    | none         | Metrics for initial share emails.                                                     |
| reminderEmails | [ReminderEmailMetricsSeriesItem](#emailmetricsget-reminder-email-metrics-series-item) | false    | none         | Metrics for reminder emails.                                                          |
| series         | [[EmailMetricsSeries](#emailmetricsget-series)]                                       | false    | none         | A time series that breaks down metrics by day. Only include if includeSeries is true. |

<h3 id="emailmetricsget-series">EmailMetricsSeries</h3>
| Name         | Type   | Required | Restrictions | Description                                                                       |
| ------------ | ------ | -------- | ------------ | --------------------------------------------------------------------------------- |
| date | string | false | none | Date for the series item |
| shareEmails | [ShareEmailMetricsSeriesItem](#emailmetricsget-share-email-metrics-series-item)  | false | none | Share email metrics for the specified date. |
| reminderEmails | [ReminderEmailMetricsSeriesItem](#emailmetricsget-reminder-email-metrics-series-item) | false | none | Reminder email metrics for the specified date. |

<h3 id="emailmetricsget-share-email-metrics-series-item">ShareEmailMetricsSeriesItem</h3>

| Name         | Type   | Required | Restrictions | Description                                                                       |
| ------------ | ------ | -------- | ------------ | --------------------------------------------------------------------------------- |
| totalOpens   | number | false    | none         | Total number of email open events.                                                |
| uniqueOpens  | number | false    | none         | Number of unique emails opened.                                                   |
| uniqueClicks | number | false    | none         | Number of unique emails clicked.                                                  |
| totalClicks  | number | false    | none         | Total number of email click events.                                               |
| shares       | number | false    | none         | Total number of email shares.                                                     |
| recipients   | number | false    | none         | Number of recipients for email shares (can be greater than the number of shares). |
| delivered    | number | false    | none         | Number of emails delivered.                                                       |
| bounced      | number | false    | none         | Number of emails bounced.                                                         |
| spam         | number | false    | none         | Number of emails that received spam complaints.                                   |

<h3 id="emailmetricsget-reminder-email-metrics-series-item">ReminderEmailMetricsSeriesItem</h3>

| Name         | Type   | Required | Restrictions | Description                                                                       |
| ------------ | ------ | -------- | ------------ | --------------------------------------------------------------------------------- |
| totalOpens   | number | false    | none         | Total number of email open events.                                                |
| uniqueOpens  | number | false    | none         | Number of unique emails opened.                                                   |
| uniqueClicks | number | false    | none         | Number of unique emails clicked.                                                  |
| totalClicks  | number | false    | none         | Total number of email click events.                                               |
| recipients   | number | false    | none         | Number of recipients for email shares (can be greater than the number of shares). |
| delivered    | number | false    | none         | Number of emails delivered.                                                       |
| bounced      | number | false    | none         | Number of emails bounced.                                                         |
| spam         | number | false    | none         | Number of emails that received spam complaints.                                   |

<h3 id="emailmetricsget-response-codes">Response Codes</h3>

| Status | Meaning                                                                    | Description                                  | Schema                                                    |
| ------ | -------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------- |
| 200    | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)                    | 0 or more records are retrieved.             | [emailMetricsGetResponse](#schemaemailmetricsgetresponse) |
| 422    | [Unprocessable Entity](https://tools.ietf.org/html/rfc2518#section-10.3)   | Unprocessable Entity                         | [Error](#schemaerror)                                     |
| 429    | [Too Many Requests](https://tools.ietf.org/html/rfc6585#section-4)         | Too many requests                            | [Error](#schemaerror)                                     |
| 500    | [Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1) | Internal Server Error (uncontrolled failure) | [Error](#schemaerror)                                     |

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

All world timezones are supported.

```json
"America/Adak"
```

#### Enumerated Values

| Example Values                 |
| ---------------------- |
| America/Adak           |
| America/Anchorage      |
| America/Anguilla       |
| America/Antigua        |
| America/Araguaina      |
| America/Argentina      |
| America/Aruba          |
| America/Asuncion       |
| America/Atikokan       |
| America/Atka           |
| America/Bahia          |
| America/Bahia_Banderas |
| America/Barbados       |
| America/Belem          |
| America/Belize         |
| America/Blanc          |
| America/Boa_Vista      |
| America/Bogota         |
| America/Boise          |
| America/Buenos_Aires   |
| America/Cambridge_Bay  |
| America/Campo_Grande   |
| America/Cancun         |
| America/Caracas        |
| America/Catamarca      |
| America/Cayenne        |
| America/Cayman         |
| America/Chicago        |
| America/Chihuahua      |
| America/Coral_Harbour  |
| America/Cordoba        |
| America/Costa_Rica     |
| America/Creston        |
| America/Cuiaba         |
| America/Curacao        |
| America/Danmarkshavn   |
| America/Dawson         |
| America/Dawson_Creek   |
| America/Denver         |
| America/Detroit        |
| America/Dominica       |
| America/Edmonton       |
| America/Eirunepe       |
| America/El_Salvador    |
| America/Ensenada       |
| America/Fortaleza      |
| America/Fort_Nelson    |
| America/Fort_Wayne     |
| America/Glace_Bay      |
| America/Godthab        |
| America/Goose_Bay      |
| America/Grand_Turk     |
| America/Grenada        |
| America/Guadeloupe     |
| America/Guatemala      |
| America/Guayaquil      |
| America/Guyana         |
| America/Halifax        |
| America/Havana         |
| America/Hermosillo     |
| America/Indiana        |
| America/Indianapolis   |
| America/Inuvik         |
| America/Iqaluit        |
| America/Jamaica        |
| America/Jujuy          |
| America/Juneau         |
| America/Kentucky       |
| America/Knox_IN        |
| America/Kralendijk     |
| America/La_Paz         |
| America/Lima           |
| America/Los_Angeles    |
| America/Louisville     |
| America/Lower_Princes  |
| America/Maceio         |
| America/Managua        |
| America/Manaus         |
| America/Marigot        |
| America/Martinique     |
| America/Matamoros      |
| America/Mazatlan       |
| America/Mendoza        |
| America/Menominee      |
| America/Merida         |
| America/Metlakatla     |
| America/Mexico_City    |
| America/Miquelon       |
| America/Moncton        |
| America/Monterrey      |
| America/Montevideo     |
| America/Montreal       |
| America/Montserrat     |
| America/Nassau         |
| America/New_York       |
| America/Nipigon        |
| America/Nome           |
| America/Noronha        |
| America/North_Dakota   |
| America/Ojinaga        |
| America/Panama         |
| America/Pangnirtung    |
| America/Paramaribo     |
| America/Phoenix        |
| America/Port           |
| America/Porto_Acre     |
| America/Porto_Velho    |
| America/Port_of_Spain  |
| America/Puerto_Rico    |
| America/Punta_Arenas   |
| America/Rainy_River    |
| America/Rankin_Inlet   |
| America/Recife         |
| America/Regina         |
| America/Resolute       |
| America/Rio_Branco     |
| America/Rosario        |
| America/Santarem       |
| America/Santa_Isabel   |
| America/Santiago       |
| America/Santo_Domingo  |
| America/Sao_Paulo      |
| America/Scoresbysund   |
| America/Shiprock       |
| America/Sitka          |
| America/St_Barthelemy  |
| America/St_Johns       |
| America/St_Kitts       |
| America/St_Lucia       |
| America/St_Thomas      |
| America/St_Vincent     |
| America/Swift_Current  |
| America/Tegucigalpa    |
| America/Thule          |
| America/Thunder_Bay    |
| America/Tijuana        |
| America/Toronto        |
| America/Tortola        |
| America/Vancouver      |
| America/Virgin         |
| America/Whitehorse     |
| America/Winnipeg       |
| America/Yakutat        |
| America/Yellowknife    |