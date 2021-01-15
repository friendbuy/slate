# Signature Validation

> NodeJS Example

```typescript
export function verifySignature(data, hmacSignature) {
  const providedHmac = Buffer.from(hmacSignature, "utf-8");
  const generatedHash = Buffer.from(
    crypto
      .createHmac("sha256", FRIENDBUY_SECRET_KEY)
      .update(JSON.stringify(data))
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

You can verify the authenticity of a webhook request, reward validation callback, or visitor status payload from friendbuy by analyzing its cryptographic signature. For webhooks and integrations, when friendbuy sends a request to your endpoints, the signature will be included in the X-Friendbuy-Hmac-SHA256 header. Visitor status includes the signature in the callback data, next to the payload.

The signature is computed by Base64 encoding the HMAC-SHA1 hash of the request body with your friendbuy secret key. Your friendbuy secret key is in the retailer app. Go to <a href="https://retailer.fbot-sandbox.me/developers/general">Developer Center &gt; Friendbuy code</a> and copy the Secret Key.

To verify the signature:

1. Calculate an HMAC-SHA-256 composition of the JSON request body:  
   `HMAC(api_secret, json_body)`
2. Base64 encode the resulting value.
3. If the Base64 encoded hash matches the signature header, the request is valid.
