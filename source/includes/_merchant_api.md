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

The base URL for all Friendbuy Merchant API endpoints is https://mapi.fbot.me/v1. For full reference documentation, see [https://app.swaggerhub.com/apis/friendbuy/Friendbuy-mapi/1.1.0](https://app.swaggerhub.com/apis/friendbuy/Friendbuy-mapi/1.1.0).

## Authorization

### Summary

The Friendbuy Merchant API uses Bearer Tokens to authorize requests.

To get a Bearer Token for authorization:

1. Get your access key and secret key from the retailer app
2. Make a POST request to **/authorization**:
   1. Set the **Content-Type** header to **application/json**
   2. The body for the request should be json containing two parameters, access key and secret key
3. The response will contain a bearer token in the “**token**” property and the expiration date of the token
4. You will use this token to authorize any further API requests.

### Example Request Body

```text
{
  "key": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "secret": "95eb1c78-f77e-4c55-828e-17ed3e0163a2"
}
```

### Example Response Body

```text
{
  "tokenType": "Bearer",
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiO...",
  "expires": "2020-03-20T22:58:56.588Z"
}
```

## Generating Referral Links

### Summary

The Friendbuy Merchant API can be used to generate a personal referral link for a specific advocate/campaign combination. The email of the advocate and the id of the campaign you want the link to be associated with are required. Additional parameters including customer id, first name, and last name can also be provided to associate additional details with the referral link.

To retrieve a personal referral link, make a **POST** request to **/personal-referral-links**. The response will include the personal referral link in the “link” parameter.

You can then distribute this link however you wish. Common use cases involve sending a personal referral link to a subset of customers through email to promote the referral program and retrieving a link to be displayed within a mobile app.

### **Example Request Body**

```text
{
  "email": "test@example.com",
  "campaignId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "customerId": "string",
  "firstName": "John",
  "lastName": "Smith",
  "destinationUrlQueryParams": {"vip": true},
}
```

### **Example Response Body**

```text
{
  "link": "https://fbuy.io/xhaf5hps",
  "createdOn": "2020-01-05T01:07:38.509Z"
}
```

## Tracking a Purchase

### **Summary**

The Friendbuy Merchant API can be used to send purchase events to Friendbuy as an alternative or supplement to our Javascript-based pixel tracking. Common use cases include tracking purchases that occur offline and purchases that occur within a mobile app.

When you submit a purchase using the Friendbuy Merchant API, you must submit a unique order id, a purchase amount, and the currency the purchase was in. We strongly recommend passing the email and/or customer id of the user who made the purchase. We also recommend passing a value for isNewCustomer, which we use as part of our reward criteria when determining if the advocate should earn a reward.

A key component of tracking a purchase through the Merchant API is the ability to pass in a referral code or coupon code with the purchase. If either of these values is present, we will attempt to use the referral code and then the coupon code to establish attribution to the advocate that referred the user making the purchase. **NOTE: the coupon code must have been distributed from a Friend Incentive widget in order for Friendbuy to establish attribution.**

Lastly, product details may be passed to facilitate rewards based on purchasing a specific product.

To track a purchase, make a **POST** request to **/event/purchase.**

### **Example Request Body**

```text
{
  "orderId": "test-order-123",
  "email": "user@example.com",
  "customerId": "15534334",
  "firstName": "Test",
  "lastName": "User",
  "amount": 10.00,
  "currency": "USD",
  "isNewCustomer": false,
  "couponCode": "FRIEND-OFFER-244432",
  "refCode": "xhaf5hps",
  "products": [
    {
      "sku": "SKU123324",
      "name": "Test Produce",
      "quantity": 1,
      "price": 10.00
    }
  ],
}
```

### **Example Response Body**

```javascript
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

## **Tracking a Signup**

### **Summary**

In much the same way that the Friendbuy Merchant API can be used to track purchases, it can also be used to track account signups. Tracking account signups is completely optional, but depending on your campaign settings you may want to track signups if they are an integral part of your referral flow \(i.e. you want to reward signups differently than purchases\). **NOTE: The ability to configure rewards differently for signups is not yet exposed in the Friendbuy Retailer App but can be configured on the backend by Friendbuy.**

Tracking a signup through the API requires an email address and a customer id. You can also optionally pass in customer first name and last name, referral code, and coupon code.

Like with purchases, Friendbuy will attempt to establish attribution if referral code or coupon code is passed in.

To track a signup, make a **POST** request to **/event/account-sign-up**

### **Example Request Body**

```javascript
{
  "email": "user@example.com",
  "customerId": "15529938",
  "firstName": "Test",
  "lastName": "User",
  "refCode": "xhaf5hps",
  "couponCode": "FRIEND-OFFER-244432",
}
```

### **Example Response Body**

```javascript
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

## **Tracking a Custom Event**

### **Summary**

In addition to tracking purchases and signups, Friendbuy also allows you to track custom event types through the API.

Tracking a custom event through the Merchant API works just like tracking a signup, except that you are also required to pass an eventType. The eventType can be any string that you want to use to denote the event you are tracking. You must configure this event type in your campaign settings in order for it to be properly tracked and attributed to a campaign.

As with purchases and signups, Friendbuy will attempt to establish attribution to an advocate if referral code or coupon code is present

To track a custom event, make a **POST** request to **/event/custom**.

### Example Request Body

```javascript
{
  "email": "user@example.com",
  "eventType": "recurring_order",
  "customerId": "15529938"
  "isNewCustomer": false,
  "firstName": "Test",
  "lastName": "User",
  "refCode": "xhaf5hps",
  "couponCode": "FRIEND-OFFER-244432",
}
```

### Example Response Body

```javascript
{
  "eventId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

## Tracking Customer Details

### Summary

Many Friendbuy Merchant API endpoints allow for the tracking of limited customer data. In some cases, you may wish to fill in detailed information for all or certain customers. Email and customerId are required values. You can also track the following: isNewCustomer, firstName, lastName, age, gender, zipCode, state, city, category, country, language.

**The primary use case of tracking customer details will be to facilitate widget and reward targeting and segmentation when that feature is released in the future.**

To track a customer make a **POST** request to **/customer**

### **Example Request Body**

```javascript
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
  "language": "English",
}
```

### **Example Response Body**

```javascript
{
  "customerId": "7b5e9a0a-3386-49c8-84d7-6d4047639285",
  "createdOn": "2020-03-05T01:07:38.509Z"
}
```

## Request User Data for CCPA/GDPR

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

### **Example Requests**

```text
GET /user-data?email=test@example.com
GET /user-data?customerID=1554332
```

### **Example Response Body**

```javascript
{
  "emails": [
    "user@example.com", "test@example.com"
  ],
  "names": [
    "Test User", "Other User"
  ],
  "customerIds": [
    "1554332"
  ],
  "ipAddresses": [
    "127.0.0.0.1"
  ],
  "languages": [
    "English", "Spanish"
  ],
  "userAgents": [
    "Mozilla/5.0 (Macintosh; Intel Mac OS X x.y; rv:42.0) Gecko/20100101 Firefox/42.0"
  ],
  "colorDepths": [
    0
  ],
  "platforms": [
    "IOS"
  ],
  "screenSizes": [
    "3072x1920"
  ],
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

## **Deleting User Data for CCPA/GDPR**

### **Summary**

In addition to retrieving user data for CCPA or GDPR, the Friendbuy Merchant API also allows you to request the deletion of user data to fulfill deletion requests from end-users. The response body contains a task_id that can be used for troubleshooting if necessary. All deletion requests run asynchronously, so if the request is successfully registered you will receive a response code of 204. Any other response code indicates an error.

**NOTE: Once this request is made any data associated with that email or customer id \(as indicated by the GET /user-data endpoint\) will be permanently deleted or redacted as appropriate. This action is completely irreversible, so be sure you want to delete this data before making the request.**

To request data deletion for a given email address or customer id, make a **DELETE** request to **/user-data** providing the email and/or customer id of the user requesting deletion as a query string parameter

### Example Requests

```text
DELETE /user-data?email=test@example.com
DELETE /user-data?customerID=1554332
```

### **Example Response**

```javascript
{
  "task_id": "47fd3e67-8659-42f2-9d03-192d82a48651"
}
```