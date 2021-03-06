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

> Invalid referral (self-referral detected)

```json
{
  "status": "success",
  "payload": {
    "referralCode": "csb5ag6y",
    "referralCodeBlocked": false,
    "isSelfReferral": true
  },
  "signature": "As+Q8yayyFMGVjRLQ494s7DebeWnB2mWWB36CdYRxF8="
}
```

> Valid referral

```json
{
  "status": "success",
  "payload": {
    "attributionId": "964224f0-c22c-46eb-a0c4-6b20f11bddfb",
    "campaignId": "e69b367f-d6a5-42b6-a438-56d837ffd1de",
    "referralCode": "8yykmns3",
    "referralCodeBlocked": false,
    "isSelfReferral": false,
    "advocate": {
      "customerId": "9843534588704",
      "firstName": "Sam"
    }
  },
  "signature": "ZpQV4uZAPLl0hOdqsLpTen9AoWOcWqfGYI9VPFZbgR8="
}
```

Visitor Status allows friendbuy to pass details about a user visiting your website to a callback function. This data includes whether the visitor has clicked on a friendbuy referral link into the site, and if so, the source of the click, whether or not the click is a self-referral, and whether or not the referral code is blocked.

The `callback` parameter in the `getVisitorStatus` command is a function that will receive an object containing the
visitor status `payload` and a `signature` to verify the authenticity of the `payload`.

## Common Use Cases for Visitor Status:

Depositing a session-based credit into a referred user’s shopping cart.

Determining if a friend offer email capture widget should be shown.

Obtaining and storing the referral code for for future use, such as in a call to the POST /purchases API endpoint.

Advocate’s first name and customer ID are provided so you can personalize a message that the friend receives after clicking on a referral link.

## Verifying the Visitor Status Payload

You may wish to distribute rewards or do some other desirable action for the user based on their visitor status response.
To prevent fraud you can verify the `payload` validates against the `signature` provided in the response.

See <a href="#signature-validation">Signature Validation</a> for instructions on validating the signature.
