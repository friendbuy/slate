# Visitor Status

> Format

```html
<script>
  friendbuyAPI.push(["getVisitorStatus", callback]);
</script>
```

> Example Invocation

```html
<script>
  friendbuyAPI.push([
    "getVisitorStatus",
    function (status) {
      console.log(status);
      // Do something based on the visitor status data
    },
  ]);
</script>
```

> Example responses

> Failed reward criteria

```json
{
  "status": "success",
  "payload": {
    "globalId": "dd61f81a-e590-4b69-b3b9-96a3c56238ea",
    "profileId": "155adb3c-196d-4f22-8e21-4e39c81ddc17",
    "customerId": "CUST01234",
    "attributionId": "278dcca0-fc4d-4ace-9e79-d8254b867ac7",
    "isSelfReferral": false,
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "advocateFirstName": "Britian",
    "advocateRewardInfo": {
      "requirementsFailed": [
        {
          "name": "new customer",
          "message": "Customer is known as 3078574637120, found matching purchase: 2112707199040"
        },
        {
          "name": "new customer",
          "message": "Customer is known as jeremy+test@friendbuy.com, found matching purchase: 2112707199040, 987398472938749, 780927840912740, 98279871294"
        },
        {
          "name": "new customer",
          "message": "Customer is known as jeremy+friend@friendbuy.com, found matching purchase: 2112710377536"
        }
      ],
      "integrationRequirementsFailed": [],
      "tiersCheckResult": {
        "conversionCount": 1,
        "tierIndex": 0,
        "nextTier": null,
        "tier": {
          "delivery": "codeBank",
          "couponBankId": "f299e6ca-0266-4a1e-8b0e-65fb9ef629b2",
          "rewardType": "discount"
        },
        "message": "Found a reward config for 1 conversions",
        "tierStatus": "pass"
      }
    }
  },
  "signature": "ajKYw+By3o9TthxDUsOuTsmCzsvJVsLKVBIhQKvdnco="
}
```

> Passed reward criteria

```json
{
  "status": "success",
  "payload": {
    "globalId": "e3d60027-e176-41cd-9fc8-8e44bd2c0bfa",
    "profileId": "c95b77f5-c9a8-44eb-bff3-56b61febff2f",
    "customerId": "CUST01234",
    "attributionId": "964224f0-c22c-46eb-a0c4-6b20f11bddfb",
    "isSelfReferral": false,
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "advocateFirstName": "Britian",
    "advocateRewardInfo": {
      "requirementsFailed": [],
      "integrationRequirementsFailed": [],
      "tiersCheckResult": {
        "conversionCount": 1,
        "tierIndex": 0,
        "nextTier": null,
        "tier": {
          "delivery": "codeBank",
          "couponBankId": "f299e6ca-0266-4a1e-8b0e-65fb9ef629b2",
          "rewardType": "discount"
        },
        "message": "Found a reward config for 1 conversions",
        "tierStatus": "pass"
      }
    }
  },
  "signature": "ZpQV4uZAPLl0hOdqsLpTen9AoWOcWqfGYI9VPFZbgR8="
}
```

Visitor Status returns relevant data we have captured around the current user.

The `callback` parameter in the `getVisitorStatus` command is a function that will receive an object containing the
visitor status `payload` and a `signature` to verify the authenticity of the `payload`.

### Verifying the Visitor Status Payload

> NodeJS Example

```typescript
export function verifyVisitorStatus(payload, hmacSignature) {
  const providedHmac = Buffer.from(hmacSignature, "utf-8");
  const generatedHash = Buffer.from(
    crypto
      .createHmac("sha256", FRIENDBUY_SECRET_KEY)
      .update(JSON.stringify(payload))
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

You may wish to distribute rewards or do some other desirable action for the user based on their visitor status response.
To prevent fraud you can verify the `payload` validates against the `signature` provided in the response.
the action you wish to perform.

1. Calculate an HMAC-SHA-256 composition of the JSON request body:  
   `HMAC(api_secret, json_body)`
2. Base64 encode the resulting value.
3. If the Base64 encoded hash matches the signature header, the request is valid.

You can get your Webhook secret key by going to the retailer app, Developer Center &gt; Friendbuy code and copy the Secret Key https://retailer.fbot-sandbox.me/developers/general
