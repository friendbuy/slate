# Reward Validation Callback

### Overview

The Reward Validation Callback feature is used to determine whether or not Friendbuy should fulfill the reward for a conversion based on logic in your own system, such as returns or cancellations. This is meant to provide flexibility on top of the fraud checks and reward criteria that Friendbuy provides.

### How it Works <a id="how-it-works"></a>

When validating a reward, we will make an HTTP POST request to the url provided in the Validation URL configuration of Reward Criteria. The HTTP response code returned by your system will indicate if the reward should be fulfilled or not. A response code of 200 will validate the reward. A response code of 400 will invalidate the reward. Any other response code will result be interpreted as an error and will trigger our retry protocol.

The request body will include details about the purchase that generated the conversion, such as Advocate data, purchase date, order id, and more. The full data included is described below.

### Retry Behavior

When the Reward Validation Callback receives a status code that is not a 200 or a 400, we will attempt to retry the request every 15 minutes until 72 hours have passed or the reward is approved or rejected, whichever comes first. If at the end of 72 hours the response code is still something other than 200 or 400, we will reject the reward and note that status as an error. 

### advocate

## Payload

| Property | Type | Description |
| :--- | :--- | :--- |
| customerId | string | The customer ID of the Advocate. Note: this is your customer ID provided to friendbuy through the javascript integration, not an internal ID generated by friendbuy. |
| email | string | The email address of the Advocate. |
| ipAddress | string | The IP Address of the Advocate. |

| Property | Type | Description |
| :--- | :--- | :--- |
| eventType | string | The event type that triggered the conversion. Currently, only `purchase` events are supported by the Reward Validation Callback. |
| purchase | object | Details about the purchase that triggered the reward. Described in detail below. |
| createdOn | ISO timestamp | The date and time the event was created. |
| campaignId | string | The id of the campaign associated with the reward. |
| advocate | object | Details about the Advocate who earned the reward. Described in detail below. |

### purchase

Event details will be available in the `purchase` property of the request with the following format:

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | Order id of the purchase. |
| amount | number | The order total. |
| currency | string | The currency of the purchase. For example: "USD", "GBP", "CAD". |
| isNewCustomer | Boolean | A true or false value indicating whether the user who made the purchase is a new customer or not. |
| date | ISO timestamp | The date and time the purchase was made. |
| products | array | A list of products purchased. Described in detail below. |
| email | string | The email address of the user who made the purchase. |
| customerId | string | The customer id of the user who made the purchase, if provided. Note: this is your customer ID provided to friendbuy through the javascript integration, not an internal ID generated by friendbuy. |
| ipAddress | string | The IP Address of the user who made the purchase. |

### product

Product details will be available in the `purchase.products` property of the request with the following format. Note: All product data is provided to friendbuy by the javascript integration

| Property | Type | Description |
| :--- | :--- | :--- |
| sku | string | The SKU of the product. |
| name | string | The name of the product. |
| quantity | number | How many of the product were purchased. |
| price | number | The price of the product. |
| currency | string | The currency of the products price. For example: `USD`. |
| description | string | A description of the product. |
| category | string | The category of the product. |
| url | string | The url of the product page. |
| imageUrl | string | The url of the product image. |

## Example

```javascript
{
  "eventType": "purchase",
  "createdOn": "2019-11-18T23:48:30.017Z",
  "campaignId": "89d78d25-6a33-4873-8b0e-410e3e7c10fa",
  "purchase": {
    "id": "order-66",
    "amount": 100,
    "currency": "USD",
    "isNewCustomer": true,
    "ipAddress": "12.156.140.124",
    "date": "2019-11-18T23:48:30.017Z",
    "email": "test@example.org",
    "customerId": "123",
    "ipAddress": "10.523.123.122",
    "products": [
      {
        "sku": "test-product",
        "name": "Test Product",
        "quantity": 1,
        "price": 10.00,
        "currency": "USD",
        "description": "A test product",
        "category": "Apparel",
        "url": "https://example.org/test-product",
        "imageUrl": "https://example.org/test-product/image.jpg"
    ]
  },
  "advocate": {
    "customerId": "66",
    "email": "britain+test@friendbuy.com",
    "ipAddress": "12.156.140.124"
  }
}
```

### Signature Validation

You can verify the authenticity of a webhook request or client API integration from friendbuy by analyzing its cryptographic signature. When friendbuy sends a request to your endpoints, a signature is placed in the X-Friendbuy-Hmac-SHA256 header, and is computed by Base64-encoding the HMAC-SHA1 hash of the request body with your friendbuy secret key. To verify the signature:

1. Calculate an HMAC-SHA-256 composition of the JSON request body: `HMAC(api_secret, json_body)`
2. Base64 encode the resulting value.
3. If the Base64 encoded hash matches the signature header, the request is valid.
4. Calculate an HMAC-SHA-256 composition of the JSON request body: `HMAC(api_secret, json_body)`
5. Base64 encode the resulting value.
6. If the Base64 encoded hash matches the signature header, the request is valid.

NodeJS Example:

```javascript
export function verifyWebhook(data, hmacSignature) {
  const providedHmac = Buffer.from(hmacSignature, "utf-8");
  const generatedHash = Buffer.from(
    crypto
      .createHmac("sha256", FRIENDBUY_SECRET_KEY)
      .update(data)
      .digest("base64"),
    "utf-8"
  );
  let hashEquals = false;
  try {
    hashEquals = crypto.timingSafeEqual(generatedHash, providedHmac);
  } catch (e) {
    hashEquals = false;
  }
  return hashEquals;
}
```

You can get your Webhook secret key by going to Developer Center &gt; Webhooks and copying the Digital Signature in the retailer app.
