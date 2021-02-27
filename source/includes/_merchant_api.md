# Merchant API Guides

## Summary

The Friendbuy Merchant API is a REST API that allows for communication directly with Friendbuy.

Common use cases for the Merchant API are:

- Create purchases, signups, and custom events
- Create customer records in Friendbuy
- Create referral links for a customer or email.
- Retrieve user data for CCPA and GDPR
- Delete user data for CCPA and GDPR
- And many more to come

## Base URL

The base URL for all Friendbuy Merchant API endpoints is https://mapi.fbot.me/v1. For full reference documentation, see [Merchant API Details](#merchant-api-mapi-).

## Authorization

> Example Request Body

```json
{
  "key": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "secret": "95eb1c78-f77e-4c55-828e-17ed3e0163a2"
}
```

> Example Response Body

```json
{
  "tokenType": "Bearer",
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiO...",
  "expires": "2020-03-20T22:58:56.588Z"
}
```

### Summary

The Friendbuy Merchant API uses Bearer Tokens to authorize requests.

To get a Bearer Token for authorization:

1. Contact Friendbuy support for your key and secret.
2. Make a POST request to **/authorization**:
   1. Set the **Content-Type** header to **application/json**
   2. The body for the request should be json containing two parameters, access key and secret key
3. The response will contain a bearer token in the “**token**” property and the expiration date of the token
4. You will use this token to authorize any further API requests.

## GET Endpoint Specifications

### Requirements

Unless otherwise stated, all GET endpoints require a toDate, fromDate, and zone to be passed in the query string for the request.

The toDate and fromDate parameters should be an ISO format date string. For example: "2021-02-23T01:20:14Z". The zone identifies which time zone to use with the toDate and FromDate.

> Example Request with Pagination

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles&pageToken=eyJzZWFyY2hBZnRlciI6WzE1OTY1NzE5NDM0NDksIjI1YmU3NDhkLWEyYTgtNDA5ZS1iMmU3LTUyNGU2NGFhY2YzYzg0Y2EyMmJmLTZjZDgtNDQxMy1iOTM0LTM3ZDE1NDhhMGU0NCJdLCJmcm9tRGF0ZSI6IjIwMTktMTItMzFUMDg6MDA6MDAuMDAwWiIsInRvRGF0ZSI6IjIwMjEtMDEtMDFUMDc6NTk6NTkuOTk5WiIsInBhZ2VTaXplIjoyMDAsInpvbmUiOiJBbWVyaWNhL0xvc19BbmdlbGVzIn0 \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response Body with Pagination

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

### Pagination

Unless otherwise noted, all of our GET endpoints support pagination using a pageToken query string parameter.

When making the request for the first page, you just need to pass in a fromDate, toDate, and zone. You can also optionally pass in a page size limit as pageSize.

If there are more total results than the page size, the response body will contain a nextPageToken attribute.

For subsequent requests, passing in nextPageToken from the previous response as pageToken will return the next page of results.

**Note: While using a page token, date ranges and page sizes will be locked to the initial request.**

## GET Widget Views

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/widget-views?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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
      "ipAddress": "192.168.0.1"
    }
  ]
}
```

### Summary

The GET Widget Views endpoint allows you to retrieve all widget views within a given time frame, optionally filtered by **campaignId**, **widgetName**, or **widgetType**. **widgetType** can be either **advocateShare** or **emailCapture**.

To retrieve widget views, make a **GET** request to **/analytics/widget-views**.

View Merchant API details [here](#merchant-api-guides-getwidgetviews)

## GET Shares

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/shares?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Shares endpoint allows you to retrieve all shares within a given time frame, optionally filtered by **campaignId**, **advocateEmail**, **advocateCustomerId**, or **channel**. Shares, like many other records, contain a referralCode that is unique to the share. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

To retrieve shares, make a **GET** request to **/analytics/shares**.

View Merchant API details [here](#merchant-api-guides-getshares)

## GET Clicks

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/clicks?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Clicks endpoint allows you to retrieve all valid clicks within a given time frame, optionally filtered by **campaignId** and/or **channel**. Clicks, like many other records, contain a referralCode that is unique to the share the click came from. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

To retrieve clicks, make a **GET** request to **/analytics/clicks**.

View Merchant API details [here](#merchant-api-guides-getclicks)

## GET Signups

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/account-sign-ups?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Signups endpoint allows you to retrieve all referral signups within a given time frame, optionally filtered by **campaignId**, **customerId**, or **email**. Signups, like many other records, contain a referralCode that is unique to the share the user clicked on before signing up. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

To retrieve signups, make a **GET** request to **/analytics/account-sign-ups**.

View Merchant API details [here](#merchant-api-guides-getsignups)

## GET Purchases

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/purchases?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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
      "totalAmount": 50.0,
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

### Summary

The GET Purchases endpoint allows you to retrieve all referral purchases within a given time frame, optionally filtered by **campaignId**, **customerId**, or **email**. Purchases, like many other records, contain a referralCode that is unique to the share the user clicked on before making the purchase. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

To retrieve purchases, make a **GET** request to **/analytics/purchases**.

View Merchant API details [here](#merchant-api-guides-getpurchases)

## GET Distributed Advocate Rewards

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-advocate-rewards?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Distributed Advocate Rewards endpoint allows you to retrieve all rewards that have been distributed to advocates within a given time frame, optionally filtered by **campaignId**, **advocateCustomerId**, or **advocateEmail**. Distributed Advocate Rewards, like many other records, contain a referralCode that is unique to the share the user clicked on before completing the action that triggered the reward. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

**NOTE This endpoint only returns rewards that we have successfully distributed to advocates. It does not include rewards that have been rejected or rewards distributed to friends. For rewards distributed to friends, use the GET Distributed Friend Incentives endpoint.**

To retrieve distributed advocate rewards, make a **GET** request to **/analytics/distributed-advocate-rewards**.

View Merchant API details [here](#merchant-api-guides-getdistributedadvocaterewards)

## GET Distributed Friend Incentives

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/distributed-friend-incentives?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Distributed Friend Incentives endpoint allows you to retrieve all incentives that have been distributed to referred friends within a given time frame, optionally filtered by **campaignId**, **friendCustomerId**, or **friendEmail**. Distributed Friend Incentives, like many other records, contain a referralCode that is unique to the share the user clicked on before completing the action that triggered the incentive. Referral codes can be used to link different types of events together to create a more complete picture of referral behavior.

**NOTE This endpoint only returns incentives that we have successfully distributed. It does not include incentives that have been rejected.**

To retrieve distributed friend incentives, make a **GET** request to **/analytics/distributed-friend-incentives**.

View Merchant API details [here](#merchant-api-guides-getdistributedfriendincentives)

## GET Email Captures

> Example Request

```curl
# You can also use wget
curl -X GET https://mapi.fbot.me/v1/analytics/email-captures?fromDate=2020-01-05T01%3A07%3A38.509Z&toDate=2021-01-05T01%3A07%3A38.509Z&zone=America%2FLos_Angeles \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

> Example Response

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

### Summary

The GET Email Captures endpoint allows you to retrieve all emails captured by Friendbuy within a given time frame, optionally filtered by **campaignId**, **emailCaptureType**, or **email**. **emailCaptureType** can be either **advocate** or **friend**. **advocate** will retrieve all emails captured by the email gate on a referral widget. **friend** will retrieve all emails captured by friend incentive widgets.

To retrieve email captures, make a **GET** request to **/analytics/email-captures**.

View Merchant API details [here](#merchant-api-guides-getemailcaptures)

## Generating Referral Links

> Example Request Body

```json
{
  "email": "test@example.com",
  "campaignId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "customerId": "string",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": { "vip": true },
  "ipAddress": "127.0.0.1",
  "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.61 Safari/537.36",
  "seed": "johnsmith"
}
```

> Example Response Body

```json
{
  "link": "https://fbuy.io/alias/johnsmith",
  "createdOn": "2020-01-05T01:07:38.509Z"
}
```

### Summary

The Friendbuy Merchant API can be used to generate a personal referral link for a specific advocate/campaign combination. The email of the advocate and the id of the campaign you want the link to be associated with are required. Additional parameters including customer id, first name, and last name can also be provided to associate additional details with the referral link.

To retrieve a personal referral link, make a **POST** request to **/personal-referral-link**. The response will include the personal referral link in the “link” parameter.

You can then distribute this link however you wish. Common use cases involve sending a personal referral link to a subset of customers through email to promote the referral program and retrieving a link to be displayed within a mobile app.

## Decoding the Attribution ID

> Code Samples

```javascript
// This example uses KJUR open source cryptographic library
<script src="https://kjur.github.io/jsrsasign/jsrsasign-latest-all-min.js"></script>;

// Validate fbuy data with public key
const urlParams = new URLSearchParams(window.location.search);
const fbuy = urlParams.get("fbuy");

const publicKey = `-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCv+UDAAmI0GyM9obO1P+N8LGfI
If6m+LgQirR1fQLTcQyu+lrQkqa+BhVa/nouoiPm+ZUKVtFMJJ44xxa4OPvXv3tB
UPyhJJGYvA8ARqXedzXo13AvSmhKBKG1LxpdU1KGTQNj9En7dmlyeXF5UXAddqoo
JizmTNzQy1wmQw14DwIDAQAB
-----END PUBLIC KEY-----`;

const isValid = KJUR.jws.JWS.verify(fbuy, publicKey, ["RS256"]);

// Decode fbuy data
const decoded = KJUR.jws.JWS.parse(fbuy);
const [
  merchantId,
  profileId,
  globalId,
  attributionId,
  domain,
  epoch,
  customerId,
  email,
] = decoded.payloadPP.split(":");
```

### Summary

An `attributionId` will link an event, like a purchase or sign up event, to a referral, allowing Friendbuy to attribute the event to the advocate.

When a Friendbuy referral link is followed, Friendbuy adds the GET parameter `fbuy` to the destination URL. The `fbuy` parameter contains an encoded string, containing the `attributionId` as well as other information relating to the referral. The following event tracking endpoints can use this `attributionId` decoded from the `fbuy` parameter.

## Tracking a Purchase

> Example Request Body

```json
{
  "orderId": "test-order-123",
  "email": "user@example.com",
  "customerId": "15534334",
  "firstName": "Test",
  "lastName": "User",
  "amount": 10.0,
  "currency": "USD",
  "isNewCustomer": false,
  "couponCode": "FRIEND-OFFER-244432",
  "attributionId": "2112d0a1-9d65-456e-a168-382ffe76965a",
  "products": [
    {
      "sku": "SKU123324",
      "name": "Test Produce",
      "quantity": 1,
      "price": 10.0
    }
  ]
}
```

> Example Response Body

```json
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

### **Summary**

The Friendbuy Merchant API can be used to send purchase events to Friendbuy as an alternative or supplement to our Javascript-based pixel tracking. Common use cases include tracking purchases that occur offline and purchases that occur within a mobile app.

When you submit a purchase using the Friendbuy Merchant API, you must submit a unique order id, a purchase amount, and the currency the purchase was in. We strongly recommend passing the email and/or customer id of the user who made the purchase. We also recommend passing a value for isNewCustomer, which we use as part of our reward criteria when determining if the advocate should earn a reward.

A key component of tracking a purchase through the Merchant API is the ability to pass in a referral code or coupon code with the purchase. If either of these values is present, we will attempt to use the referral code and then the coupon code to establish attribution to the advocate that referred the user making the purchase. **NOTE: the coupon code must have been distributed from a Friend Incentive widget in order for Friendbuy to establish attribution.**

Lastly, product details may be passed to facilitate rewards based on purchasing a specific product.

To track a purchase, make a **POST** request to **/event/purchase.**

## **Tracking a Signup**

> Example Request Body

```json
{
  "email": "user@example.com",
  "customerId": "15529938",
  "firstName": "Test",
  "lastName": "User",
  "attributionId": "2112d0a1-9d65-456e-a168-382ffe76965a",
  "couponCode": "FRIEND-OFFER-244432"
}
```

> Example Response Body

```json
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

### **Summary**

In much the same way that the Friendbuy Merchant API can be used to track purchases, it can also be used to track account signups. Tracking account signups is completely optional, but depending on your campaign settings you may want to track signups if they are an integral part of your referral flow \(i.e. you want to reward signups differently than purchases\). **NOTE: The ability to configure rewards differently for signups is not yet exposed in the Friendbuy Retailer App but can be configured on the backend by Friendbuy.**

Tracking a signup through the API requires an email address and a customer id. You can also optionally pass in customer first name and last name, referral code, and coupon code.

Like with purchases, Friendbuy will attempt to establish attribution if referral code or coupon code is passed in.

To track a signup, make a **POST** request to **/event/account-sign-up**

## **Tracking a Custom Event**

> Example Request Body

```json
{
  "email": "user@example.com",
  "eventType": "recurring_order",
  "customerId": "15529938"
  "isNewCustomer": false,
  "firstName": "Test",
  "lastName": "User",
  "attributionId": "2112d0a1-9d65-456e-a168-382ffe76965a",
  "couponCode": "FRIEND-OFFER-244432",
}
```

> Example Response Body

```json
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

### **Summary**

In addition to tracking purchases and signups, Friendbuy also allows you to track custom event types through the API.

Tracking a custom event through the Merchant API works just like tracking a signup, except that you are also required to pass an eventType. The eventType can be any string that you want to use to denote the event you are tracking. You must configure this event type in your campaign settings in order for it to be properly tracked and attributed to a campaign.

As with purchases and signups, Friendbuy will attempt to establish attribution to an advocate if referral code or coupon code is present

To track a custom event, make a **POST** request to **/event/custom**.

## Tracking Customer Details

> Example Request Body

```json
{
  "email": "user@example.com",
  "customerId": "328989893",
  "isNewCustomer": false,
  "firstName": "Test",
  "lastName": "User",
  "age": 23,
  "gender": "male",
  "zipCode": "90038",
  "state": "CA",
  "city": "West Hollywood",
  "category": "VIP",
  "country": "USA",
  "language": "English"
}
```

> Example Response Body

```json
{
  "eventId": "7b5e9a0a-3386-49c8-84d7-6d4047639285",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

### Summary

Many Friendbuy Merchant API endpoints allow for the tracking of limited customer data. In some cases, you may wish to fill in detailed information for all or certain customers. Email and customerId are required values. You can also track the following: isNewCustomer, firstName, lastName, age, gender, zipCode, state, city, category, country, language.

**The primary use case of tracking customer details will be to facilitate widget and reward targeting and segmentation when that feature is released in the future.**

To track a customer make a **POST** request to **/customer**

## Request User Data for CCPA/GDPR

> Example Requests

```text
GET /user-data?email=test@example.com
GET /user-data?customerId=1554332
```

> Example Response Body

```json
{
  "emails": ["user@example.com", "test@example.com"],
  "names": ["Test User", "Other User"],
  "customerIds": ["1554332"],
  "ipAddresses": ["127.0.0.0.1"],
  "languages": ["English", "Spanish"],
  "userAgents": [
    "Mozilla/5.0 (Macintosh; Intel Mac OS X x.y; rv:42.0) Gecko/20100101 Firefox/42.0"
  ],
  "colorDepths": [0],
  "platforms": ["IOS"],
  "screenSizes": ["3072x1920"],
  "trackedEvents": [
    {
      "type": "purchase",
      "url": "https://example.com"
    }
  ],
  "shares": {
    "email": 5,
    "facebook": 1,
    "messenger": 0,
    "sms": 0,
    "twitter": 0,
    "purl": 1
  },
  "conversions": {
    "email": 2,
    "facebook": 0,
    "messenger": 0,
    "sms": 0,
    "twitter": 0,
    "purl": 3
  }
}
```

### **Summary**

In order to comply with CCPA and GDPR requirements, Friendbuy supports the retrieval of any user data for a given email address or customer id. When a request is made, Friendbuy will return the following data points that we have associated with the email address or customer id:

- Emails
- Names
- Customer Ids
- IP Addresses
- Languages
- User Agents
- Device Data including
  - Color depths
  - Platforms
  - Screen sizes
- Tracked events
- Share counts by channel
- Conversion counts by channel

\***\*To make a request for user data, make a **GET** request to **/user-data\*\* providing the email or customer id as a query string parameter.

## **Deleting User Data for CCPA/GDPR**

> Example Requests

```text
DELETE /user-data?email=test@example.com
DELETE /user-data?customerId=1554332
```

> Example Response

```json
{
  "task_id": "47fd3e67-8659-42f2-9d03-192d82a48651"
}
```

### **Summary**

In addition to retrieving user data for CCPA or GDPR, the Friendbuy Merchant API also allows you to request the deletion of user data to fulfill deletion requests from end-users. The response body contains a task_id that can be used for troubleshooting if necessary. All deletion requests run asynchronously, so if the request is successfully registered you will receive a response code of 204. Any other response code indicates an error.

**NOTE: Once this request is made any data associated with that email or customer id \(as indicated by the GET /user-data endpoint\) will be permanently deleted or redacted as appropriate. This action is completely irreversible, so be sure you want to delete this data before making the request.**

To request data deletion for a given email address or customer id, make a **DELETE** request to **/user-data** providing the email and/or customer id of the user requesting deletion as a query string parameter
