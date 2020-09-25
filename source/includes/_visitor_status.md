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
    "attributionId": "278dcca0-fc4d-4ace-9e79-d8254b867ac7",
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "isSelfReferral": false,
    "advocate": {
      "customerId": "9843534588704",
      "firstName": "Sam",
      "rewardInfo": {
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
    "attributionId": "964224f0-c22c-46eb-a0c4-6b20f11bddfb",
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "isSelfReferral": false,
    "advocate": {
      "customerId": "9843534588704",
      "firstName": "Sam",
      "rewardInfo": {
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
    }
  },
  "signature": "ZpQV4uZAPLl0hOdqsLpTen9AoWOcWqfGYI9VPFZbgR8="
}
```

Visitor Status returns relevant data we have captured around the current user.

The `callback` parameter in the `getVisitorStatus` command is a function that will receive an object containing the
visitor status `payload` and a `signature` to verify the authenticity of the `payload`.

## Common Use Cases for Visitor Status:

Applying an account credit or session based discount for referrals. If you wish to give your customers a discount if they came through a friendbuy referral you can check both `isSelfReferral` and `referralCodeBlocked`. If both are false the referral is valid.

Getting information about the referral advocate. The advocate first name is provided as well as the advocate customer ID to allow you to customize a message the friend receives when arriving at your site.

Issuing an advocate reward. The advocate reward info shows if we have determined whether the advocate meets the criteria for a reward.

## Verifying the Visitor Status Payload

You may wish to distribute rewards or do some other desirable action for the user based on their visitor status response.
To prevent fraud you can verify the `payload` validates against the `signature` provided in the response.

See <a href="#signature-validation">Signature Validation</a> for instructions on validating the signature.
